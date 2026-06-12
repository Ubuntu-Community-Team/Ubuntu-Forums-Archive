---
title: "How is this modulus working correctly?"
date: 2011-09-03
forum: Programming Talk
---

### Post by isaacj87 on 2011-09-03
Hello,

I've written a small tic-tac-toe program derived from examples on the web. I felt I had a good handle on the difference between real and integer division and the modulus operator. However, there is something that confuses me.

```
/*
Simple tic-tac-toe game by me derived 
from examples I've found on the web.
*/


#include <stdio.h>
#include <stdlib.h>

char win_by_diagonals;
char win_by_rows_columns;
char board[3][3] = {
											{'1','2','3'},
											{'4','5','6'},
											{'7','8','9'}
									 };

void display_board(void);
char check_board(void);
void get_player_move(void);
void get_computer_move(void);

void main(void)
{
	int i = 0;
	int player = 0;
	int winner = 0;
	char check_if_done;

	printf("\n\n");
	printf("Welcome to a simple game of tic-tac-toe.\n");
	printf("Choose carefully or suffer an embarrassing loss to a stupid computer.\n");

  do {
    display_board();
    get_player_move();
    check_if_done = check_board(); /* check if human player is winner */
    if(check_if_done == win_by_diagonals || win_by_rows_columns) break; /* winner!*/
    //get_computer_move();
    //done = check(); /* check if computer is winner */
  } while(check_if_done != win_by_diagonals || win_by_rows_columns);

	if(check_if_done == win_by_diagonals || win_by_rows_columns && board == 'X') printf("\nYou won!!!\n");
  else printf("I won!!!!\n");
  display_board(); /* show final positions */

}

void get_player_move(void)
{
	int choice = 0;
	int row = 0;
	int column = 0;
	
	do {
  	printf("Please enter a number where you want to place your choice: ");
  	scanf("%d", &choice);

		[B]row = --choice/3;
		column = choice%3;[/B]

	} while(choice<0 || choice>9 || board[row][column]>'9');
  board[row][column] = 'X';
}

/* This needs to be finished 

void get_computer_move(void)
{

	int row = 0;
	int column = 0;

	char player = 'X';

  for(row=0; i<3; i++){
    for(column=0; j<3; j++)
      if(board[row][column]== player) break;
    if(board[row][column]== player) break;
  }

  if(i*j==9)  {
    printf("draw\n");
    exit(0);
  }
  else
    board[row][column] = 'O';
}
*/

void display_board(void)
{
	printf("\n\n");
	printf(" %c | %c | %c\n", board[0][0],board[0][1],board[0][2]);
	printf(" --+---+--\n");
	printf(" %c | %c | %c\n", board[1][0],board[1][1],board[1][2]);
	printf(" --+---+--\n");
	printf(" %c | %c | %c\n", board[2][0],board[2][1],board[2][2]);
	printf("\n\n");
}

char check_board(void)
{
  int i;
	int line = 0;

  if((board[0][0] == board[1][1] && board[0][0] == board[2][2]) ||
    (board[0][2] == board[1][1] && board[0][2] == board[2][0])) {
      	return win_by_diagonals;
	} else 
		for(line = 0; line <= 2; line ++)
    	if((board[line][0] == board[line][1] && board[line][0] == board[line][2])||
      	(board[0][line] == board[1][line] && board[0][line] == board[2][line])) {
      		return win_by_rows_columns;
			}
}

```

I've bolded the section that puzzles me. Technically, say if I were to choose 4, 4%3 would result in 1 (technically column 2 or board[1][1]). However, it shows up in the actual program at board[1][0]. Can someone explain to me as to why it does?

EDIT: BTW, the code present is actually working correctly, I was just curious as to why.

---

### Post by Bachstelze on 2011-09-03
[http://cplus.about.com/od/glossar1/g/predecdefn.htm](http://cplus.about.com/od/glossar1/g/predecdefn.htm)

row = --choice/3;

is equivalent to

choice = choice - 1;
row = choice/3;

---

### Post by isaacj87 on 2011-09-03
> **Bachstelze said:**
> [http://cplus.about.com/od/glossar1/g/predecdefn.htm](http://cplus.about.com/od/glossar1/g/predecdefn.htm)

row = --choice/3;

is equivalent to

choice = choice - 1;
row = choice/3;

Thanks for the reply. I'm aware of the decrement, but I was talking about column.

```
column = choice%3
```

---

### Post by Bachstelze on 2011-09-03
Same thing, choice keeps its decremented value, so choice is 3 here.

---

### Post by isaacj87 on 2011-09-03
> **Bachstelze said:**
> Same thing, choice keeps its decremented value, so choice is 3 here.

Ahhh, I see what you're saying. Thanks that makes sense now.

---

