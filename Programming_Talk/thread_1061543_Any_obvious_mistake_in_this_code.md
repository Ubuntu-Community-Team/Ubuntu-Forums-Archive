---
title: "Any obvious mistake in this code?"
date: 2009-02-05
forum: Programming Talk
---

### Post by geo909 on 2009-02-05
Hello everybody,
I could really use some help here, if you can 
have a look I would be grateful.

I have to make a program in C that solves a sudoku 
using backtracking. 

It reads a file with a sudoku, where the missing numbers are
denoted by a 0.

I don't have any problems with technicalities like
reading the file, placing everything in a 9X9 int array
etc. Everything but the backtracking works perfectly.

To make my life easier, I have made a function
```
int can_put_n_here(int n, int sudoku[][9] ,int a, int b)
```
that takes as arguments an integer n, a 9X9 integer array (the sudoku matrix) and two integers a and b, and returns 1 if n is allowed to be
put in the coordinates(a,b) of the sudoku matrix and 0 if it is not.

Now, the problem is with the backtracking function.
I just cannot see what is the problem (mind that I am 
totally unexperienced!!):

```

void backtrack(int sudoku[][9])
{
int i,j,n;
for(i=0; i<9; ++i){
	for(j=0; j<9; ++j){
		if(sudoku[i][j]==0){
			for(n=1; n<10; ++n){
				if(can_put_n_here(n,sudoku,i,j)==1){
					sudoku[i][j]=n;
					backtrack(sudoku);
				}
			}
		}
	}
}

}

```

So, under these recursions, shouldn't the matrix 'sudoku' be 
a solved one in the end?! This is not the case...

If any more experienced eye can see the flaw in this, please
help!!

Thanks in advance..

---

### Post by croto on 2009-02-06
I think the problem is here:
```

if(can_put_n_here(n,sudoku,i,j)==1){
					sudoku[i][j]=n;
					backtrack(sudoku);
				}

```

I would put the problem like this. Your algorithm solves sudoku getting deeper into the recursion. But suppose that, at some level in the recursion, there is no place where you can put a number. In that case, your algorithm would just exit to the previous level, which won't be able to put any number, and will exit to the previous level, etc. til it exits the program. That's not what you want. You would like that when a level is stuck, the previous level would do try something different. I think the solution to that is:
```

if(can_put_n_here(n,sudoku,i,j)==1){
					sudoku[i][j]=n;
					backtrack(sudoku);
                                       sudoku[i][j]=0;
				}

```

Now the problem is figuring out when you actually filled in every square, or in other words, when you are in the last level of the recursion (81?), probably you need to keep that in a variable.

I may be wrong. But I gotta go to sleep too. Let me know what happens!

---

