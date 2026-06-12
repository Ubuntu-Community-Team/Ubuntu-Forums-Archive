---
title: "Weekly Programming Challenge: Friday, Jan 5, 2006"
date: 2007-01-06
forum: Programming Talk
---

### Post by ghostdog74 on 2007-01-06
Seeing that the challenge has not been decided till now, i think i will post one taken from somewhere but simplified. If anyone has any better one or if its too difficult, let me know and i will re-edit/delete this post. Here goes

The problem:

We have a 4 x 4 square grids 1 through 16, from left to right, top to bottom.

Eg. 4x4 grid:
```

1    2    X  4
5    6    7  8 
9    10  11 X 
13  14  X  16

```

3 of these squares (3,12 and 15) contain obstacles, ( X above )

Find the longest(maximum) path one can go before he gets stuck with the following criteria

- Always start walking on grid 1, going either down or right.
- Can move in 4 directions: up, down, left, right.
- He cannot travel through the obstacle (X) or a previous grid 
- He moves [COLOR="Red"]straight[/COLOR] until he reaches a square he can not travel through or the edge.
-When he cannot move straight, he turns either left or right.
-When he cannot move left, right, or straight, he stops.


For a start, we just solve for obstacles at 3,12,15. The maximum path I could find is
1->2->6->5->9->13->14->10->11->7->8->4  so the final answer is 12 grids (?I may be wrong.?).
The challenge is to find an algorithm to calculate this path.
Its good to print the path taken too..
You can also solve for straight line only, as some of you have pointed out its more simple.

eg.
For situation of "totally no obstacles" using straight line (simpler) rule, i can find only 2 solutions (correct me if i am wrong):
a) 1->2->3->4->8->12->16->15->14->13->9->5->6->7->11->10
b) 1->5->9->13->14-15->16->12->8>4->3->2->6->10->11->7

So for the above obstacle example at 3,12, 15 , using straight line  rule, the solution seeem to be
1->5->9->13->14->10->6->2 (correct me if i miss something)

any diagonals not allowed
1->6->11->16->x->x->x ......<---not allowed

---

### Post by gpolo on 2007-01-06
I believe you are wrong, based on this rule: 
 - He moves in a straight line until he reaches a square he can not travel through or the edge.

If he moves in a straight line until he reaches a square he can not travel through or the edge, the path should be: 1->2->6->10->14->13->9->5 end

---

### Post by amiga_os on 2007-01-06
Which ironically makes the challenge a whole lot easier! (imo), as it's easier to make the character walk in a straight direction, and then make good choices when forced to, rather than find the optimal route to take when I can turn on any square.

Without the straight line rule, the algorithm has to process all of the available data at once, rather than iterating through one step at a time.

---

### Post by Verminox on 2007-01-06
It's a real cool problem, and gpolo is right on the given example, but I guess one will have to sit and think hard on it to get even near close to an algorithm.

I don't mind giving it a try, but as these challenges were started by someone as a way to get non-programmers or newbies more involved in managing general tasks.... IMO this is a bit overkill. None the less we will keep this going till the end of the week for now.

---

### Post by gpolo on 2007-01-06
it is easier and you get just one solution, in his example there could be more than one solution

---

### Post by jayemef on 2007-01-06
Yeah, can we clarify whether the figure MUST continue forward when possible?

---

### Post by slavik on 2007-01-06
so, is it finding the path to travel most squares or do you just travel in straight line as if on ice and then turn when you hit an obstacle (kind of how the atomic game works  where you put molecules together).

either way, this is a tree traversion problem

---

### Post by Mirrorball on 2007-01-06
Assuming you have to travel in a straight line until you hit an obstacle:
```

def turn_right(direction):
    if direction == 'up':
        return 'right'
    elif direction == 'down':
        return 'left'
    elif direction == 'left':
        return 'up'
    else:
        return 'down'

def turn_left(direction):
    if direction == 'up':
        return 'left'
    elif direction == 'down':
        return 'right'
    elif direction == 'left':
        return 'down'
    else:
        return 'up'

def traverse(grid, row, col, direction):
    path = []
    nextrow = row
    nextcol = col
    while 1:
        if direction == 'up':
            nextrow -= 1
        elif direction == 'down':
            nextrow += 1
        elif direction == 'left':
            nextcol -= 1
        else:
            nextcol += 1
        if nextcol < 4 and nextcol >= 0 and nextrow < 4 and nextrow >= 0 and grid[nextrow][nextcol] != -1:
            col = nextcol
            row = nextrow
            path.append((row, col))
            grid[row][col] = -1
        else:
            break
    if len(path) == 0:
        return path
    path1 = traverse(grid, row, col, turn_right(direction))
    path2 = traverse(grid, row, col, turn_left(direction))
    # Erase path in grid 
    for row, col in path:
        grid[row][col] = row * 4 + col + 1
    if len(path1) >= len(path2):
        return path + path1
    else:
        return path + path2

def solve(grid):
    path1 = traverse(grid, 0, -1, 'right')
    path2 = traverse(grid, -1, 0, 'down')
    if len(path1) >= len(path2):
        path = path1
    else:
        path = path2
    print "Grid"
    for i in grid:
        print " ".join(["%2d" % j for j in i]).replace("-1", " X")
    print "Longest path length:", len(path)
    print '->'.join(["%d" % (row * 4 + col + 1) for row, col in path])
    print

grid = [[1, 2, -1, 4], [5, 6, 7, 8], [9, 10, 11, -1], [13, 14, -1, 16]]
solve(grid)

```Output:
```

Grid
 1  2  X  4
 5  6  7  8
 9 10 11  X
13 14  X 16
Longest path length: 8
1->2->6->10->14->13->9->5

```

---

### Post by dwblas on 2007-01-06
Well, whatever you want since some looseness is necessary to be able to explore different ways to approach these problems.  I would vote that we start with the straight line rule for those who don't understand everything yet, and then post another solution with another set of rules if you want to.  'Not necessarily in a straight line' and 'starting from any square' would be two variations.  We may be getting into a brute force situation again here, not that that's bad, just an observation.  How would you solve this using any set of rules, other than trying all possibilities?  Perhaps Third Thoughts has some math on this one like he did on the palindrome.  I am wanting to test his observation on that, but there is no time to do it right now.

---

### Post by jayemef on 2007-01-06
Well just thinking out loud, I see the solution to this problem utilizing a decision tree. A tree for the given example would look like the following:
[php]
Tree:
    1
  __|__
 |     |
 2     5
 |     |
 6     9
 |     |
 10   13
 |     |
 14   14
 |     |
 13   10
 |     |
 9     6
 |     |
 5     2
