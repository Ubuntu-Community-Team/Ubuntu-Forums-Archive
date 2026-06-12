---
title: "Why the null pointer exception"
date: 2008-06-26
forum: Programming Talk
---

### Post by shadylookin on 2008-06-26
I'm trying to write a program solving the "N queens" problem. Essentially I'm trying to simulate a chestboard of N size and seeing how to place N queens without them being able to capture each other. 

However I'm receiving a null pointer exception at the bolded part and I can't figure out whats wrong. I'm guessing it has something to do with initializing the 2D board array but I can't see the problem. Any ideas?

```


public class Queens {

	
	
	private Square[][] board;
	private int numberOfSolutions;
	private int numberOfRowsAndColumns;
	
	public Queens(int numberOfQueens){		
		numberOfRowsAndColumns = numberOfQueens;		
		board = new Square[numberOfQueens][numberOfQueens];
	}// end constructor
	
	public void putQueens(int row){
		for(int col = 0; col < numberOfRowsAndColumns; col++){
			//if the spot on the board is available put a queen there
			**if(board[row][col].isAvailable == true)**{
				board[row][col].hasQueen = true;
				//use a for loop to set the row and column as unavailable
				for(int i = 0; i < board[row].length; i++){
					board[row][i].isAvailable = false;
					board[i][col].isAvailable = false;
				}// end nested for loop
				//loops to handle the diagonals
				
				for(int i = 1, column = col; 
				row + i < numberOfRowsAndColumns && column+i < numberOfRowsAndColumns; i++, column++){
					board[row+i][column+i].isAvailable = false;
				}
				
				for(int i = row+1, j = col -1; 
				i < numberOfRowsAndColumns && j >= 0; i++, j--){
					board[i][j].isAvailable = false;
				}
				
				for(int i = row -1, j = col -1;
				i >= 0 && j >= 0; i--, j--){
					board[i][j].isAvailable = false;
				}
				
				for(int i = row -1, j = col +1;
				i >= 0 && j < numberOfRowsAndColumns; i--, j++){
					board[i][j].isAvailable = false;
				}
				
				//end the diagonal loops
				
				if(row < numberOfRowsAndColumns -1){
					putQueens(row+1);
				}// end nested if statement
				
				else printBoard();
				
				
				for(int i = 0; i < board[row].length; i++){
					board[row][i].isAvailable = true;
					board[i][col].isAvailable = true;
				}// end nested for loop
				//loops to handle the diagonals
				
				for(int i = 1, column = col; 
				row + i < numberOfRowsAndColumns && column+i < numberOfRowsAndColumns; i++, column++){
					board[row+i][column+i].isAvailable = true;
				}
				
				for(int i = row+1, j = col -1; 
				i < numberOfRowsAndColumns && j >= 0; i++, j--){
					board[i][j].isAvailable = true;
				}
				
				for(int i = row -1, j = col -1;
				i >= 0 && j >= 0; i--, j--){
					board[i][j].isAvailable = true;
				}
				
				for(int i = row -1, j = col +1;
				i >= 0 && j < numberOfRowsAndColumns; i--, j++){
					board[i][j].isAvailable = true;
				}
				
				
			}// end if statement
			
		}// end for loop
	}// end putQueens()
	
	
	public void printBoard(){
		
		// if there are 10 or fewer queens to solve then print out the solutions
		// otherwise just add to the number of solutions
		if(numberOfRowsAndColumns < 11){		
			for(int row = 0; row < numberOfRowsAndColumns; row++){

				for(int column = 0; column < numberOfRowsAndColumns; column++){
					System.out.print(board[row][column]+ " ");
				}// end nested for loop

				System.out.println();

			}// end for loop

			// add one to the number of solutions
			numberOfSolutions++;
		}
	}// end printBoard
	
	public int getNumberOfSolutions(){
		return numberOfSolutions;
	}// end getNumberOfSolutions
	
	
	public static void main(String args[]){
		Queens q = new Queens(4);		
		q.putQueens(0);		
		System.out.println("number of solutions: "+q.getNumberOfSolutions());		
	}// end main	
	
}// end class


class Square{
	
	public boolean hasQueen = false;
	public boolean isAvailable = true;
	
	public String toString(){
		if (hasQueen = true)
			return String.format("Q");
		else
			return String.format("-");
	}// end toString
	
	
}// end class Square



```

---

### Post by geirha on 2008-06-26
You need to iterate board with new Square()s.

---

### Post by Zugzwang on 2008-06-26
Here's an idea: Use a debugger to find out what the problem is.

---

### Post by achelis on 2008-06-26
What geirha said :)

When you make an array it will be initialized with null values (unless it's an array of primitives in which case it will be initialized to the default value of the primitive).

---