### Post by croto on 2009-02-06
Also, your algorithm is correct, but it solves sudoku by trying every possible combination of numbers in the matrix, which is 9^(81-# of initially filled places). That number, unfortunately, is HUGE. To give you an idea. Your number is roughly 10^77. Keep that somewhere. Now, the number of stars in a galaxy is 10^10, and there are 10^11 galaxies in the universe. So there are 10^21 stars in the universe. Still WAYYYYY smaller than your number. Now, a star may be 10^30 kg. So the total mass in stars in the universe is 10^51 kg. Still WAYYYYY smaller than your number. There are 10^27 protons&neutrons in a kilogram, which tells us that there are 10^78 protons&neutrons in stars in the fricking whole universe. Conclusion, your program has to try numbers as many times as protons&neutrons in all the stars in the universe. Don't hold your breath for your algorithm to give you the solution.

---

### Post by kavon89 on 2009-02-06
You should add some actual logic to your sudoku solver instead of just trying to brute force the answer.

---

### Post by nvteighen on 2009-02-06
You have to solve (in principle) 81 variables. And you've got 9 (verticals) + 9 (horizontals) + 9 (squares) = 27 equations that all sum exactly 45 (1 + 2 + 3 + ... 9 = 55).

Ok, that's a lot. But, first: a sudoku never starts blank, so there are less than 81 variables to solve. And then, you know by definition that all variables are in the interval [1, 9]. And they're all first-order linear equations.

If you have exactly 27 variables left, you can use [Gaussian Elimination]("http://en.wikipedia.org/wiki/Gaussian_elimination") to solve them all in a glance. So, what I'd do is to try to get to that situation.

---

### Post by dburnett77 on 2009-02-06
> **geo909 said:**
> Hello everybody,
I could really use some help here, if you can 
have a look I would be grateful.

I have to make a program in C that solves a sudoku 
using backtracking. 

It reads a file with a sudoku, where the missing numbers are
denoted by a 0.

I don't have any problems with technicalities like
reading the file, placing everything in a 9X9 int array
etc. Everything but the backtracking works perfectly.

To make my life easier, I have made a function
```
int can_put_n_here(int n, int sudoku[][9] ,int a, int b)
```
that takes as arguments an integer n, a 9X9 integer array (the sudoku matrix) and two integers a and b, and returns 1 if n is allowed to be
put in the coordinates(a,b) of the sudoku matrix and 0 if it is not.

Now, the problem is with the backtracking function.
I just cannot see what is the problem (mind that I am 
totally unexperienced!!):

```

void backtrack(int sudoku[][9])
{
int i,j,n;
for(i=0; i<9; ++i){
	for(j=0; j<9; ++j){
		if(sudoku[i][j]==0){
			for(n=1; n<10; ++n){
				if(can_put_n_here(n,sudoku,i,j)==1){
					sudoku[i][j]=n;
					backtrack(sudoku);
				}
			}
		}
	}
}

}

```

So, under these recursions, shouldn't the matrix 'sudoku' be 
a solved one in the end?! This is not the case...

If any more experienced eye can see the flaw in this, please
help!!

Thanks in advance..

Wrong call on variable [i] within the function.  Parameters are not being passed correctly.  You defined it in the calling function as non-defined.  Linear, then take it to 2 dimensional within the function_define.  In other words, you initialized it with one variable, than handled it with two.  Mismatch.  Don't hack out your error codes to look good.  A trace function would have highlited it.

---

### Post by croto on 2009-02-06
dburnett77, I'm not sure of what you're saying, but if I'm understanding correctly, I don't think what you're saying is right. He's declaring the multidimensional input array as sudoku[][9], which in C is a perfectly valid declaration of a 2-dimensional array. 
A one dimensional array doesn't need the length declared in the function call, because it isn't necessary to address any element of the array. For an N-dimensional array, the length of the first dimension is in the same way not needed for anything, so it can be omitted.
I think geo909's declarations and definitions are just fine.

---

### Post by Npl on 2009-02-06
> **nvteighen said:**
> You have to solve (in principle) 81 variables. And you've got 9 (verticals) + 9 (horizontals) + 9 (squares) = 27 equations that all sum exactly 45 (1 + 2 + 3 + ... 9 = 55).

Ok, that's a lot. But, first: a sudoku never starts blank, so there are less than 81 variables to solve. And then, you know by definition that all variables are in the interval [1, 9]. And they're all first-order linear equations.

If you have exactly 27 variables left, you can use [Gaussian Elimination]("http://en.wikipedia.org/wiki/Gaussian_elimination") to solve them all in a glance. So, what I'd do is to try to get to that situation.Try this and report back :p.
Hint 1: You`re wrong.
Hint 2: Restricting the solution to discrete values will prove the big problem.

---

### Post by nvteighen on 2009-02-06
> **Npl said:**
> Try this and report back :p.
Hint 1: You`re wrong.
Hint 2: Restricting the solution to discrete values will prove the big problem.
It should work. I'm only working with the definition on how Sudoku works... there's only discrete values from 1-9 and each equation sums up to the very same number per definition. Where's my mistake?

---

### Post by geo909 on 2009-02-06
Hey guys, thank you so much for taking the time to answer thi,
I really appreciate it.

Thanks Kroto, I think I get the idea now, I'll have to make the algorithm "backtrack" when I have a box where no number can be placed . I will try to correct it and let you know what happened. I have some things running and I will probably won't have time to do that until tomorrow.

Just a comment about efficiency:

This is not about making an efficient sudoku-solving algorithm; I am a math student (unfortunately not experienced in programming) and taking a combinatorics course where we look different ways to enumerate, search and generate various combinatorial structures. We did backtracking and a good way (and not so tough) to see that is to do this sudoku-solver to see it in practice.

That said, backtracking is by no means an exhaustive search! First of all, as nveitghen mentioned you don't start with an empty 9X9 matrix. Then, if you see all the possible solutions as a tree where in each node you have 9 branches, then for every box that doesn't have a solution, if you backtrack, it is like cutting the node and ignore all the branches  below. That's a lot! Anyway, I will certainly not hold my breath until this one gives a solution and there must certainly be some smarter ways,
but I just want to implement backtracking in practice..

I will let you know what I did soon, probably by tomorrow.

---

### Post by Npl on 2009-02-06
> **nvteighen said:**
> It should work. I'm only working with the definition on how Sudoku works... there's only discrete values from 1-9 and each equation sums up to the very same number per definition. Where's my mistake?The variables and also equations arent linear/continuos which is required for GE to work. You will end up running discrete values 1-9 through all variables to see which fit... which aint an improvement from the original algorithm.
Discrete Problems like this are hard to solve exactly for the reason that, most of the time, you cant use algorithms from calculus.

---

### Post by PythonPower on 2009-02-06
A back-tracking solution should be easy to find. Consider each square had all possibilities written in them. All that is needed is for one square to be decided and that restricts lots of other squares as well.

This Python 2.5 program I made ages ago shows what I mean:

[PHP]
from copy import copy, deepcopy

grid = []

for line in open('sudoku'):
	line = line[:len(line)-1]
	for c in line:
		if c == '0': grid += ['123456789']
		else: grid += [c]


def getrow(x, y):
	r = []
	for i in xrange(9):
		if i != x: r += [9*y+i]
	
	return r

def getcol(x, y):
	r = []
	for j in xrange(9):
		if j != y: r += [9*j+x]
	
	return r

def getrange(x, y):
	r = []
	for i in xrange(x-x%3, x-x%3+3):
		for j in xrange(y-y%3, y-y%3+3):
			if i != x or j != y:
				r += [9*j+i]
	
	return r

def getall(x, y):
	s = set(getrange(x, y)+getrow(x, y)+getcol(x, y))
	r = []
	for a in s: r += [a]
	return r

next = []
for y in xrange(9):
	for x in xrange(9):
		next += [getall(x, y)]


def make(grid, s, v):
	grid[s] = v
	
	check = []
	for a in next[s]:
		if len(grid[a]) != 1: check += [a]
		grid[a] = grid[a].replace(v, '')
		
	
	for a in check:
		if len(grid[a]) == 1:
			make(grid, a, grid[a])

def ways(grid):
	r = 1
	for a in grid: r *= len(a)
	return r

def draw(grid):
	for i in xrange(81):
		print grid[i],
		if i%9 == 8: print
	

def search(grid):
	scale = ways(grid)
	if scale == 0: return
	
	if scale == 1:
		draw(grid)
		quit()
		return
	
	best = 0
	bestl = 10
	for a in xrange(81):
		l = len(grid[a])
		if l > 1 and l < bestl:
			best = a
			bestl = l
	
	for v in grid[best]:
		new = copy(grid)
		make(new, best, v)
		search(new)
	

for i in xrange(81):
	if len(grid[i]) == 1:
		make(grid, i, grid[i])

search(grid)

[/PHP]

It opens a file called 'sudoku' and prints the first solution it finds. The file format should be each row on a new line with no spaces or anything else.

---

### Post by nvteighen on 2009-02-06
> **Npl said:**
> The variables and also equations arent linear/continuos which is required for GE to work. You will end up running discrete values 1-9 through all variables to see which fit... which aint an improvement from the original algorithm.
Discrete Problems like this are hard to solve exactly for the reason that, most of the time, you cant use algorithms from calculus.

I see, it is Gauss who "complains". 

But, if the initial state is given by natural numbers and the sum is also natural, is there a possibility a rational number could appear as a solution to one variable?

---

### Post by croto on 2009-02-06
> **geo909 said:**
> That said, backtracking is by no means an exhaustive search! First of all, as nveitghen mentioned you don't start with an empty 9X9 matrix. Then, if you see all the possible solutions as a tree where in each node you have 9 branches, then for every box that doesn't have a solution, if you backtrack, it is like cutting the node and ignore all the branches  below. That's a lot! Anyway, I will certainly not hold my breath until this one gives a solution and there must certainly be some smarter ways,
but I just want to implement backtracking in practice..

I will let you know what I did soon, probably by tomorrow.

I agree with you... it's not exactly exhaustive, since you're trimming the tree of all possibilities whenever you get stuck at a level. However, I'm afraid the tree trimming is not efficient enough to actually get to a solution. I guess something along your algorithm line of thought that could be implemented is, instead of trying numbers and getting deeper into the recursion in row-column order, it will be more efficient to check at the current level how many possible numbers can be put into each square and start with the one with less possibilities (hopefully there will be only one possibility for that square, in which case that number will be correct and you wouldn't waste time in that recursion). Anyways, it's a nice problem.