[/php]
Basically, any time a decision would need to be made, an additional node would be inserted at the given level. This is demonstrated at the root, where the figure can either head east (2) or south (5). Once all paths are completed in this manner, the segment of the tree with the greatest height would be your answer. As can be seen by this tree, the (only) two possible paths are of equal height (and are also reverse paths of one another when not including the origin). In such a case, I would probably just return the first.

If we stick to the rule that the traveler must always go forward when possible, then this tree can be implemented as a binary tree (binary as in 2 children, not as in left child < right child), as there will always be 2 or less decisions: either go forward (only 1 decision), or travel either left, right, or both (1 or 2 decisions).

---

### Post by Mirrorball on 2007-01-06
My solution was buggy, now I think I fixed it.

---

### Post by Wybiral on 2007-01-06
This was a fun challenge. I've actually encountered a similar challenge before when writing a paint program way back in the qbasic days... This is very similar to a floodfill algorithm (one of them anyway). Anyway, my solution is in C++, it may not be the prettiest, but it uses a recursive function to check each movable space, while flagging previous spaces as obstacles. When it can't move anywhere else, it compares that path to the current longest path, if the new one is longer, it becomes the longest...

The obstacles aren't hardcoded, you have to enter them when the program starts as (X,Y) locations on the grid.

Compile it with "g++ longestPath.cpp -o longestPath"

```

#include <iostream>
#include <vector>

// Grid dimensions
#define width 4
#define height 4

// Directional constants
#define U 1
#define D 2
#define L 3
#define R 4

using namespace std;

// Grid class
class grid {
	public:
		bool cell[width][height];
		grid(){}
		void clear(){
			for(int y=0; y<height; y++){
				for(int x=0; x<width; x++){
					cell[x][y] = true;
				}
			}
		}
};

// Path class
class path {
	public:
		vector<char> vPath;
		path(){}
		void add(char dir){vPath.push_back(dir);}
		int length(){return vPath.size();}
		char at(int i){ return vPath.at(i); }
} ;

// Global longest path
path longestPath;

// Print grid
void printGrid(grid thisGrid){
	for(int y=0; y<height; y++){
		for(int x=0; x<width; x++){
			cout << thisGrid.cell[x][y] << " ";
		} cout << endl;
	}
}

// Print path
void printPath(path thisPath){
	cout << "Path length: " << thisPath.length() << endl;
	for(int i=0; i<thisPath.length(); i++){
		switch(thisPath.at(i)){
			case U: cout << "Up "; break;
			case D: cout << "Down "; break;
			case L: cout << "Left "; break;
			case R: cout << "Right "; break;
		}
	} cout << endl;
}

// Recursively seek longest path(s)
void solve(grid thisGrid, int x, int y, path thisPath, char dir){
	bool found = false;
	thisGrid.cell[x][y] = false;
	if(dir){thisPath.add(dir);}
	if(thisGrid.cell[x+1][y  ] && (x+1)<width ){found=true; solve(thisGrid, x+1, y  , thisPath, R);}
	if(thisGrid.cell[x-1][y  ] && (x-1)>=0    ){found=true; solve(thisGrid, x-1, y  , thisPath, L);}
	if(thisGrid.cell[x  ][y+1] && (y+1)<height){found=true; solve(thisGrid, x  , y+1, thisPath, D);}
	if(thisGrid.cell[x  ][y-1] && (y-1)>=0    ){found=true; solve(thisGrid, x  , y-1, thisPath, U);}
	// If no direction is possible, stop and check path to longest path
	if(!found){
		if(thisPath.length()>longestPath.length()){longestPath = thisPath;}
		return;
	}
}

int main(){
	int x=1, y=1;

	// Initialize grid
	grid myGrid;

	// Clear grid
	myGrid.clear();

	// Print empty grid
	printGrid(myGrid);

	// Ask for obstacle locations
	cout << "Enter (X,Y) of obstacle or 0 to solve!" << endl;
	while(x && y){
		cout << "X: "; cin >> x;
		if(x){
			cout << "Y: "; cin >> y;
			if(x>0 && y>0 && x<=width && y<=height){
				myGrid.cell[x-1][y-1] = false;
			}
		}
	}

	// Print new grid
	printGrid(myGrid);

	// Call solve function... (grid, int startX, int startY, path startPath, char startDirection)
	solve(myGrid, 0, 0, longestPath, 0);

	// Print longest path found
	printPath(longestPath);
}

```

---

### Post by Mirrorball on 2007-01-06
> **Wybiral said:**
> This was a fun challenge. I've actually encountered a similar challenge before when writing a paint program way back in the qbasic days...
I think you can only turn right or left, and only when you can't go forward anymore.

---

### Post by Wybiral on 2007-01-06
Oh, My bad... I just now read those post's, I'll have to make some adjustments and repost it. Thanks!

---

### Post by Mirrorball on 2007-01-06
I'm going to post a few grids and results, and we can compare if our programs produce the same output. I don't guarantee they are correct.
```

Grid
 1  2  X  4
 5  6  7  8
 9 10 11  X
13 14  X 16
Longest path length: 8
1->2->6->10->14->13->9->5

Grid
 1  2  3  4
 5  6  7  8
 9 10 11 12
13 14 15 16
Longest path length: 16
1->2->3->4->8->12->16->15->14->13->9->5->6->7->11->10

Grid
 1  X  X  4
 5  6  X  8
 9  X 11 12
13  X  X 16
Longest path length: 4
1->5->9->13

Grid
 1  X  3  4
 5  X  7  8
 9 10  X 12
13 14 15 16
Longest path length: 12
1->5->9->13->14->15->16->12->8->4->3->7

Grid
 1  2  3  4
 5  6  7  8
 9  X  X 12
13  X  X 16
Longest path length: 7
1->2->3->4->8->12->16

```

---

### Post by ghostdog74 on 2007-01-06
> **gpolo said:**
> I believe you are wrong, based on this rule: 
 - He moves in a straight line until he reaches a square he can not travel through or the edge.

If he moves in a straight line until he reaches a square he can not travel through or the edge, the path should be: 1->2->6->10->14->13->9->5 end

hi
sorry for the confusion, i have edited the rule. He can only move straight, (ie, not diagonal)... and not "a straight line", so the 12 grids answer is still "correct". But as dwblas mentioned, for those who don't quite get the problem or who think its overkill, they can program for just the straight line (in your case) rule.

---

### Post by Wybiral on 2007-01-06
Ok, updated for the straight line rule, some algorithm as before, just some adjustments, it also displays the path taken in steps...

