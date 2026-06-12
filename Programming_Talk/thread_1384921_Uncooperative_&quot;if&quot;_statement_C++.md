---
title: "Uncooperative &quot;if&quot; statement C++"
date: 2010-01-19
forum: Programming Talk
---

### Post by Eragon0605 on 2010-01-19
I put the following code into my program:
[PHP]if (board[0] == 'X')
    bob = 1;
if (board[0] == 'O')
    bob = 1;[/PHP]The program compiles fine, no errors or warnings, but when I run the program, integer bob is ALWAYS assigned the number 1, weather or not the first item in vector bob is X or O or not. I also tried:
[PHP]if ((board[0] == 'X') || (board[0] == 'O'))
    bob = 1;[/PHP]I did it both with and without parentheses, but all removing the parentheses did was generate a compiler warning. As I stated in my title, this is C++.

---

### Post by raydeen on 2010-01-19
Well, in both cases, bob equals 1. I'm assuming that board[0] can only be an 'X' or an 'O'. Is this a Tic-Tac-Toe game? I would think that instead of two if statements, you'd have an if and an else (or elif - not sure of the syntax) and that bob would equal 0 or 1 depending on the whether board[0] = X or O. And shouldn't there be some {} braces for the if sub blocks? Been a while since I did any C++.

---

### Post by Hellkeepa on 2010-01-19
HELLo!

What is the default value of any given cell?

Happy codin'!

---

### Post by samjh on 2010-01-19
> **Eragon0605 said:**
> I put the following code into my program:
[PHP]if (board[0] == 'X')
    bob = 1;
if (board[0] == 'O')
    bob = 1;[/PHP]The program compiles fine, no errors or warnings, but when I run the program, integer bob is ALWAYS assigned the number 1, weather or not the first item in vector bob is X or O or not.

Without a context, it's hard to tell what the problem is.

Using only the information you've provided, I can think of a few possible problems.  Check your code for these:
[list][*]What do you assign bob if board[0] is neither X nor O?  When board[0] is neither X nor O, you should assign a value other than 1 for bob.  If you don't do it, then once board[0] is X or O, bob will always be 1, whether or not board[0] is X or O or otherwise.
[*]Check that the default (initial) value for bob is not 1.  It shouldn't be 1 or any other value you assign to it in the logic portion of your program.[/list]

Could you provide some context for your code?  Like, what is it used for?

---

### Post by Eragon0605 on 2010-01-19
To samjh: If it is neither X or O, the value could be any number from 0-10. The default value of bob is zero.

To radeen: No this is not a tic-tac-toe game, it is something totally unrelated. I made the coding part of it look a little like a tic-tac-toe game just for fun. I previously assigned bob the value zero. If board[0] equals X or O, the value becomes 1. Otherwise, it's supposed to stay as a zero. The curly brackets are not required if you are executing a single command. For example, this:[PHP]if (var1 = 0)
    var2 = 1;
    var3 = 1;[/PHP]would make var2 equal 1 only if var1 equals zero. The program would then proceed to assign the number one to var3, weather or not var1 equals zero or not. I if I wanted var2 and var3 to be assigned the value 1 only if var1 = 0, I would need to write:[PHP]if (var1 = 0)
{
    var2 = 1;
    var3 = 1;
}[/PHP]EDIT: Oh, and this is part of a function to assign X or O to board[0] only if board[0] isn't already X or O. Like I said, I made the program look a bit like a tic-tac-toe game, from the programmer's point of view, just for fun. I could have an if and else statement with bob = X or O (I did that in the second code snippet in my first post, except the else statement), but I get the same thing.

---

### Post by MadCow108 on 2010-01-19
I guess most here are aware when they need brackets... (besides your missing a == in the condition)

without more context nobody can help you, other than saying the code you've given is correct, the problem is elsewhere
best is to give a minimal complete working example reproducing your problem.

---

### Post by Maheriano on 2010-01-19
Make sure it's not a case issue, maybe board[0] == x.

---

### Post by issih on 2010-01-19
One possible error to look out for in if statements is the following.

Correct code:
```

if (a == b)
    c = 1;

```

Incorrect code:
```

if (a == b);
    c = 1;

```

The latter one will always assign c to 1, regardless of the if statement because the ";" on the if line closes the if statement before you ever get to what would be the conditional statement.

If its not that then you will have to post more context as everyone else has suggested..