---

### Post by PythonPower on 2009-02-06
My backtracking solution can be made to find all solutions, if I remember correctly... Just replace the line:

[PHP]quit()[/PHP]

With:

[PHP]print[/PHP]

It should return all solutions then.

---

### Post by Npl on 2009-02-06
> **nvteighen said:**
> I see, it is Gauss who "complains". 

But, if the initial state is given by natural numbers and the sum is also natural, is there a possibility a rational number could appear as a solution to one variable?The problem is that you have an underdetereminated system and will get a infinite number of possible solutions (with the variables beeing real numbers).

Err.. to make clear whats the problem, lets do something different: look at prime-factorization (has nothing to do with GE, but the problem is the same and easier to explain). You got that really big number n and want top find prime-factors, finding 2 **real** variables x,y so that x*y = n, is very easy and there are many (infinite). The problem will then be that you have alot of (x,y) tuples which satisfy x*y=n as solution, but then have the **problem of sorting out the ones where x and y are integers** - in the end you dint safe yourself any work.

---

### Post by c174 on 2009-02-06
Hi geo909

You are really close! The main problem in your algorithm is that you pass the original "sudoku" to the next level of iteration. If the new level fails, the algorithm cannot fall back to the previous state -- because it was modified (and unfortunately by a value that didn't work on the long run :)).

Take a look at this (I compiled with g++). I put a simple can_put_n_here-function, but it doesn't enforce all the rules of sudoku.

[PHP]#include <iostream.h>

int can_put_n_here(int n, int sudoku[9][9], int i, int j)
{
    int m;    
    for( m=0; m<9; m++ ) if( sudoku[i][m] == n ) return 0;
    for( m=0; m<9; m++ ) if( sudoku[m][j] == n ) return 0;
    // add check of nine 3x3 matrices, in which digits 1-9 can only appear once
    return 1;
}


void backtrack(int sudoku[9][9])
{
    int i,j,n,m,l;

    for(i=0; i<9; ++i){
        for(j=0; j<9; ++j){
	        if(sudoku[i][j]==0){
	    	    for(n=1; n<10; ++n){
	    		    if(can_put_n_here(n,sudoku,i,j)==1) {
	    		    
	    		        // create a new candidate solution, and continue iteration on
	    		        // that one (keep the old one so we can fall back on that, if
	    		        // something goes wrong)
	    		        
	    		        // make a copy
	    			    int candidate[9][9];
	    			    for(m=0; m<9; m++ ) 
	    			        for(l=0; l<9; l++ )
	    			            candidate[m][l] = sudoku[m][l];
	    			            
	    			    // fill in trial value
	    			    candidate[i][j] = n;
	    			    
	    			    // recurse
	    			    backtrack(candidate);
	    		    }
	    	    }
	    	    
	    	    // none of the digits are allowed in this cell, so further iteration
	    	    // is waste of time
	    	    return;
	        }
	    }
    }
    
    // all fields are filled in, print solution
    printf( "\n\nSolution found:\n" );
    for(i=0; i<9; i++ ) {
        for(j=0; j<9; j++ ) {
            printf( "%3i", sudoku[i][j] );
        }
        printf( "\n" );
    }
}

int main( int argc, char* argv[] )
{
    int sudoku[9][9] = { 0, 0, 0, 9, 0, 5, 0, 6, 4,
                     4, 5, 7, 8, 0, 0, 9, 3, 1,
                     2, 0, 0, 0, 0, 1, 0, 0, 0,
                     0, 7, 0, 3, 0, 0, 0, 0, 0,
                     0, 8, 1, 0, 9, 0, 4, 2, 0,
                     0, 0, 0, 0, 0, 6, 0, 7, 0,
                     0, 0, 0, 1, 0, 0, 0, 0, 3,
                     5, 1, 3, 0, 0, 8, 7, 9, 2,
                     8, 6, 0, 7, 0, 3, 0, 0, 0 };

    backtrack( sudoku );
    return 0;                     
}[/PHP]

By the way, you'll see that in general we always have to create a "new"  variable (on the stack in this case) when using recursive methods. I hope you find this useful! :)

---

### Post by geo909 on 2009-02-06
> **c174 said:**
> 
By the way, you'll see that in general we always have to create a "new"  variable (on the stack in this case) when using recursive methods. I hope you find this useful! :)

That was very helpful indeed!! Thanks a lot!!
I am trying to understand the logic behind the creation
of a new variable. Thinking about recursive functions is 
so complicated for me.. But it is starting to make sense 
after a while..

Will let you know what happened.

Btw, just a small technical question:
I have forgotten most things about pointers and stuff but
if you want to copy an array to an array, you have to 
copy each value separately?

P.S. That's fun! I regret so much that I didn't take courses from the CSC department when I was an undergrad!!

---

### Post by geo909 on 2009-02-06
Re: Any obvious mistake in this code?
I have this running:
```


#include <stdio.h>
#include <stdlib.h>
#include "my_head.h"

void backtrack(int sudoku[][9])
{
int i,j=0,n;
int solution[9][9], candidate[9][9];
for(i=0; i<9; ++i){
	for(j=0; j<9; ++j){
		if(sudoku[i][j]==0){
			for(n=1; n<10; ++n){
				if( can_put_n_here(n,sudoku,i,j)){
					make_a_copy_of(sudoku,candidate);
					candidate[i][j]=n;
					backtrack(candidate);
				}
			}
		break;
		}
	}
}

}
```

The "make_a_copy_of" function copies the first matrix to the second.

How fast do you think that should be?!
It's been a couple of minutes that it is running..

EDIT: Still confused, but I guess in the end of the backtracking
progress, the solution will be 'candidate' and not 'sudoku',right?
So you should print out 'candidate'.. Tell me if I miss something.

Btw, since you've done all the job, here is a way to write your
"can_put_n_here" function and check if your's works as well:
```
/*Returns 1 if n is allowed in position [a,b] of sudoku[9][9] 
and 0 if not*/
int can_put_n_here(int n, int sdku[][9] ,int a, int b)
{
	int i;
	for(i=0; i<9; ++i){
		if(sdku[a][i]==n || sdku[i][b]==n || sdku[3*(a/3)][3*(b/3)+9*(i/3)+(i % 3)]==n)
			return(0);
	}
	return(1);
}

```

---

### Post by geo909 on 2009-02-07
At last!!
Solved!

Actually I googled a while and found the correct approach
written in.. err..I don't know what language this was..

Ok, so here's the deal:
Please, any comments on the code would be greatly appreciated,
I could really use some advice on technical stuff, logic, common
programming habits I didn't follow and whatever..

[B]
backtrack.c[/B]
```
#include <stdio.h>
#include <stdlib.h>
#include "my_head.h"

int backtrack(int sudoku[][9])
{
	int i,j,n,solution[9][9];

	if(sudoku_is_solved(sudoku))
		return 1;

	for(i=0; i<9; ++i){
		for(j=0; j<9; ++j){
			if(sudoku[i][j]==0){
				for(n=1; n<10; ++n){
					if( can_put_n_here(n,sudoku,i,j) ){
						sudoku[i][j]=n;
							if(backtrack(sudoku))
								return 1;
							sudoku[i][j]=0;
					}
				}
			return 0;
			}
		}
	}

}


```

[B]
my_functions.c[/B]
```
#include <stdio.h>
#include <stdlib.h>
#include "my_head.h"

/* A better version of fopen that checks for errors when 
opening file:*/ 
FILE *my_fopen(char *filename, char *mode)
{
	FILE *fp;
	if(!(fp=fopen(filename,mode))){
		printf("Error opening file %s!\n",filename);
		exit(-1);
	}
	return fp;
}

//Puts entries from our text files into a 9X9 int matrix
void read_sudoku_from_file(FILE *file, int sudoku[][9])
{
	int i,j;
	char c;
	for(i=0; i<9; ++i){
		j=0;
		while(fscanf(file,"%c",&c)!=EOF && c!='\n')
			sudoku[i][j++]=c-48;
	}
}

/*Returns 1 if n is allowed in position [a,b] of sudoku[9][9] 
and 0 if not*/
int can_put_n_here(int n, int sdku[][9] ,int a, int b)
{
	int i;
	for(i=0; i<9; ++i){
		if(sdku[a][i]==n || sdku[i][b]==n || sdku[3*(a/3)][3*(b/3)+9*(i/3)+(i % 3)]==n)
			return(0);
	}
	return(1);
}

//prints the sudoku nicely in the screen
void print_sudoku(int sdku[][9])
{
	int i;
		for(i=0; i<81; ++i){
			if (i%27==0) printf("\n\n");
			else if(i%9==0) printf("\n");
			else if (i%3==0) printf("  ");
				printf("%d ", sdku[0][i]);
		}
	printf("\n");
}

/*Returns 1 if the sudoku is solved and 0 if there
are still unassigned boxes*/
int sudoku_is_solved(int sudoku[][9])
{
	int i;
	for(i=0; i<81; ++i){
		if(sudoku[0][i]==0)
			return 0;
	}

	return 1;
}

```

[B]
sudoku.c[/B]
```
#include <stdio.h>
#include "my_head.h"

//usage: ./a.out sudoku.txt

int main(int argc, char *argv[])
{
	int sudoku[9][9];
	FILE* fp=my_fopen(argv[1],"r+");

	read_sudoku_from_file(fp, sudoku);

	printf("\n\nSudoku unsolved:");
	print_sudoku(sudoku);

	backtrack(sudoku);

	printf("\n\nSudoku solved:");
	print_sudoku(sudoku);

	return 0;
}

```

```
#ifndef MY_HEAD_H
#define MY_HEAD_H

FILE *my_fopen(char *, char *);
void read_sudoku_from_file(FILE *, int[][9]);
int can_put_n_here(int , int[][9] ,int , int );
void print_sudoku(int[][9]);
int backtrack(int[][9]);
int sudoku_is_solved(int[][9]);

#endif
 

```

EDIT: Can you please tell me a way to count the running time for a c program?
I remember there was some kind of function who could set the time or something..

---

### Post by andrewc6l on 2009-02-07
$ time ./progname 

will give you the real (clock) time, as well as the user and system time used by ./progname.

---

### Post by PythonPower on 2009-02-07
From a glance, your code sends the board to backtrack() which then tries adding any possible digit to any possible square and calls itself. On finding a solution it returns "true" and that signals that no more search is necessary.

That's all well and quite good. :)

I would propose some slight changes though. When you decide the value of one square that stops other squares being that value. If any of those squares now only have 1 option you can essentially set those squares to that option eliminating others. If any square has 0 options, no solution can be obtained. Bear in mind that you might have to start copying the board between function calls if you do this, so it might not help.

In addition, it *may* improve the average case complexity (although the worse case will remain the same) by deciding squares with fewer options first - you'll have to experiment. This point is minor but could help.

---

### Post by geo909 on 2009-02-07
> **PythonPower said:**
> From a glance, your code sends the board to backtrack() which then tries adding any possible digit to any possible square and calls itself. On finding a solution it returns "true" and that signals that no more search is necessary.

Not really... You have this 'for' loop with the 'n' there.
If n goes from 0 to 8 and n is not allowed in tha cell, then
'can_put_n_here' will return 0, so we will not get into that 'if'
at all and we will not call the function again from that point
because after it exits the 'for', it will return 0. So this 'path'
of solutions will not be chosen again; 

If you see a sudoku as a tree of 81 levels (each corresponding to one of the 9X9 squares) where each node has 9 branches(9 possible numbers
can be put there), this 'return 0' will cut the whole branch of solutions 
under the node we found that no number can be put.

So it does not try any possible solution, that's an important thing..

See also:
[http://en.wikipedia.org/wiki/Backtracking](http://en.wikipedia.org/wiki/Backtracking)

> 
I would propose some slight changes though. When you decide the value of one square that stops other squares being that value. If any of those squares now only have 1 option you can essentially set those squares to that option eliminating others. If any square has 0 options, no solution can be obtained. Bear in mind that you might have to start copying the board between function calls if you do this, so it might not help.

In addition, it *may* improve the average case complexity (although the worse case will remain the same) by deciding squares with fewer options first - you'll have to experiment. This point is minor but could help.

I will check that, though I am already confused with what I did!

---

### Post by geo909 on 2009-02-07
> **andrewc6l said:**
> $ time ./progname 

will give you the real (clock) time, as well as the user and system time used by ./progname.

Thanks!

Could you tell me what these mean?
```
real    0m0.030s
user    0m0.004s
sys     0m0.000s

```

What is real, user and sys?

---

### Post by andrewc6l on 2009-02-07
real is actual time spent (wall clock time). It includes everything.
user is time spent in user land (running your actual code).
sys is time spent in kernel mode (running kernel calls like malloc()) that are called by your code.

$ man time

will give you more info.

---

### Post by geo909 on 2009-02-07
> **andrewc6l said:**
> real is actual time spent (wall clock time). It includes everything.
user is time spent in user land (running your actual code).
sys is time spent in kernel mode (running kernel calls like malloc()) that are called by your code.

$ man time

will give you more info.

Well..

Every time I try *time* on the same puzzle I get different results!
Is there any c function that would work like this:
Just when you enter the main function you grub the time and you set
it in a variable t1, then you do the same before the end of the program for a variable t_2. Then before you exit you print t_2-t_1..
Is there something like this?

---

### Post by nvteighen on 2009-02-07
> **geo909 said:**
> Well..

Every time I try *time* on the same puzzle I get different results!
Is there any c function that would work like this:
Just when you enter the main function you grub the time and you set
it in a variable t1, then you do the same before the end of the program for a variable t_2. Then before you exit you print t_2-t_1..
Is there something like this?
Who told you execution speed is constant? You're running a whole OS too, not just your program ;)

But anyway, I doubt you get too different results each time.

---

### Post by c174 on 2009-02-07
Hi geo909

Congratulations! You found a very nice solution!

Did you actually try the solution I posted earlier? In post #19 you say something about it taking a long time to run. It should only take a few milliseconds.

> EDIT: Still confused, but I guess in the end of the backtracking
progress, the solution will be 'candidate' and not 'sudoku',right?
So you should print out 'candidate'.. Tell me if I miss something.
No, it is correct to print out the current 'sudoku'. If all the loops are passed without a new recursion it means that the passed in 'sudoku' is solved, so it actually holds the solution.

> Btw, since you've done all the job, here is a way to write your
"can_put_n_here" function and check if your's works as well:
Thanks! I tried it -- it works fine for me also:)

I like your solution because it solves the problem without allocating space for temporary Sudoku boards. Cool. However, you might know that sometimes a Sudoku can have more than one solution (grab a problem from I news paper and remove some of the initial entries). Your version will exit once a solution is found -- it will not detect other possible solution. The version a posted earlier does this, but it is a little slower than yours and uses more memory. So the "best" choice depends on what you need.

By the way, you can do without the sudoku_is_solved-function. Remove it from 'backtrace' and instead add a "return 1" at the end of 'backtrace';)