```

#include <iostream>
#include <iomanip>
#include <vector>

// Grid dimensions
#define width 4
#define height 4

// Directional constants
#define R 1
#define L 2
#define D 3
#define U 4

using namespace std;

// Grid class
class grid {
	public:
		char cell[width][height];
		grid(){}
		void clear(){
			for(int y=0; y<height; y++){
				for(int x=0; x<width; x++){
					cell[x][y] = 0;
				}
			}
		}
};

// Path class
class path {
	public:
		vector<char> vPath;
		path(){}
		void add(char dir){vPath.push_back(dir);}
		int length(){return vPath.size();}
		char at(int i){ return vPath.at(i); }
} ;

// Global longest path and map of path
grid longestMap;
path longestPath;

// Print grid
void printGrid(grid thisGrid){
	cout.fill('0');
	for(int y=0; y<height; y++){
		for(int x=0; x<width; x++){
			cout << setw(2) << (int)thisGrid.cell[x][y] << " ";
		} cout << endl;
	}
}

// Print path
void printPath(path thisPath){
	cout << "Path length: " << thisPath.length() << endl;
	for(int i=0; i<thisPath.length(); i++){
		switch(thisPath.at(i)){
			case U: cout << "Up "; break;
			case D: cout << "Down "; break;
			case L: cout << "Left "; break;
			case R: cout << "Right "; break;
		}
	} cout << endl;
}

// Check if cell is valid or not...
bool checkCell(grid thisGrid, int x, int y){
	if(x>=0 && x<width && y>=0 && y<height){
		return not(thisGrid.cell[x][y]);
	} else {
		return false;
	}
}

// Recursively seek longest path(s)
void solve(grid thisGrid, int x, int y, path thisPath, char dir){
	bool found = false;
	if(dir){thisPath.add(dir);}
	thisGrid.cell[x][y] = thisPath.length()+1;
	// Check to see if we can still move in this direction
	switch(dir){
		case R: if(checkCell(thisGrid, x+1, y  )){found=true; solve(thisGrid, x+1, y  , thisPath, R);} break;
		case L: if(checkCell(thisGrid, x-1, y  )){found=true; solve(thisGrid, x-1, y  , thisPath, L);} break;
		case D: if(checkCell(thisGrid, x  , y+1)){found=true; solve(thisGrid, x  , y+1, thisPath, D);} break;
		case U: if(checkCell(thisGrid, x  , y-1)){found=true; solve(thisGrid, x  , y-1, thisPath, U);} break;
	}

	// If we couldn't keep moving, see if we can turn...
	if(!found){
		if(checkCell(thisGrid, x+1, y  )){found=true; solve(thisGrid, x+1, y  , thisPath, R);}
		if(checkCell(thisGrid, x-1, y  )){found=true; solve(thisGrid, x-1, y  , thisPath, L);}
		if(checkCell(thisGrid, x  , y+1)){found=true; solve(thisGrid, x  , y+1, thisPath, D);}
		if(checkCell(thisGrid, x  , y-1)){found=true; solve(thisGrid, x  , y-1, thisPath, U);}
	}

	// If no direction is possible, stop and check path to longest path
	if(!found){
		if(thisPath.length()>longestPath.length()){
			longestMap = thisGrid;
			longestPath = thisPath;
		}
		return;
	}
}

int main(){
	int x=1, y=1;

	// Initialize grid
	grid myGrid;

	// Clear grid
	myGrid.clear();

	// Print empty grid
	printGrid(myGrid);

	// Ask for obstacle locations
	cout << "Enter (X,Y) of obstacle or 0 to solve!" << endl;
	while(x && y){
		cout << "X: "; cin >> x;
		if(x){
			cout << "Y: "; cin >> y;
			if(x>0 && y>0 && x<=width && y<=height){
				myGrid.cell[x-1][y-1] = -1;
			}
		}
	}

	// Call solve function... (grid, int startX, int startY, path startPath, char startDirection)
	solve(myGrid, 0, 0, longestPath, 0);

	// Print new grid
	printGrid(longestMap);

	// Print longest path found
	printPath(longestPath);
}

```

"-1"s are obstacles, you enter the x,y of the obstacles when the program starts...

```

01 02 -1 00 
08 03 00 00 
07 04 00 -1 
06 05 -1 00 
Path length: 7
Right Down Down Down Left Up Up 

```

```

01 -1 -1 00 
02 00 00 00 
03 -1 00 00 
04 -1 -1 00 
Path length: 3
Down Down Down 

```

No obstacles...
```

01 02 03 04 
12 13 14 05 
11 16 15 06 
10 09 08 07 
Path length: 15
Right Right Right Down Down Down Left Left Left Up Up Right Right Down Left 

```

---

### Post by Mirrorball on 2007-01-06
You should add 1 to your path lengths. My program found the same paths than yours. :D

---

### Post by Wybiral on 2007-01-06
Yeah, the path length of mine is calculated in steps from the 0,0 locations... If anyone wants it like that, just put an +1 in the printPath function. It's basically the same, we just mean too different things... Mine is the number of moves, and yours is the length of the entire path.

---

### Post by RoyArne on 2007-01-06
Common Lisp version:

```

(defmacro **defgrid** (&body rows)
  `(quote (,@rows)))

(defun **xpos** (point) 
  "*Return the X coordinate of a point.*"
  (first point))

(defun **ypos** (point) 
  "*Return the Y coordinate of a point.*"
  (second point))

(defun **row** (ypos grid) 
   "*Return row number ypos from the grid.*"
  (nth ypos grid))

(defun **column** (xpos row)
  "*Return column number xpos from the row.*"
  (nth xpos row))

(defun **look-at** (point grid)
  "*Return the contents of a point in the grid.*"
  (column (xpos point)
	  (row (ypos point) grid)))