Hope that helps

---

### Post by Eragon0605 on 2010-01-19
I triple checked my semicolons before starting this topic, and yes there is no semicolon at the end of the if statement. Good suggestion though; it has caused me many hours of frustration in the past :D. It can't be a case issue, I use the toupper() function. And yes, I think it would be beneficial if I gave a little more context, so here is more context!
[PHP]if (yes == 9)
        {
            bob = 0;

            while (bob == 0)
            {
                yes = 0;

                legal(yes, board, bob);

                if (bob == 0)
                    yes++;
            }
        }[/PHP]And here is the legal() function I made:
[PHP]void legal(int choice, const vector<char>& board, int& bob)
{
        if ((board[choice] == 'X') || (board[choice] == 'O'))
        {
            bob = 1;
        }
}[/PHP]For some weird reason, now when I try to compile, the above while loop loops forever, even though an X or an O is put in the board vector before this code executes, and if I put an else statement in the legal() function, the code in the else statement is always executed. It's almost like it doesn't see the X or O.

---

### Post by MadCow108 on 2010-01-19
if board[0] is not O or X it will loop forever because the index is reset to 0 in every iteration

this still does not really help.
how and where is the vector filled?

---

### Post by Maheriano on 2010-01-19
Ya, it should loop forever. You have it set to loop while Bob is equal to 0 but it will never get set to 1 with that code. You're passing in a parameter of 0 for choice and it continuously checks to see if board[0] is equal to X or O. If that's false then it's going to keep checking over and over and over....

EDIT - I just noticed you're incrementing the yes variable. Your actual problem then is what the guy above me said, you're resetting yes to 0 on every loop. Trying putting the yes = 0 setting outside the while loop. That will work. You're going to run into something like an ArrayIndexOutOfBounds exceptions that way though, you need to stop the incrementing when you run out of squares.

---

### Post by Eragon0605 on 2010-01-19
board[0] is defined earlier by what the user types in. Just to make sure that board[0] is indeed an X or an O, I displayed board[0] in the window, and I always get an X or an O. I can't really show you much more of this particular program; some of it is someone else's work, and he refuses to let me show it on here... Anyway, just to make things quick, I copied and pasted and edited snippets of code into a very simple tic-tac-toe program:
[PHP]#include <iostream>
#include <string>
#include <vector>

using namespace std;

void displayboard(const vector<char>& board);
void checkwin(const vector<char>& board, char player, int& win);
void legal(int choice, const vector<char>& board, int& bob);
void compmove(vector<char> board, char comp, char player);

char player, comp;
int compchoice;
int bob = 0;

string choiice;

int main()
{

    vector<char> board;
    board.push_back('0');
    board.push_back('1');
    board.push_back('2');
    board.push_back('3');
    board.push_back('4');
    board.push_back('5');
    board.push_back('6');
    board.push_back('7');
    board.push_back('8');

    cout << "Enter 0-8 corresponding with your choice." << endl;

    cout << "Would you like to be X? ";
    cin >> choiice;

    if (choiice == "Y" || choiice == "YES" || choiice == "y" || choiice == "yes")
    {
        cout << "Okay, you are X.\n" << endl;
        player = 'X';
        comp = 'O';
    }
    else
    {
        cout << "Okay, you are O.\n" << endl;
        player = 'O';
        comp = 'X';
    }

    displayboard(board);

    int choice, blob = 1;


    int win = 0;
    int lose = 0;
    char currentturn;

    while (win != 1 && lose != 1)
    {
        currentturn = player;
        cout << "\nEnter your choice: ";
        cin >> choice;

        legal(choice, board, blob);

        while (blob == 0)
        {
            cout << "INVALID. TRY AGAIN: ";
            cin >> choice;

            legal(choice, board, blob);
        }

        while (choice < 0 || choice > 8)
        {
            cout << "\nEnter 0-8, corresponding with your choice: ";
            cin >> choice;
        }

        board[choice] = player;

        displayboard(board);

        checkwin(board, player, win);

        compmove(board, comp, player);

        board[compchoice] = comp;

        cout << "The computer moves:" << endl;

        displayboard(board);

        checkwin(board, comp, lose);
    }
    if (win == 1)
        cout << "You win!" << endl;
    if (lose == 1)
        cout << "The computer wins." << endl;

    return 0;
}

