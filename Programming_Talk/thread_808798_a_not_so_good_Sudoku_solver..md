---
title: "a not so good Sudoku solver."
date: 2008-05-26
forum: Programming Talk
---

### Post by slavik on 2008-05-26
Congratulations, you have been chosen to look at more of my ugly C code.

This time it is a sudoku solver that can solve 9 by 9 sudokus in about 3 seconds (on my system, 2.4GHz C2Q).

Some notes (mostly bad things):
- Can only do 9x9 (hard coded)
- Checks the entire board at the end of the game to ensure that the solution is correct. This is bad because I check each number as it goes in, but only in rows and column, not in 3x3 squares. This is bad because if the end check fails, the code has to backtrack a lot. Ideally, the number check would check everything (row, column, and 3x3 squares) so that once the board is full, you know that the puzzle is solved.
- Single threaded
- The puzzle is a shameless rip out of gnome-sudoku (a hard puzzle)
- It took me a 4 hour period to write the code (off and on, so there was maybe at most 2 hours of coding)

Plans for future (what I hoped to do before laziness set in):
- soft code the size (so that different sizes were possible, up to 49x49 if I could find a puzzle and the solution)
- fix the number checking routine to check for the small squares (the size needs to be soft coded first)
- multithread (not multiple processes, but multiple threads), maybe try out openmp?

And now, here is the code:

[php]
/*
 *      sudoku.c
 *      
 *      Copyright 2008 Vyacheslav Goltser <slavikg@gmail.com>
 *      
 *      This program is free software: you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation, either version 3 of the License, or
 *      (at your option) any later version.
 *      
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *      
 *      You should have received a copy of the GNU General Public License
 *      along with this program.  If not, see <http://www.gnu.org/licenses/>.
 *      
 */

// Linear 9x9 sudoku solver (no SMP).

#include <stdio.h>

#define SIZE9

//only size 9 works ... this needs to be redone ...

#ifdef SIZE9
#define CHECK chsol9
#define SIZE 9
#elif defined(SIZE16)
#define CHECK chsol16
#define SIZE 16
#else
#define CHECK chsol25
#define SIZE 25
#endif

// puzzle is global to avoid an extra argument to the puzzle.
// ultimately, this should be made more object oriented, where
// the puzzle would solve itself ( puzzle.solve() ) or some such
int puzzle[SIZE][SIZE] = {
	{0,0,4,1,0,0,3,0,0},
	{0,7,0,0,0,8,0,0,1},
	{0,0,0,0,0,0,7,0,9},
	{8,0,3,0,5,9,0,0,2},
	{0,0,9,6,0,1,5,0,0},
	{1,0,0,8,2,0,9,0,4},
	{6,0,1,0,0,0,0,0,0},
	{4,0,0,3,0,0,0,9,0},
	{0,0,8,0,0,4,2,0,0}
};

// validate the puzzle
// returns 1 if puzzle is valid, 0 otherwise
int isvalid(int pos, int num) {
	int row = pos/SIZE; //which row
	int col = pos%SIZE; //which col
	int i;

	//check rows and columns
	for(i = 0; i < SIZE; i++) {
		if ((puzzle[row][i] == num || puzzle[i][col] == num)) return 0;
	}

	return 1;
}

// check the puzzle validity for 9x9
int chsol9() {
	int i,j,k,l,a,b;
	int sum;

	for(k = 0; k <= 2; ++k) {
		for(l = 0; l <= 2; ++l) {
			sum = 0;
			for(i = 0; i <= 2; ++i) {
				for(j = 0; j <= 2; ++j) {
					for(a = 0; a <= 2; ++a) {
						for(b = 0; b <= 2; ++b) {
							if ((puzzle[i+(k*3)][j+(l*3)] == puzzle[a+(k*3)][b+(l*3)])
							&&(i+(k*3) != a+(k*3))) return 0;
						}
					}
					//sum += puzzle[i+(k*3)][j+(l*3)];
				}
			}
			//if (sum != 45) return 0;
		}
	}
	return 1;
}