---

### Post by geo909 on 2009-02-07
> **c174 said:**
> Hi geo909

Congratulations! You found a very nice solution!


Well.. Literally "found it"!!
[http://see.stanford.edu/materials/icspacs106b/Lecture11.pdf](http://see.stanford.edu/materials/icspacs106b/Lecture11.pdf)

> Did you actually try the solution I posted earlier? In post #19 you say something about it taking a long time to run. It should only take a few milliseconds.


Yes.. I must have done something wrong because it would run forever.

> 
I like your solution because it solves the problem without allocating space for temporary Sudoku boards. Cool. However, you might know that sometimes a Sudoku can have more than one solution (grab a problem from I news paper and remove some of the initial entries). Your version will exit once a solution is found -- it will not detect other possible solution. The version a posted earlier does this, but it is a little slower than yours and uses more memory. So the "best" choice depends on what you need.

I see! Well, I think I will leave it now, I saw what I wanted to see.
I am still confused with all the recursion stuff though!


> By the way, you can do without the sudoku_is_solved-function. Remove it from 'backtrace' and instead add a "return 1" at the end of 'backtrace';)

Yes, indeed! I did that and it works fine!
Thanks for the help!!

---

### Post by c174 on 2009-02-07
Okay, good luck. It was fun working with this problem. Thanks for sharing:)