void displayboard(const vector<char>& board)
{
    cout << "\n\t" << board[0] << " | " << board[1] << " | " << board[2];
    cout << "\n\t" << "---------";
    cout << "\n\t" << board[3] << " | " << board[4] << " | " << board[5];
    cout << "\n\t" << "---------";
    cout << "\n\t" << board[6] << " | " << board[7] << " | " << board[8];
    cout << "\n\n";
}

void checkwin(const vector<char>& board, char player, int& win)
{
        if ((board[0] == player && board[1] == player && board[2] == player) ||
             (board[3] == player && board[4] == player && board[5] == player) ||
             (board[6] == player && board[7] == player && board[8] == player) ||

             (board[0] == player && board[3] == player && board[6] == player) ||
             (board[1] == player && board[4] == player && board[7] == player) ||
             (board[2] == player && board[5] == player && board[8] == player) ||

             (board[0] == player && board[4] == player && board[8] == player) ||
             (board[2] == player && board[4] == player && board[6] == player))
            win = 1;
}

void legal(int choice, const vector<char>& board, int& bob)
{
        if ((board[choice] == 'X') || (board[choice] == 'O'))
        {
            bob = 1;
        }
}

void compmove(vector<char> board, char comp, char player)
{
    int yes = 9;
    int valid = 0;

    while (valid != 1)
    {
        if (yes == 9)
        {
            bob = 0;
            yes = 0;

            while (bob == 0)
            {
                legal(yes, board, bob);

                if (bob == 0)
                    yes++;
                
                if (yes == 9)
                   bob = 1;
            }
        }

        compchoice = yes;

        valid = 1;
    }
}[/PHP]Sorry if there is some stuff in there that doesn't really make sense, this is just a very quickly made program with an extremely dumb AI. The program freezes when it's the AI's turn.

EDIT: Oh, I didn't see Maheriano's post. I have modified the above code according to what he said. Now the looping problem is fixed, but now the legal() statement has my old problem; bob is given the value 1 weather or not board[choice] equals X or O or not.

---

### Post by MadCow108 on 2010-01-20
your code keeps executing the loop in legal with every possible index (and without boundary checks)
until it encounters the O or X
so at the end of the loop bob will always be set to 1

---

### Post by lisati on 2010-01-20
Just a thought after a quick perusal: what happens when yes !=9 and valid != 1 ??????

---

### Post by dwhitney67 on 2010-01-20
Just a thought after a quick perusal: what happens when bad code is written?  The OP sure missed the mark with this app.

Here's some suggestions for the OP:

1.  Skip the query about whether the player wants to be an 'X' or an 'O'.  Just designate him as 'X'.

2.  When appropriate, use the data type 'bool' in lieu of 'int'.

3.  Do not use global variables.  Use your functions to return values.  Avoid declaring passing parameters of basic data types by reference, especially if you have a void return value for the function.
```

bool legal(const int choice, const vector<char>& board)
{
   return !(board[choice] == 'X' || board[choice] == 'O');
}

```

4.  Initialize your variables when they are declared.

There are more issue I could point out, but hopefully the comments above will help you.

P.S.

> 
some of it is someone else's work, and he refuses to let me show it on here

I found this to be hilarious!

---

### Post by Arndt on 2010-01-20
> **dwhitney67 said:**
> Just a thought after a quick perusal: what happens when bad code is written?  The OP sure missed the mark with this app.

Here's some suggestions for the OP:

1.  Skip the query about whether the player wants to be an 'X' or an 'O'.  Just designate him as 'X'.

2.  When appropriate, use the data type 'bool' in lieu of 'int'.

3.  Do not use global variables.  Use your functions to return values.  Avoid declaring passing parameters of basic data types by reference, especially if you have a void return value for the function.
```

bool legal(const int choice, const vector<char>& board)
{
   return !(board[choice] == 'X' || board[choice] == 'O');
}

```

4.  Initialize your variables when they are declared.

There are more issue I could point out, but hopefully the comments above will help you.

P.S.


I found this to be hilarious!

And when all else fails, insert print statements that show you what the values of the relevant variables are. Either you will find a surprising combination of values that obviously has the effect you're observing - then you can one step back and try to determine how they got these values. Or your get an expected set of values with a surprising effect, which can be because you misunderstood something in the language, or hadn't typed what you thought you had typed (that last keeps happening).

---