// same as chsol9()
int chsol16() {
	int i,j,k,l;
	int sum;

	for(k = 0; k <= 2; ++k) {
		for(l = 0; l <= 2; ++l) {
			sum = 0;
			for(i = 0; i <= 2; ++i) {
				for(j = 0; j <= 2; ++j) {
					sum += puzzle[i+(k*3)][j+(l*3)];
				}
			}
			if (sum != 45) return 0;
		}
	}
	return 1;
}

// same as chsol9()
int chsol25() {
	int i,j,k,l;
	int sum;

	for(k = 0; k <= 2; ++k) {
		for(l = 0; l <= 2; ++l) {
			sum = 0;
			for(i = 0; i <= 2; ++i) {
				for(j = 0; j <= 2; ++j) {
					sum += puzzle[i+(k*3)][j+(l*3)];
				}
			}
			if (sum != 45) return 0;
		}
	}
	return 1;
}

// solve the puzzle
// returns 1 on found solution, 0 otherwise
int solve(int pos) {
	int row;
	int col;
	int num;

	if (pos == SIZE*SIZE) return CHECK();

	row = pos/SIZE;
	col = pos%SIZE;
	
	while(puzzle[row][col] != 0) {
		pos++;
		row = pos/SIZE;
		col = pos%SIZE;
	}
	if (pos == SIZE*SIZE) return CHECK();

	for (num = 1; num <= SIZE; num++) {
		if(isvalid(pos, num)) {
			puzzle[row][col] = num;
			if (solve(pos+1)) return 1;
			else puzzle[row][col] = 0;
		}
	}
	return 0;
}

int main(int argc, char** argv)
{
	int i, j;

	solve(0);
	
	for(j = 0; j < SIZE; ++j) {
		for(i = 0; i < SIZE; ++i) {
			printf("%d ",puzzle[j][i]);
		}
		printf("\n");
	}
	return 0;
}
[/php]

---

### Post by Can+~ on 2008-05-26
[PHP]    for(k = 0; k <= 2; ++k) {
        for(l = 0; l <= 2; ++l) {
            sum = 0;
            for(i = 0; i <= 2; ++i) {
                for(j = 0; j <= 2; ++j) {
                    for(a = 0; a <= 2; ++a) {
                        for(b = 0; b <= 2; ++b) {
                            if ((puzzle[i+(k*3)][j+(l*3)] == puzzle[a+(k*3)][b+(l*3)])
                            &&(i+(k*3) != a+(k*3))) return 0;
                        }
                    }
                    //sum += puzzle[i+(k*3)][j+(l*3)];
                }
            }
            //if (sum != 45) return 0;
        }
    }
    return 1;
} [/PHP]

hexa[FONT="Courier New"]for[/FONT]-C-C-C-Combo.

Don't worry, that's why you'll eventually pick up the project later and make it better, we all have to do terrible code at start. Mostly, try to pick up a piece of paper and sketch the algorithm (guessing you invented a brute force solution from scratch).

---

### Post by slavik on 2008-05-26
the thing is, will an 3x3 box filled in, doing all_different is still n^2 (unless I am missing something)

also, that piece in particular, I just got it to the point where it works and left it alone. First I get code that actually works, then I try to make it nicer.

---

### Post by Paul Miller on 2008-05-27
I didn't have time to read your C code, but here's a link to a short (110-lines, well-commented) Python script that solves any sudoku in the blink of an eye: [http://norvig.com/sudoku.html]("http://norvig.com/sudoku.html")

I hope it helps you out.

---

### Post by slavik on 2008-06-28
> **Paul Miller said:**
> I didn't have time to read your C code, but here's a link to a short (110-lines, well-commented) Python script that solves any sudoku in the blink of an eye: [http://norvig.com/sudoku.html]("http://norvig.com/sudoku.html")

I hope it helps you out.
it uses constraint programming, which is something Prolog is very good at and much easier to do. :)

---