(defun **visitedp** (point path)
  "*True if this point has been visited previously.*"
  (member point path :test #'equal))

(defun **outside-grid-p** (point grid)
  "*True if the point is outside the grid.*"
  (or (< (ypos point) 0)
      (>= (ypos point) (length grid))
      (>= (xpos point) (length (row (ypos point) grid)))
      (< (xpos point) 0)))

(defun **blockedp** (point grid path)
  "*True if it's impossible to move to this point.*"
  (or (outside-grid-p point grid)
      (visitedp point path)
      (or (eql 'x (look-at point grid))
	  (null (look-at point grid)))))

[I];; south, east, north and west are the
;; "heading" functions passed around below.[/I]
(defun **south** (point)
  "*Return a point to the south of this point.*"
  (list (xpos point) (1+ (ypos point))))

(defun **east** (point)
  "*Return a point to the east of this point.*"
  (list (1+ (xpos point)) (ypos point)))

(defun **north** (point)
  "*Return a point to the north of this point.*"
  (list (xpos point) (1- (ypos point))))

(defun **west** (point)
  "*Return a point to the west of this point.*"
  (list (1- (xpos point)) (ypos point)))

(defun **straight** (point grid path heading)
  "*If possible, walk to the point calculated by the heading function.*"
  (unless (blockedp (funcall heading point) grid path)
    (walk (funcall heading point) grid (append path (list point)) heading)))

(defun **left** (heading)
  "[I]Returns a function that will calculate a point to the left of the
given heading[/I]."
  (cond ((eql heading #'north)  #'west)
	((eql heading #'west) #'south)
	((eql heading #'south) #'east)
	((eql heading #'east) #'north)))

(defun **right** (heading)
  "[I]Returns a function that will calculate a point to the right of the
given heading.[/I]"
  (cond ((eql heading #'north) #'east)
	((eql heading #'west) #'north)
	((eql heading #'south) #'west)
	((eql heading #'east) #'south)))

(defun **longest** (&rest paths)
  "*Return the longest of an arbitrary number of paths.*"
  (loop with longest-path = nil
	for path in paths
	do (when (> (length path) (length longest-path))
	     (setf longest-path path))
	finally (return longest-path)))
  
(defun **walk** (point grid path heading)
  "*Walk from point towards the given heading.*"
  (or (straight point grid path heading)
      (longest (straight point grid path (left heading))
	       (straight point grid path (right heading)))
      (append path (list point))))

(defun **start-walking** (from grid)
  (unless (blockedp from grid nil)
    (let ((path (loop for point in (longest (walk from grid nil #'south)
					    (walk from grid nil #'east)
					    (walk from grid nil #'north)
					    (walk from grid nil #'west))
		      collect (look-at point grid))))
      (values path (length path)))))

```

And the results:

```

CL-USER> (start-walking '(0 0) (defgrid ( 1  2  X  4)
					( 5  6  7  8)
					( 9 10 11  X)
					(13 14  X 16)))
(1 5 9 13 14 10 6 2)
8
CL-USER> (start-walking '(0 0) (defgrid ( 1  2  3  4)
					( 5  6  7  8)
					( 9 10 11 12)
					(13 14 15 16)))
(1 5 9 13 14 15 16 12 8 4 3 2 6 10 11 7)
16
CL-USER> (start-walking '(0 0) (defgrid ( 1  X  X  4)
					( 5  6  X  8)
					( 9  X 11 12)
					(13  X  X 16)))
(1 5 9 13)
4
CL-USER> (start-walking '(0 0) (defgrid ( 1  X  3  4)
					( 5  X  7  8)
					( 9 10  X 12)
					(13 14 15 16)))
(1 5 9 13 14 15 16 12 8 4 3 7)
12
CL-USER>  (start-walking '(0 0) (defgrid ( 1  2  3  4)
					 ( 5  6  7  8)
					 ( 9  X  X 12)
					 (13  X  X 16)))
(1 2 3 4 8 12 16)
7
CL-USER> (start-walking '(3 2) (defgrid ( 1  2  x  4)
					( x  6  7  8  9)
					(10 11 12 13 14)
					(15  x 16 17 18 19 20 21  x 23)
					( x 25 26  x 27 28 29 30 31 32)
					(33 34 35 36  x 38)
					(39 40 41  x 42)
					(43 44 45)))
(13 14 9 8 7 6 11 12 16 26 35 41 45 44 43 39 33 34 25)
19
CL-USER> 

```

---

### Post by jayemef on 2007-01-06
You can feel pretty confident with your solution if it gets the correct result when solving the following two grids (the reason for 2 is to verify that no single direction is favored):
[php]
Grids:
 1  2  3  X
 X  6  7  8
 X 10 11  X
 X 14 15 16

---------- Capture Output ----------
Right answer:
1 -> 2 -> 3 -> 7 -> 11 -> 15 -> 14 -> 10 -> 6


and

 1  2  3  X
 X  6  7  8
 X  X 11 12
 X 14 15 16

---------- Capture Output ----------
Right answer:
1 -> 2 -> 3 -> 7 -> 11 -> 15 -> 16 -> 12 -> 8
[/php]

I'm close to a solution in ruby. Just need to make sure it always returns the longest.

---

### Post by Mirrorball on 2007-01-06
Both checked!

---

### Post by jayemef on 2007-01-07
Alright, here's my solution in ruby. I'm still not that happy with it, so I'll probably rework some things, but it works.

[php]
class GridGame

    def initialize(obstacles)
        @grid = Array.new(16) {|i| i+1}
        obstacles.each {|x| _mark(x, 'X')}
    end
    
    
    def solve
        path1 = _traverse([1], "E")
        path2 = _traverse([1], "S")
        
        return (path1.length >= path2.length) ? path1 : path2
    end
    
    
    def to_s
        s = ''
        4.times do |row|
            i = row * 4
            s += sprintf("%2s %2s %2s %2s\n",
                         @grid[i], @grid[i+1], @grid[i+2], @grid[i+3] );
        end
        
        return s
    end
    
    
    private
    
    def _traverse(path, facing)
        index = path.last

        if _valid_move?(index)
            _mark(index, '#')
        else
            path.pop
            return path
        end
        
        if _reached_end?(index)
            return path
        end
        
        
        if _forward?(index, facing)
            path.push(_forward(index, facing))
            return _traverse(path, facing)
        else
            pathl = Array.new(path)
            pathl.push(_forward(index, _rotate_left(facing)))
            
            pathr = Array.new(path)
            pathr.push(_forward(index, _rotate_right(facing)))
            
            pathl = _traverse(pathl, _rotate_left(facing))
            pathr = _traverse(pathr, _rotate_right(facing))            
            
            return (pathl.length >= pathr.length) ? pathl : pathr
        end
    end
    
    
    def _reached_end?(index)
        num_rotations = 0
        facing = "N"
        
        while !_forward?(index, facing) and num_rotations < 4
            facing = _rotate_left(facing)
            num_rotations += 1
        end
        
        return num_rotations == 4
    end
    
    
    def _forward?(index, facing)
        next_index = _forward(index, facing)
        
        if _valid_move?(next_index)
            case facing
            when "N", "S" then return true
            when "E" then return ((index     % 4) != 0)
            when "W" then return (((index-1) % 4) != 0)
            end
        end
        
        return false
    end
    
    
    def _forward(index, facing)
        case facing
        when "N" then return index - 4
        when "E" then return index + 1
        when "S" then return index + 4
        when "W" then return index - 1
        end
    end
    
    
    def _valid_index?(index)
        return ((1 <= index) && (index <= @grid.length))
    end
    
    
    def _valid_move?(index)
        return _valid_index?(index)    \
            && (@grid[index-1] != "X") \
            && (@grid[index-1] != "#")
    end
    
    
    def _rotate_left(facing)
        case facing
        when "N" then return "W"
        when "E" then return "N"
        when "S" then return "E"
        when "W" then return "S"
        end
    end
    
    
    def _rotate_right(facing)
        return _rotate_left(_rotate_left(_rotate_left(facing)))
    end
    
    
    def _mark(index, c)
        @grid[index - 1] = c
    end
    
end


if __FILE__ == $0
    puzzles = [
        [5, 9, 13, 4, 10],
        [5, 9, 13, 4, 12],
        [3, 12, 15],
        [],
        [2, 3, 7, 10, 14, 15],
        [2, 6, 11],
        [10, 11, 14, 15]
    ]
    
    puzzles.each do |puzzle|
        grid = GridGame.new(puzzle)
        puts grid.to_s
        path = grid.solve
        puts path.join(" -> ")
        puts
    end
end
[/php]

Output:
[php]
---------- Capture Output ----------
 1  2  3  X
 X  6  7  8
 X  X 11 12
 X 14 15 16
1 -> 2 -> 3 -> 7 -> 11 -> 15 -> 16 -> 12 -> 8

 1  2  3  X
 X  6  7  8
 X 10 11  X
 X 14 15 16
1 -> 2 -> 3 -> 7 -> 11 -> 15 -> 14 -> 10 -> 6

 1  2  X  4
 5  6  7  8
 9 10 11  X
13 14  X 16
1 -> 2 -> 6 -> 10 -> 14 -> 13 -> 9 -> 5

 1  2  3  4
 5  6  7  8
 9 10 11 12
13 14 15 16
1 -> 2 -> 3 -> 4 -> 8 -> 12 -> 16 -> 15 -> 14 -> 13 -> 9 -> 5 -> 6 -> 7 -> 11 -> 10

 1  X  X  4
 5  6  X  8
 9  X 11 12
13  X  X 16
1 -> 5 -> 9 -> 13

 1  X  3  4
 5  X  7  8
 9 10  X 12
13 14 15 16
1 -> 5 -> 9 -> 13 -> 14 -> 15 -> 16 -> 12 -> 8 -> 4 -> 3 -> 7

 1  2  3  4
 5  6  7  8
 9  X  X 12
13  X  X 16
1 -> 2 -> 3 -> 4 -> 8 -> 12 -> 16
[/php]

---

### Post by 56phil on 2007-01-07
I'm late. ](*,)  Here's my solution:

```

#! /usr/bin/python
""" problem module """


import string
import copy



def turn_right(course):
    """ add 90 to course 
    
    return number """
    course += 90
    while course >= 360:
        course -= 360
    return course


def mark_pos(p):
    """ mark position and bump move counter 
    
    return list """
    p[4][p[2]][p[3]] = string.lowercase[p[1]]
    p[1] += 1
    return p


def print_grid(array):
    """ prints solution """
    print '\n'
    for row in array:
        print ' %2s' * 4 % tuple(row)
    print '\n'


def advance(p):
    """ moves one space in the direction stored in p[0] 
    
    return list """
    course = p[0]
    if course == 0:
        p[2] -= 1
    elif course == 90:
        p[3] += 1
    elif course == 180:
        p[2] += 1
    else:
        p[3] -= 1
    return p


def next_position_safe(p):
    """ check to see if next move is safe
    
    return boolean """
    rc = False
    course = p[0]
    i = p[2]
    j = p[3]
    array = p[4]
    if course == 0 and i > 0:
        rc = array[i - 1][j].isdigit()
    elif course == 90 and j < 3:
        rc = array[i][j + 1].isdigit()
    elif course == 180 and i < 3:
        rc = array[i + 1][j].isdigit()
    elif course == 270 and j > 0:
        rc = array[i][j - 1].isdigit()
    return rc


def go(p):
    """ makes safe moves """
    global sol_state
    while next_position_safe(p):
        p = advance(p)
        p = mark_pos(p)
    n = 0
    while not next_position_safe(p):
        p[0] = turn_right(p[0])
        n += 1
        if n > 3:
            break
    if n <= 3:
        go(p)
    elif sol_state[1] < p[1]:       # do we have a new winner?
        sol_state = copy.deepcopy(p)
    

if __name__ == '__main__':
    # course = 0, moves = 0, row = 0, column = 0, new grid
    state = [0, 0, 0, 0, 
        [['1', '2', 'X', '4'], 
         ['5', '6', '7', '8'], 
         ['9', '10', '11', 'X'], 
         ['13', '13', 'X', '16']]]
    sol_state = copy.deepcopy(state)
    state = mark_pos(state)
    go(state)
    print_grid(sol_state[4])

```
output:
```

  a  b  X  4
  h  c  7  8
  g  d 11  X
  f  e  X 16

```
I'm just learning python. So it may be a little rough.

---

### Post by jblebrun on 2007-01-07
Here's my python solution. I've included a few tests. Here are the results:

Format is:
Max path found : (obstacle set) - last longest path recorded

12 : ([3, 12, 15]) - [1, 2, 6, 5, 9, 13, 14, 10, 11, 7, 8, 4]
16 : ([]) - [1, 5, 9, 13, 14, 10, 6, 2, 3, 7, 11, 15, 16, 12, 8, 4]
4 : ([2, 3, 7, 10, 14, 15]) - [1, 5, 9, 13]
12 : ([2, 6, 11]) - [1, 5, 9, 13, 14, 15, 16, 12, 8, 4, 3, 7]
9 : ([4, 5, 9, 12, 13]) - [1, 2, 6, 10, 14, 15, 11, 7, 3]
9 : ([4, 5, 9, 10, 13]) - [1, 2, 6, 7, 11, 15, 16, 12, 8]

```

#The grid class works with a 2D grid in (x,y) 0-based coordinates
#Information can be passed in and out using cell-numbered formats.
class Grid:

    def __init__(self,x,y,obstacles):

	self.xsize,self.ysize=x,y
	self.x,self.y=0,0
	self.longest_path=[(0,0)]
	self.current_path=[(0,0)]
	self.obstacles=[]

	#Convert numbered obstacles to coordinates	
	for o in obstacles:
	    self.obstacles.append(self.num_to_coord(o))

    #A valid move must be in the grid (0-size-1) and not an obstacle, and not 
    #already visisted.    
    def valid_move(self, x, y):
	return (x >= 0 and x < self.xsize 
		and y >= 0 and y < self.ysize 
		and (x,y) not in self.obstacles 
		and (x,y) not in self.current_path)

    #Core of the problem solution
    #This recursive function simply tries all NSEW paths recursively. 
    def travel(self):
	for choice in ( (self.x, self.y+1),
			(self.x,self.y-1),
			(self.x+1,self.y),
			(self.x-1,self.y)):

	    #For each of the valid NSEW choices, add it to the current path
	    #and check from there. If you end up with a longer path, update
	    #the longest path.
	    if self.valid_move(*choice):
		self.current_path.append(choice)
		self.x,self.y=choice
		
		if len(self.current_path) > len(self.longest_path):
		    self.longest_path = self.current_path[:]
		self.travel()
		self.current_path.remove(choice)
	
    #Convert (x,y) format to cell-numbered format (i,e, (0,0)->1, (0,1)->2, etc)
    def coord_to_num(self,x,y):
	return y*self.xsize+x+1

    #Convert cell-numbered to (x,y) format
    def num_to_coord(self, num):
	return ((num-1) % self.ysize), ((num-1) / self.xsize) 

    def get_result(self):
	return [self.coord_to_num(x,y) for x,y in self.longest_path]

if __name__=="__main__":

    testset=[[3,12,15],[],[2,3,7,10,14,15],[2,6,11],[4,5,9,12,13],[4,5,9,10,13]]

    for obs in testset:
	grid=Grid(4,4,obs)
	grid.travel()    
	result=grid.get_result()
	
	print len(result),":",result



```

---

### Post by Mirrorball on 2007-01-08
> **jblebrun said:**
> 16 : ([]) - [1, 5, 9, 13, 14, 10, 6, 2, 3, 7, 11, 15, 16, 12, 8, 4]
You have to move forward if you can. If you get to 13 and 14, then you have to go to 15 and 16 too. At least according to rules.

---

### Post by jblebrun on 2007-01-08
> **Mirrorball said:**
> You have to move forward if you can. If you get to 13 and 14, then you have to go to 15 and 16 too. At least according to rules.

No, that's not correct. According to ghostdog's reply #16:
> 
hi
sorry for the confusion, i have edited the rule. He can only move straight, (ie, not diagonal)... and not "a straight line", so the 12 grids answer is still "correct". But as dwblas mentioned, for those who don't quite get the problem or who think its overkill, they can program for just the straight line (in your case) rule.


He also updated the rules to state this. In any case, I modified my solution to easily use either rule. If you create a new Grid with icey=True, then it uses the maximal straight line rule. 
EDIT: Ok, it seems he hasn't updated the rules in the parent post, yet. 


Test results:
```

12 : ([3, 12, 15]) - [1, 2, 6, 5, 9, 13, 14, 10, 11, 7, 8, 4]
icey: 8 : ([3, 12, 15]) - [1, 5, 9, 13, 14, 10, 6, 2]
16 : ([]) - [1, 5, 9, 13, 14, 10, 6, 2, 3, 7, 11, 15, 16, 12, 8, 4]
icey: 16 : ([]) - [1, 5, 9, 13, 14, 15, 16, 12, 8, 4, 3, 2, 6, 10, 11, 7]
4 : ([2, 3, 7, 10, 14, 15]) - [1, 5, 9, 13]
icey: 4 : ([2, 3, 7, 10, 14, 15]) - [1, 5, 9, 13]
12 : ([2, 6, 11]) - [1, 5, 9, 13, 14, 15, 16, 12, 8, 4, 3, 7]
icey: 12 : ([2, 6, 11]) - [1, 5, 9, 13, 14, 15, 16, 12, 8, 4, 3, 7]
9 : ([4, 5, 9, 12, 13]) - [1, 2, 6, 10, 14, 15, 11, 7, 3]
icey: 9 : ([4, 5, 9, 12, 13]) - [1, 2, 3, 7, 11, 15, 14, 10, 6]
9 : ([4, 5, 9, 10, 13]) - [1, 2, 6, 7, 11, 15, 16, 12, 8]
icey: 9 : ([4, 5, 9, 10, 13]) - [1, 2, 3, 7, 11, 15, 16, 12, 8]

```

```

#The grid class works with a 2D grid in (x,y) 0-based coordinates
#Information can be passed in and out using cell-numbered formats.

class Grid:

    def __init__(self,x,y,obstacles=[],icey=False):

	self.xsize,self.ysize=x,y
	self.x,self.y=0,0
	self.longest_path=[(0,0)]
	self.current_path=[(0,0)]
	self.obstacles=[]
	self.icey=icey

	#Convert numbered obstacles to coordinates	
	for o in obstacles:
	    self.obstacles.append(self.num_to_coord(o))

    #A valid move must be in the grid (0-size-1) and not an obstacle, and not 
    #already visisted.    
    def valid_move(self, coord):
	x,y=coord
	return (x >= 0 and x < self.xsize 
		and y >= 0 and y < self.ysize 
		and (x,y) not in self.obstacles 
		and (x,y) not in self.current_path)

    #Core of the problem solution
    #This recursive function simply tries all NSEW paths recursively. 

    def travel(self):
	startx,starty = self.x,self.y
	for move in ((0,1),(0,-1),(1,0),(-1,0)):
	    #For each of the valid NSEW choices, add it to the current path
	    #and check from there. If you end up with a longer path, update
	    #the longest path.
	    x,y=startx,starty
	    dx , dy=move
	    x += dx
	    y += dy

	    if self.valid_move((x,y)):
		steps=1
		self.current_path.append((x,y))

		#Keep moving in the same direction if in icey mode
	    	if self.icey:
		    while self.valid_move((x+dx,y+dy)):
			x += dx
			y += dy
			self.current_path.append((x,y))
			steps+=1

		if len(self.current_path) > len(self.longest_path):
		    self.longest_path = self.current_path[:]
		self.x,self.y=x,y
		self.travel()
		self.current_path=self.current_path[0:-steps]

    #Convert (x,y) format to cell-numbered format (i,e, (0,0)->1, (0,1)->2, etc)
    def coord_to_num(self,x,y):
	return y*self.xsize+x+1

    #Convert cell-numbered to (x,y) format
    def num_to_coord(self, num):
	return ((num-1) % self.ysize), ((num-1) / self.xsize) 

    def get_result(self):
	return [self.coord_to_num(x,y) for x,y in self.longest_path]

if __name__=="__main__":
    testset=[[3,12,15],[],[2,3,7,10,14,15],[2,6,11],[4,5,9,12,13],[4,5,9,10,13]]
    for obs in testset:
	grid=Grid(4,4,obs)
	grid.travel()    
	result=grid.get_result()
	print len(result),":","(%s)"%obs,"-",result

	grid=Grid(4,4,obs,icey=True)	
	grid.travel()    
	result=grid.get_result()
	print "icey:",len(result),":","(%s)"%obs,"-",result


```

---

### Post by jblebrun on 2007-01-08
Hmmm, i just looked at the parent post, and the rules haven't been updated. Ghostdog, can you please fix the rules in the original post to reflect your reply #16, or remove that reply completely?

---

### Post by ghostdog74 on 2007-01-08
> **jblebrun said:**
> Hmmm, i just looked at the parent post, and the rules haven't been updated. Ghostdog, can you please fix the rules in the original post to reflect your reply #16, or remove that reply completely?

hi
i have edited. My original intention was to turn anyway you like, left or right or keep going straight(but cannot go back) , so as to find the max path. For this to work, the algorithm might be a tad too complex, so someone suggested go straight line when there's no obstacle until it hits one , for simplicity.
The solution can be the straight line only rule,  or the more complex one, or both....

---

### Post by Wybiral on 2007-01-08
Personally I don't think it was more complex with the any direction rule, in fact, my straight line version is bigger because I had to check if the straight path was OK before check the others.

---

### Post by cocteau on 2007-01-08
Hi

So after two bothced attemps and loads of serious head scratching I have come up with this reply i C++. In order to make it easier for myself I have allowed a few simplifications of the original puzzle.

First this only finds a route when it can turn on every node, not just when it hits an obstacle.
Second I changed all nodes in the grid to single chars, not numbers.

This solution finds all the routes through the grid before determining which is the longest. You can uncomment two places in the code (where noted) to have it print all the routes as well. 

This also works on other grid sizes as long as the dimensions are equal. I.e. the x and y axis must have the same length. To use other grids change the drawGrid function.

```

#include <iostream>
#include <vector>
#include <string>

using std::cout;			using std::endl;
using std::vector;		using std::string;

//populate a vector with the grid
//I changed the symbols from the original puzzle to symplify the
//types I work with in this puzzle.
//
//vector is x-axis, string is y-axis.
void drawGrid(vector<string>& vec)
{
	vec.push_back("159D");
	vec.push_back("26AE");
	vec.push_back("X7BX");
	vec.push_back("48XG");
	
	return;
}

//print the grid
void printGrid(const vector<string>& vec)
{
	for (int i = 0; i != vec.size(); ++i) {
		for (int j = 0; j != vec[i].size(); ++j) {
			cout << vec[j][i] << " ";
		}
		
		cout << endl;
	}
	
	return;
}

//return the x - coordinate of a node in the grid
int getx(const vector<string>& grid, char coordinate)
{
	for (int i = 0; i != grid.size(); i++) {
		for (int j = 0; j != grid[i].size(); j++) {
			if ( coordinate == grid[i][j] )
				return i;
		}
	}
	
	return -1;
}

//return the y - coordinate of a node in the grid
int gety(const vector<string>& grid, char coordinate)
{
	for (int i = 0; i != grid.size(); i++) {
		for (int j = 0; j != grid[i].size(); j++) {
			if ( coordinate == grid[i][j] )
				return j;
		}
	}
	
	return -1;
}

//checks to see if node already exists in path.
bool existInPath(const string& szPath, char x)
{
	string::const_iterator iter = szPath.begin();
	
	while ( iter != szPath.end() ) {
		if ( *iter == x )
			return true;

		iter++;
	}

	return false;
}
	

//find all possible routes through the grid.
vector<string> findPath(const vector<string>& grid)
{
	vector<string> completePaths, stack;
	char currentPosition = '1';						//start point in the grid
	int x = 0, y = 0;
	string currentPath;
	bool pathRunning = true, found = true;
	currentPath = currentPosition;
	
	while ( pathRunning ) {
		found = false;
		x = getx(grid, currentPosition);
		y = gety(grid, currentPosition);
		
		if ( x - 1 >= 0 && grid[x - 1][y] != 'X' && !existInPath(currentPath, grid[x - 1][y]) ) {
			found = true;
			currentPosition = grid[x - 1][y];
		}
		
		if ( y - 1 >= 0 && grid[x][y - 1] != 'X' && !existInPath(currentPath, grid[x][y - 1]) ) {
			if ( found ) {
				stack.push_back( currentPath + grid[x][y -1] );
			} else {
				found = true;
				currentPosition = grid[x][y - 1];
			}
		}
		
		if ( x + 1 < grid.size() && grid[x + 1][y] != 'X' && !existInPath(currentPath, grid[x + 1][y]) ) {
			if ( found ) {
				stack.push_back( currentPath + grid[x + 1][y] );
			} else {
				found = true;
				currentPosition = grid[x + 1][y];
			}
		}
		
		if ( y + 1 < grid[x].size() && grid[x][y + 1] != 'X' && !existInPath(currentPath, grid[x][y + 1]) ) {
			if ( found ) {
				stack.push_back( currentPath + grid[x][y + 1] );
			} else {
				found = true;
				currentPosition = grid[x][y + 1];
			}
		}
		
		//if found is true, add char to string of coordinates, otherwise continue previously stacked path.
		if ( found ) {
			currentPath += currentPosition;
		} else {
			completePaths.push_back(currentPath);
			pathRunning = true;		//set this to false to make it runs only once.
			
			if ( !stack.empty() ) {
				currentPath = stack[stack.size() - 1];
				stack.pop_back();
				currentPosition = currentPath[currentPath.size() - 1];
			} else {
				pathRunning = false;
			}
		}
		
	}
	
	return completePaths;
}

int main()
{
	vector<string> grid, completePaths;
	vector<char> vec;
	int longestPathIndex = 0;

	drawGrid(grid);
	printGrid(grid);
	
	completePaths = findPath(grid);

	//uncomment next to 'cout's to print all possible paths through the grid.	
	//cout << "List of possible paths: " << endl;
	for (vector<string>::size_type i = 0; i != completePaths.size(); ++i) {
		//cout << completePaths[i] << endl;					
		if ( completePaths[i].size() > completePaths[longestPathIndex].size() )
			longestPathIndex = i;
	}
	
	cout << "Longest path is: " << completePaths[longestPathIndex] << endl;


	return 0;
}
```

In case you just want to see the pathfinder loop of the code, as this is where the puzzle challenge is anyway, I copied it here:

```

//find all possible routes through the grid.
vector<string> findPath(const vector<string>& grid)
{
	vector<string> completePaths, stack;
	char currentPosition = '1';						//start point in the grid
	int x = 0, y = 0;
	string currentPath;
	bool pathRunning = true, found = true;
	currentPath = currentPosition;
	
	while ( pathRunning ) {
		found = false;
		x = getx(grid, currentPosition);
		y = gety(grid, currentPosition);
		
		if ( x - 1 >= 0 && grid[x - 1][y] != 'X' && !existInPath(currentPath, grid[x - 1][y]) ) {
			found = true;
			currentPosition = grid[x - 1][y];
		}
		
		if ( y - 1 >= 0 && grid[x][y - 1] != 'X' && !existInPath(currentPath, grid[x][y - 1]) ) {
			if ( found ) {
				stack.push_back( currentPath + grid[x][y -1] );
			} else {
				found = true;
				currentPosition = grid[x][y - 1];
			}
		}
		
		if ( x + 1 < grid.size() && grid[x + 1][y] != 'X' && !existInPath(currentPath, grid[x + 1][y]) ) {
			if ( found ) {
				stack.push_back( currentPath + grid[x + 1][y] );
			} else {
				found = true;
				currentPosition = grid[x + 1][y];
			}
		}
		
		if ( y + 1 < grid[x].size() && grid[x][y + 1] != 'X' && !existInPath(currentPath, grid[x][y + 1]) ) {
			if ( found ) {
				stack.push_back( currentPath + grid[x][y + 1] );
			} else {
				found = true;
				currentPosition = grid[x][y + 1];
			}
		}
		
		//if found is true, add char to string of coordinates, otherwise continue previously stacked path.
		if ( found ) {
			currentPath += currentPosition;
		} else {
			completePaths.push_back(currentPath);
			pathRunning = true;		//set this to false to make it runs only once.
			
			if ( !stack.empty() ) {
				currentPath = stack[stack.size() - 1];
				stack.pop_back();
				currentPosition = currentPath[currentPath.size() - 1];
			} else {
				pathRunning = false;
			}
		}
		
	}
	
	return completePaths;
}
```

---

### Post by jblebrun on 2007-01-08
> **ghostdog74 said:**
> hi
i have edited. My original intention was to turn anyway you like, left or right or keep going straight(but cannot go back) , so as to find the max path. For this to work, the algorithm might be a tad too complex, so someone suggested go straight line when there's no obstacle until it hits one , for simplicity.
The solution can be the straight line only rule,  or the more complex one, or both....

Depending on the approach that you use to solve it, there is really no difference in the complexity of the algorithm. If you look at my code, the straight line solution is actually the "more complex" option, since it requires executing an additional block of code.

---

### Post by eteran on 2007-01-08
Ok here is mine, written in Tcl. Works fine and i'm quite satisfied with it.
Was fun though, thanks for the challenge.

[http://paste.tclhelp.net/?id=81m](http://paste.tclhelp.net/?id=81m)

Some example output:
[php]
-- Grid -------------------------
 1       2       X       4
 5       6       7       8
 9      10      11       X
13      14       X      16
---------------------------------


-- Longest Path -----------------
1 -> 2 -> 6 -> 5 -> 9 -> 13 -> 14 -> 10 -> 11 -> 7 -> 8 -> 4 (11 moves)
---------------------------------
[/php]

P.S. We're in 2007 allready ;)

---

### Post by Wybiral on 2007-01-08
> P.S. We're in 2007 already

lol, wow...
I didn't notice that until you mentioned it. Shows how observant I am...

---

### Post by ghostdog74 on 2007-01-08
oops..lol..my bad...
how can i change the thread title though?

---

### Post by jblebrun on 2007-01-09
I like these weekly programming challenges.  Someone suggested a monthly programming challenges as well, with slightly more substantial projects.

Does anyone who reads these have the power to create new subforums (and to move previous challenge threads to the new forum, as appropriate?)

---

### Post by eteran on 2007-01-09
Although I like the idea of grouping the Challenge Threads, I think the chances newcomers - like me - find those, are bigger when they are kept here.

---

### Post by jblebrun on 2007-01-09
> **eteran said:**
> Although I like the idea of grouping the Challenge Threads, I think the chances newcomers - like me - find those, are bigger when they are kept here.

You're saying you wouldn't notice a subform called "Programming Challenges" located directly next to "Programming Talk" in the forum list?

---

### Post by eteran on 2007-01-09
I was thinking that you were suggesting to make it a subforum of Programming Talk, like the Packaging is one, and gets little attention.

But that gets OT, I'm fine with either way, as long as the challenges persist :)

---

### Post by jayemef on 2007-01-09
For the time being, you can always do a search for "weekly programming." Brings up all the challenge threads in order of what has been posted to last.

---

### Post by jblebrun on 2007-01-10
> **jayemef said:**
> For the time being, you can always do a search for "weekly programming." Brings up all the challenge threads in order of what has been posted to last.

Indeed, and that's what I already do. It just seems to me that since it's hopefully going to be an on-going thing, it might be nice to have all challenges grouped together neatly. It might also encourage different types of challenges to pop up... like "Python Challenge" or "Team Challenges" or "Monthly Challenges" or whatever. Could end up being lots of fun!

---

### Post by jblebrun on 2007-01-11
This thread is quiet! The inherently recursive nature of this problem is begging for a Lisp/Scheme solution! And a Lispy ruby solution, of course. Maybe I should try a ruby solution....

---

### Post by Wybiral on 2007-01-12
It's next week... Wheres the challenge?

---

### Post by jblebrun on 2007-01-12
> **Wybiral said:**
> It's next week... Wheres the challenge?

Oops, I am slipping up! It will be up in the next 5-10 minutes!

---

### Post by dwblas on 2007-01-12
Maybe 'the chooser' should be choosing two weeks ahead, currently that would be for the challenge starting on the 19th, so who ever would have a week to decide what they wanted to do.

---

### Post by jblebrun on 2007-01-12
> **dwblas said:**
> Maybe 'the chooser' should be choosing two weeks ahead, currently that would be for the challenge starting on the 19th, so who ever would have a week to decide what they wanted to do.

Well, another possibility is that you should submit your entry with enough confidence that you think you will win, and so you have something ready to go! If you don't have a challenge, and don't want to come up with one, you should state that when you submit your example! We don't want people avoiding the game because they don't want to come up with challenges!

---