You can add printf-commands here and there in 'backtrace' to see better how it works. I would suggest something like

[PHP]void backtrack(int sudoku[9][9])
{
    int i,j,n,m,l;
    int debug = 0;
    static int level = 0;
    static int total = 0;
    
    if( debug ) {
        printf( "\n\nbacktrack call no: %i level: %i\n", ++total, level );
        printf( "current Sudoku\n" );
        for(i=0; i<9; i++ ) {
            for(j=0; j<9; j++ ) {
                printf( "%3i", sudoku[i][j] );
            }
            printf( "\n" );
        }
        getchar();
    }        

    
    for(i=0; i<9; ++i){
        for(j=0; j<9; ++j){
	        if(sudoku[i][j]==0){
	    	    for(n=1; n<10; ++n){
	    		    if(can_put_n_here(n,sudoku,i,j)==1) {
	    		    
	    		        // create a new candidate solution, and continue iteration on
	    		        // that one (keep the old one so we can fall back on that, if
	    		        // something goes wrong)
	    		        
	    		        // make a copy
	    			    int candidate[9][9];
	    			    for(m=0; m<9; m++ ) 
	    			        for(l=0; l<9; l++ )
	    			            candidate[m][l] = sudoku[m][l];
	    			            
	    			    // fill in trial value
	    			    candidate[i][j] = n;
	    			    
	    			    // recurse
	    			    level++;
	    			    backtrack(candidate);
	    			    level--;
	    		    }
	    		    else {
	    		        if( debug ) printf( "couldn't put %i in cell (%i,%i)\n", n, i+1, j+1 );
	    		    }
	    	    }
	    	    
	    	    if( debug ) printf( "this was a dead end! level: %i cell: (%i,%i)\n", level, i+1, j+1 );
	    	    
	    	    // none of the digits are allowed in this cell, so further iteration
	    	    // is waste of time
	    	    return;
	        }
	    }
    }
    
    // all fields are filled in, print solution
    printf( "\n\nSolution found:\n" );
    for(i=0; i<9; i++ ) {
        printf( "     " );
        for(j=0; j<9; j++ ) {
            printf( "%3i", sudoku[i][j] );
        }
        printf( "\n" );
    }
}[/PHP]

You can do something similar to your version, to see how the solution evolves and how the recursive calls go deeper and deeper and then pops back when a dead end is found (in your case it also pops "return 1" all the way up, when a solution is found).

---

### Post by geo909 on 2009-02-07
Thanks so much, that is helpful!
I'll try that soon to get a better idea.

Thanks for your time, I had fun too and
learned a thing or two!

---

### Post by geo909 on 2009-02-08
I upload the final(?) version of the sudoku solver.
To compile, enter the folder and run
```
make
```

Then run with 
```

./sudoku sudoku.txt
```

GTe.txt, GTm.txt, GTh.txt are sample input files.

Valid format for input files is:
a text file with 9 lines, each line is a number from
0 to 9 (no spaces). 0 represents an empty box.
[COLOR="Red"][B]
EDIT: Uploaded archive misses files, the corrext archive is the attachment is in the next post:[/B][/COLOR]

---

### Post by geo909 on 2009-02-08
**[COLOR="DarkRed"]The previous attachment has a missing file, this is the valid one:[/COLOR]**

---

