---
title: "C++ Tic-Tac-Toe Console Problem"
date: 2011-08-12
forum: Programming Talk
---

### Post by philpot345 on 2011-08-12
Hello all, trying to practice C++ a bit, but ran into a problem. Trying to make a simple console version of Tic-Tac-Toe, but after I enter the input, or the spot to replace on the board with the player's mark, the program usually freezes. I am at a loss for where this problem is coming from, originally I had the variables for the rows setup as an array and had a couple extra bool values, but dropped everything down to the most basic parts just to try and find out why this game keeps locking up or entering into an endless loop. Any hints that can be given about which part of the program is actually locking up, (I know it runs down to the point of after the console output of the variable you entered in.), and any places to check around to find info how to fix this would be greatly appreciated. Alas, just fixing the code will do nothing for me, just need an explanation of where all I am screwing up here if possible. Thanks! ;)

```

#include <iostream>
using namespace std;
int tic_tac_toe_game();
int main()
{
    char answer;
    cout << endl << endl << "Welcome to Tic-Tac-Toe!" << endl << endl;
    tic_tac_toe_game();
}

int tic_tac_toe_game()
{
    bool game_end, valid_move;
    char char_move;
        char board_spot_zero = '1';
        char board_spot_one = '2';
        char board_spot_two = '3';
        char board_spot_three = '4';
        char board_spot_four = '5';
        char board_spot_five = '6';
        char board_spot_six = '7';
        char board_spot_seven = '8';
        char board_spot_eight = '9';
        char answer;
    char player_mark;
    int char_turn = 0;
    game_end = false;
    while (game_end != true)
    {
        cout << endl << "--------------------------------------------------" << endl;
        cout << "|\t" << board_spot_zero << "\t+\t" << board_spot_one << "\t+\t" << board_spot_two << "\t|" << endl;
        cout << "|\t" << board_spot_three << "\t+\t" << board_spot_four << "\t+\t" << board_spot_five << "\t|" << endl;
        cout << "|\t" << board_spot_six << "\t+\t" << board_spot_seven << "\t+\t" << board_spot_eight << "\t|" << endl;
        cout << "--------------------------------------------------" << endl;
        cout << endl << "Please select your move:\t";
        cin >> char_move;
        cout << endl << endl << "You have enetered:\t" << char_move << endl << endl;
        if (char_turn == 0){player_mark = 'X';}
        else {player_mark = 'O';}
        valid_move = false;
        while (valid_move != true)
        {
            if (char_move == '1' && board_spot_zero == '1'){board_spot_zero == player_mark;valid_move = true;}
                        else if (char_move == '2' && board_spot_one == '2'){board_spot_one == player_mark;valid_move = true;}
                        else if (char_move == '3' && board_spot_two == '3'){board_spot_two == player_mark;valid_move = true;}
                        else if (char_move == '4' && board_spot_three == '4'){board_spot_three == player_mark;valid_move = true;}
                        else if (char_move == '5' && board_spot_four == '5'){board_spot_four == player_mark;valid_move = true;}
                        else if (char_move == '6' && board_spot_five == '6'){board_spot_five == player_mark;valid_move = true;}
                        else if (char_move == '7' && board_spot_six == '7'){board_spot_six == player_mark; valid_move = true;}
                        else if (char_move == '8' && board_spot_seven == '8'){board_spot_seven == player_mark;valid_move = true;}
            else if (char_move == '9' && board_spot_eight == '9'){board_spot_eight == player_mark;valid_move = true;}
            else {cout << endl << "That is an invalid move!" << endl;}
        }
        if (char_turn == 0){char_turn = 1;}
        else {char_turn == 0;}
                if (board_spot_zero == board_spot_one && board_spot_zero == board_spot_two){game_end = true;}
                if (board_spot_zero == board_spot_three && board_spot_zero == board_spot_six){game_end = true;}
                if (board_spot_eight == board_spot_two && board_spot_eight == board_spot_five){game_end = true;}
        if (board_spot_eight == board_spot_six && board_spot_eight == board_spot_seven){game_end = true;}
                if (board_spot_zero == board_spot_four && board_spot_zero == board_spot_eight){game_end = true;}
                if (board_spot_two == board_spot_four && board_spot_two == board_spot_six){game_end = true;}
                if (board_spot_one == board_spot_four && board_spot_one == board_spot_seven){game_end = true;}
                if (board_spot_three == board_spot_four && board_spot_three == board_spot_five){game_end = true;}
    }
}

```

---

### Post by dwhitney67 on 2011-08-12
Use double-equals, or ==, for comparisons.

Use single-equals, or =, for assignment.

Check out lines 43-55 AFTER you recompile your program using the -Wall compiler option.

Also, consider using an array, or 3x3 matrix (2-d array), to represent your TTT board.  This may help to reduce the redundancy in your code.

P.S.  Code is much more readable when there are newlines between statements.  Slapping multiple statements on the same line is "crap".

---

### Post by GeneralZod on 2011-08-12
Also: have you actually tested what happens when an invalid move is entered? ;)

---

### Post by philpot345 on 2011-08-12
Thank you both. Looking at this during the mid p.m. hours instead of the early a.m. hours really gives a whole new perspective of what I was doing. Looking back at it during this time of day, I see where the problems were with the loops and the conditionals. Next time I'll just sleep on it for a night or two. I'll post the finished solution after I clean it up a bit, finish the conditional statements and close this thread so that if anyone else runs across this problem they can see the solution. Again greatly appreciate the quick response dwhitney as always and also appreciate the hint GeneralZod. :D

---

