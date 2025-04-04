# AI-Chess
# Chess AI GUI Documentation

## Overview
This Python script creates a graphical chess game using Tkinter and integrates the Stockfish chess engine. It allows a human player to compete against the AI with different difficulty levels, provides move hints, and enables undoing moves.

## Dependencies
- `tkinter` for the graphical user interface
- `chess` (python-chess library) for handling chess logic
- `chess.engine` for communicating with the Stockfish chess engine

## Features
- Selectable difficulty levels: Easy (400), Medium (1000), Hard (1800)
- Player can choose to play as White or Black
- Graphical representation of the chessboard
- AI opponent using Stockfish engine
- Move highlighting and legal move indication
- AI blunder chance for lower difficulty levels
- Move hints provided by Stockfish
- Undo last move feature
- Game over detection (checkmate, stalemate, draws)

## Code Structure
### 1. **Initializing the Chess Engine**
```python
engine_path = "<path_to_stockfish>"
engine = chess.engine.SimpleEngine.popen_uci(engine_path)
```
The script initializes the Stockfish engine using the provided executable path.

### 2. **Class: `ChessGUI`**
Handles the entire GUI and game logic.

#### **Attributes:**
- `difficulty`: Stores selected AI difficulty level.
- `ai_thinking_time`: Defines AI move calculation time.
- `blunder_chance`: Probability of AI making a blunder.
- `player_color`: Stores player's selected color.
- `board`: Maintains the chess game state.
- `selected_square`: Stores currently selected square by player.
- `last_move`: Stores the most recent move.

#### **Methods:**

##### **`show_start_screen()`**
Displays the welcome screen where the player selects difficulty.

##### **`set_difficulty(rating)`**
Configures AI parameters based on selected difficulty level.

##### **`show_color_selection()`**
Allows the player to choose to play as White or Black.

##### **`start_game(color)`**
Initializes the chessboard and GUI elements.

##### **`create_widgets()`**
Creates the canvas for the board, status labels, and control buttons.

##### **`update_board()`**
Redraws the chessboard with the latest game state.

##### **`highlight_square(square, color, outline_only=False)`**
Highlights squares for selected moves or recent moves.

##### **`draw_piece(piece, x, y)`**
Draws chess pieces on the board.

##### **`on_click(event)`**
Handles player's move input and processes move logic.

##### **`ask_promotion()`**
Prompts user for pawn promotion choice.

##### **`ai_move()`**
Handles AI move generation using Stockfish.

##### **`get_hint()`**
Provides a suggested move using Stockfish.

##### **`undo_move()`**
Undoes the last two moves (one from AI and one from player).

### 3. **Main Execution**
```python
if __name__ == "__main__":
    root = tk.Tk()
    root.geometry("480x600")
    gui = ChessGUI(root)
    root.mainloop()
    engine.quit()
```
This section initializes the Tkinter GUI and starts the application loop.

## How to Run the Program
1. Install dependencies: `pip install python-chess`
2. Ensure Stockfish is downloaded and its path is correctly set in `engine_path`.
3. Run the script: `python chess_gui.py`

## Future Enhancements
- Add piece images instead of Unicode symbols.
- Implement time control for games.
- Support multiplayer mode.
- Improve AI difficulty scaling beyond skill levels.

This documentation provides an overview of how the Chess AI GUI works, covering its structure, functionalities, and usage.

