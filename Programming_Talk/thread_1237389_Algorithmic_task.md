---
title: "Algorithmic task"
date: 2009-08-11
forum: Programming Talk
---

### Post by cdiem on 2009-08-11
This is NOT a homework. I've been reading a 'beginner's programming' book. In the course of several days I've been trying to implement Depth-First-Search to solve an algorithmic issue I have found in this book. It's the first time I'm writing DFS algorithm, so I'm not even sure whether I have represented the matrix right... 

-- The issue is the following:
-- Find the biggest area of adjacent numbers in this matrix:
// 1 **3** 2 2 2 4
// **3 3 3** 2 4 4
// 4 **3** 1 2 **3 3** -> 13 times '3'
// 4 **3** 1 **3 3** 1
// 4 **3 3 3** 1 1

Here's the code I have so far, using the DFS implementation from [http://www.algolist.net/Algorithms/Graph_algorithms/Undirected/Depth-first_search](http://www.algolist.net/Algorithms/Graph_algorithms/Undirected/Depth-first_search). There are 'magic numbers' everywhere, and the methods are 'public static', also there is no memoization of the elements that DFS is already run on - I was intending to fix these things after the algorithm worked...

[PHP]public class AdjacentAreaInMatrix {

	/*
	 * Enums for the state of the Nodes, for use in DFS/BFS
	 */
	private enum NodeState {
		Visited, InProgress, Unvisited
	}; 

	/*
	 * These 2 'magic' numbers come from the hardcoded 'matrix' below,
	 * cause it has 5 rows and 6 columns
	 */
	public static final int ROWSCOUNT = 5;
	public static final int COLUMNSCOUNT = 6;

	/*
	 * Two variables for counting the maximum sequence 
	 * of numbers (as required by the problem definition)
	 */
	private static int tempElementsCount = 0;
	private static int maxElementsCount = 1; // except if the matrix is empty, then it should be 0
	
	/*
	 * The hardcoded matrix
	 */
	private static final int[][] matrix = new int[][] { 
			{ 1, 3, 2, 2, 2, 4 },
			{ 3, 3, 3, 2, 4, 4 }, 
			{ 4, 3, 1, 2, 3, 3 },
			{ 4, 3, 1, 3, 3, 1 }, 
			{ 4, 3, 3, 3, 1, 1 } };
	
	/* 
	 * Create an auxiliary matrix 'state' to implement DFS. 
	 * Initialize the whole matrix as 'unvisited' and
	 * start DFS at the first element of the matrix
	 */
	public static void DFS() {
		NodeState state[][] = new NodeState[ROWSCOUNT][COLUMNSCOUNT];
		// clear the state of the matrix
		for (int i = 0; i < ROWSCOUNT; i++) {
			for (int j = 0; j < COLUMNSCOUNT; j++) {
				state[i][j] = NodeState.Unvisited;
			}
		}
		runDFS(0, 0, state);	
	}

	/*
	 * Using the auxiliary matrix "state[][]", use DFS to traverse the
	 * 'real' matrix[][] 
	 */
	public static void runDFS(int i, int j, NodeState state[][]) {
		state[i][j] = NodeState.InProgress;
		// traverse the whole matrix state[][] and recursively run runDFS() from the needed elements. 
		for (int rows = 0; rows < ROWSCOUNT; rows++) {
			for (int columns = 0; columns < COLUMNSCOUNT; columns++) {
				/*
				 * ----------------------------------------------------------------------
				 * For the logic in the 'if' statement regarding the adjacent elements:
				 * i0j0 i1j0 i1j0
				 * i0j1 i1j1 i2j1
				 * i0j2 i1j2 i2j2
				 * It uses the thing, that the sum of (i+j) for the coordinates of
				 * the elements above, below, on the left and on the right of i1j1
				 * are exactly +1/-1 of the sum of the coordinates of i1j1
				 * -> i1j2 -> 1+2 = 3 
				 * -> i2j1 -> 1+2 = 3 
				 * -> i1j1 -> 1+1 = 2 (the current element) -> matrix[i][j] 
				 * -> i1j0 -> 1+0 = 1 
				 * -> i0j1 -> 1+0 = 1 
				 * ----------------------------------------------------------------------
				 */
				if ((matrix[i][j] == matrix[rows][columns]) // if the values are equal
						&& ((((i+j) - (rows + columns)) == 1) || (((i+j) - (rows + columns)) == -1))// and if the element is adjacent
						&& (state[rows][columns] == NodeState.Unvisited)) { // and if the element is still not visited
					tempElementsCount++;
					if (tempElementsCount > maxElementsCount) {
						maxElementsCount = tempElementsCount;
					}
					runDFS(rows, columns, state); // recursively run DFS for each element, that "isEdge"
				} else {
					// if the elements aren't [adjacent, equal and not visited], start the count again from '0'
					tempElementsCount = 0;  
				}
			}
		}
		state[i][j] = NodeState.Visited;
	}
	
	public static void go() {
		AdjacentAreaInMatrix.DFS();
		System.out.println(maxElementsCount);
	}
}
[/PHP]

After debugging it for several days, with every debugging session the code becomes more complicated...any help will be appreciated. Thanks in advance.

P.S.: I think a game that comes with Ubuntu, from the 'gnome-games' package, uses a similar algorithm - though I may be wrong.

EDIT1: There can be used ABS in this line:
"&& ((((i+j) - (rows + columns)) == 1) || (((i+j) - (rows + columns)) == -1))// and if the element is adjacent"
which will at least make the code a bit more readable.

EDIT: caught it; should not start every time from (0,0), and also shouldn't use tempCount... as '0' at the end of the DFS method.

---

