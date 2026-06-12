---
title: "[C] Wanna get out of recursion!"
date: 2009-02-20
forum: Programming Talk
---

### Post by hanniph on 2009-02-20
Hey,
  I wrote simple sudoku solver that uses recursive bactracking to find a solution. It works well with one sudoku: goes deeper and deeper into recursion until it finds a solution, prints it and then uses exit() function to terminate the program. However, now I realised that it would be cool to solve a set of sudokus instead of one, but in order to do that i need to somehow get back from that 'deep level of recursions' to main() function that originally calls the recursion.
So is there a quick & neat way to rollback to main()?

---

### Post by SledgeHammer_999 on 2009-02-20
If you don't post an example code I don't think anyone will be able to help you.
If I understand you correctly you can try this:
1. Put the "recursive bactracking" mechanism in a separate function
2. make a **for** loop in your main which loops the same number as your sudokus
3. in that **for** loop call the function described in step 1

EDIT: you can also end early any loop you use by using the "break" keyword.

---

### Post by hanniph on 2009-02-20
Ok, here's my code:
[PHP]
// With every call function scans all the fields until it finds 0
// If it doesn't find any 0's , it means we have a solution and can 
// get out of 81'th recursion (well, number depends on initial data of course) call it will be
// before finding a solution (which is what I want to do)
// Ok, if function finds a number that 'fits', it writes it and then 
//calls itself and search goes further
//if it doesn't find a valid number - it means we put a wrong number. 
// Function clears previously written number and 'backtracks' for other
// options
int solve(char (*X)[SIZE], int row, int col){
    int i, j, z;

    for (i = 0; i < SIZE; i++){
        for (j = 0; j < SIZE; j++){
            if(X[i][j] == 0){
                for (z = 1; z < 10; z++)
                    if (fits_board(X, i, j, z)){  //checking whether given number can be written to X[i][j]
                        X[i][j] = z;
                        solve(X, i, j);
                    }
                X[row][col] = 0;
                return X[row][col];
            }
        }
    }
    print_solution(X);
    exit(0);
}
int main(){
char A[SIZE][SIZE];

    read_data(A);     
    solve(A, 0, 0);
    printf("Solution not found!\n");
    return 0;
}

[/PHP]

---

### Post by SledgeHammer_999 on 2009-02-20
Well assuming that solve() solves the entire sudoku(diddn't read the whole code) applying my logic, your main should look like this:
[php]
int main(){
char A[SIZE][SIZE];
int number_of_sudoku, i;


    read_data(A);     
    for (i = 0; i < number_of_sudoku; i++)
       { 
         solve(A, 0, 0);
         //sudoku solved. do something here with result(like storing it or printing() it) before proceeding to solve the next sudoku
         printf("Solution not found!\n");
       }    
    return 0;
} [/php]

---

### Post by hanniph on 2009-02-20
err.. 
   I changed exit(0) to return statement and since there are no 0's left function rollbacks to where it was called. Really easy. :lolflag:
Thanks for the tips

---

### Post by monkeyking on 2009-02-21
just use goto like a real man

---

### Post by konqueror7 on 2009-02-21
or just create another function instead to replace main(), this way you don't need to call main(), just recursive functions...

---

### Post by nvteighen on 2009-02-21
> **hanniph said:**
> err.. 
   I changed exit(0) to return statement and since there are no 0's left function rollbacks to where it was called. Really easy. :lolflag:
Thanks for the tips

Forget exit(). It's very rare the situation in which you need it or most possibly, a bad design.

---

### Post by mike_g on 2009-02-21
It looks as if you have tired to create an iterative way of solving the problem, then added recursion on top of it. 

The current way you are iterating wont run through all permutations. What is i and j doing when passed to the solve function? It looks like a bit of a mess should probably be split into two functions. the first function calls the function for each cell for each character. The called function would then be the recursive one. 

For the recursive function, implementing the [minimax algorithm](http://en.wikipedia.org/wiki/Minimax) should find an answer for you. Its not going to be the most efficient method, but its fairly simple. 

Also, what is the purpose of your fits board function? z will always be a number 1-9 at x/y coo-oords 1-9. 

For returning to main you could have a solved variable (pointer) when you find an answer set it and return. Each other instance of the function would then check this var and if its set return immediately. Good luck with it.

---

### Post by hanniph on 2009-02-21
>  What is i and j doing when passed to the solve function? 

It's an information about the position filled with a number by a previous function call. 
Those i and j are passed because i'm not sure if I entered correct number.(it may be other possible values).  If further function call cannot find numbers that can bet put into next empty position, it means I have made a wrong guess and have to erase previously filled position (A[i][j] = 0)

> Also, what is the purpose of your fits board function?
It checks whether the given number can be written to a given position.  
It searches same line/column/block for itself and if it founds, then this number is not a valid choice.

And yeah, that code is messy :smile:

---

### Post by Wybiral on 2009-02-21
If C had proper first-class continuations, you could magically transport the 'return' value and the program flow anywhere you want without having to ride the call stack back down :)

---

### Post by issih on 2009-02-21
The logic is fine, your solution to exit the recursion is fine...Its not entirely what I'd call readable code though.

The fact that in every recursion you have the system step over every position on the board is a bit odd rather than only passing down an array containing the remaining empty positions. This means that the whole board is scanned for a blank position at every level, rather than just taking the next empty slot from the list, also the final exit is when the solve function iterates over the whole board and fails to find an empty hole rather than when the number of blanks to fill is zero. Its all perfectly valid, and it will work, its just a bit painful on the eyes, imho anyway.

Oh and having done this myself, I can tell you that implementing a few bits of actual logic into your solution rather than brute forcing it produces some dramatic speed ups.

---

