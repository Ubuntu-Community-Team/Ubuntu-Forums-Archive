---
title: "Tic-Tac-Toe"
date: 2008-04-20
forum: Programming Talk
---

### Post by Sinkingships7 on 2008-04-20
*sigh*
Alright, here it goes.

Please, PLEASE do not bash on me. I'm a programmer in progress. My work is currently sloppy and I am very aware that it is full of redundancy and the such. Keep in mind that for having JUST started learning C, it's expected to be a bit sloppy.

I'm attempting to make a Tic-Tac-Toe game, entirely for the learning experience. I want to be a programmer, and the only way to reach that goal is to learn from experience. You are free to pick apart my code and tell me everything that's wrong with it, but please don't hate me just because I'm just starting out.

This is my Tic-Tac-Toe game, written in C, which I just learned this morning:
[php]
#include <stdio.h>

/* PROTOTYPES */
int spot_taken(int, int);
int latitude();
int longitude();


char board[3][3];
    
/* MAIN */
int main()
{
    /* wipes board clean --  t represents a free space */
    int x, y;
    for (x = 0; x < 3; x++) {
        for (y = 0; y < 3; y++) {
            board[x][y] = 't';
        }
    }

    int game = 5;
    int taken;
    int a, b;
    while (game == 5) {
        p1: /* start player 1 */
        a = longitude();
        b = latitude();
        taken = spot_taken(a, b);
        if (taken == 0) {
            board[a][b] = 'x';
        }
        else if (taken == 1) {
            printf("That spot's already taken! Try again.\n");
            goto p1;
        }
        p2: /* start player 2 */
        a = longitude();
        b = latitude();
        taken = spot_taken(a, b);
        if (taken == 0) {
            board[a][b] = 'o';
        }
        else if (taken == 1) {
            printf("That spot's already taken! Try again.\n");
            goto p2;
        }
    }
    
    return 0;
}

/* FUNCTIONS */
int spot_taken(int a, int b)    /* returns 0 if spot is available, 1 if it's taken */
{
    return(board[a][b] == 'x' || board[a][b] == 'o');
}

int longitude()    /* returns desired longitude of player 1 */
{
    int lon;
    printf("Enter the longitude you wish to move: ");
    scanf("%d", &lon);
    return(lon);
}

int latitude()     /* returns desired latitude of player 1 */
{
    int lat;
    printf("Enter the latitude you wish to move: ");
    scanf("%d", &lat);
    return(lat);
}

[/php]

Again, I'm new and I really REALLY want to learn. Please help me in any way you can. The errors I get are on the return statement of the spot_taken() function. It states: 
```

error: &#8216;board&#8217; undeclared (first use in this function)
 error: (Each undeclared identifier is reported only once
 error: for each function it appears in.)

```
And my other error is on the line just below it (the finishing brace):
```

warning: control reaches end of non-void function

```

Again, I'M NEW. So very, very new. But I'm trying.

---

### Post by mike_g on 2008-04-20
The problem you have is that spot_taken() does not knwo about 'board'  because its out of its scope. You can fix this by passing board into the function. IE:
```
int spot_taken(char board[][3], int a, int b)   
{
    return(board[a][b] == 'x' || board[a][b] == 'o');
}
```
and:
```
taken = spot_taken(board, a, b);
```

---

### Post by amingv on 2008-04-20
char board[n][n] is out of scope (unreachable) for the function spot_taken(); it is born in the main() function and dies just after the return statement.
At a first glance, the easier solution (with the least change to the code) would be to declare char board[][] outside of the main function, maybe under your prototypes, which, to be honest, I don't fully understand.
You may also modify spot_taken() to take a pointer to board[][] as an argument, but that would be more complex.

Both my solutions are probably not very elegant, but they require the least change to the code. Also, I'm not a C programmer ;).
Good luck.

---

### Post by Sinkingships7 on 2008-04-20
I went ahead and made the declaration of my board global. That seems to work out fine.

Any and all critiques welcomed. I just want to get better.

---

### Post by amingv on 2008-04-20
> **Sinkingships7 said:**
> I went ahead and made the declaration of my board global. That seems to work out fine.

Any and all critiques welcomed. I just want to get better.

Yes, that ought to work.
However (and I repeat myself) I don't feel it is very elegant; it is good to get the code working quickly and (hopefully) understand a little better the concept of the scope.

mike_g is obviously a better programmer than I am, whether your code works now or not, play with the example he gave you, if not now, it will certainly help you to understand it.

Also, I do not see why player 1 and 2 should each have a longitude and latitude function, you could have a lon() and lat() function and use it for either of them (if you needed a function at all).
Anyway, just speaking through my hat...

---

### Post by Sinkingships7 on 2008-04-20
> **amingv said:**
> Yes, that ought to work.
However (and I repeat myself) I don't feel it is very elegant; it is good to get the code working quickly and (hopefully) understand a little better the concept of the scope.

mike_g is obviously a better programmer than I am, whether your code works now or not, play with the example he gave you, if not now, it will certainly help you to understand it.

Also, I do not see why player 1 and 2 should each have a longitude and latitude function, you could have a lon() and lat() function and use it for either of them (if you needed a function at all).
Anyway, just speaking through my hat...

How very right you are...

EDIT: updated the original post with new code...
You should also all know that this program isn't close to complete. This is just the start.

---

### Post by mssever on 2008-04-20
Many programmers believe that the goto statement is evil. At any rate, it's unnecessary. In your case, you're using labels and gotos as while loops. Better to actually write them as while loops to improve your code's readability.

---

### Post by amingv on 2008-04-20
> **mssever said:**
> Many programmers believe that the goto statement is evil. At any rate, it's unnecessary. In your case, you're using labels and gotos as while loops. Better to actually write them as while loops to improve your code's readability.

[SIZE="7"]+1[/SIZE]
True, true, true, and I completely skipped it before. I suggest you change it ASAP, it is frowned upon by anyone who will see them, at all costs do not use it! You'll thank yourself countless times later for learning not to use spaghetti code ([http://en.wikipedia.org/wiki/Spaghetti_code](http://en.wikipedia.org/wiki/Spaghetti_code)) from an early stage.
Besides, you don't want this to happen to you:

[IMG]http://imgs.xkcd.com/comics/goto.png[/IMG]

---

### Post by moc on 2008-04-20
> **Sinkingships7 said:**
> *sigh*
Alright, here it goes.

Please, PLEASE do not bash on me. I'm a programmer in progress. My work is currently sloppy and I am very aware that it is full of redundancy and the such. Keep in mind that for having JUST started learning C, it's expected to be a bit sloppy.

I'm attempting to make a Tic-Tac-Toe game, entirely for the learning experience. I want to be a programmer, and the only way to reach that goal is to learn from experience. You are free to pick apart my code and tell me everything that's wrong with it, but please don't hate me just because I'm just starting out.

This is my Tic-Tac-Toe game, written in C, which I just learned this morning:
[php]
#include <stdio.h>

/* PROTOTYPES */
int spot_taken(int, int);
int latitude();
int longitude();


char board[3][3];
    
/* MAIN */
int main()
{
    /* wipes board clean --  t represents a free space */
    int x, y;
    for (x = 0; x < 3; x++) {
        for (y = 0; y < 3; y++) {
            board[x][y] = 't';
        }
    }

    int game = 5;
    int taken;
    int a, b;
    while (game == 5) {
        p1: /* start player 1 */
        a = longitude();
        b = latitude();
        taken = spot_taken(a, b);
        if (taken == 0) {
            board[a][b] = 'x';
        }
        else if (taken == 1) {
            printf("That spot's already taken! Try again.\n");
            goto p1;
        }
        p2: /* start player 2 */
        a = longitude();
        b = latitude();
        taken = spot_taken(a, b);
        if (taken == 0) {
            board[a][b] = 'o';
        }
        else if (taken == 1) {
            printf("That spot's already taken! Try again.\n");
            goto p2;
        }
    }
    
    return 0;
}

/* FUNCTIONS */
int spot_taken(int a, int b)    /* returns 0 if spot is available, 1 if it's taken */
{
    return(board[a][b] == 'x' || board[a][b] == 'o');
}

int longitude()    /* returns desired longitude of player 1 */
{
    int lon;
    printf("Enter the longitude you wish to move: ");
    scanf("%d", &lon);
    return(lon);
}

int latitude()     /* returns desired latitude of player 1 */
{
    int lat;
    printf("Enter the latitude you wish to move: ");
    scanf("%d", &lat);
    return(lat);
}

[/php]

Again, I'm new and I really REALLY want to learn. Please help me in any way you can. The errors I get are on the return statement of the spot_taken() function. It states: 
```

error: ‘board’ undeclared (first use in this function)
 error: (Each undeclared identifier is reported only once
 error: for each function it appears in.)

```
And my other error is on the line just below it (the finishing brace):
```

warning: control reaches end of non-void function

```

Again, I'M NEW. So very, very new. But I'm trying.

Hi,

I just had a quick glance at your program. Here's my immediate comments

1) Avoid global variables
In general... you shall not use global variables like you have done  with board. pass it by reference as previously suggested. If you choose to keep it global, make sure it's only changed by one function.
But face it... sooner or later you'll have to use pointers. so learn how to deal with them.
This program is a good example why C++ is preferred. Here you would encapsulate your board in a class and only access the board via member class functions.  


2)Never use goto.
It makes your code unreadable, 
If an experieced C programmer sees a goto, he's in no doubt that he is dealing with a novice.
You'll probably realise this when your program starts to grow. Suddenly you don't understand it yourself. Make dedicated functions to your players.

3)keep main() simple
Be careful not to put to much complexity into your main function.
Main shall only handle the very top level control.
Have dedicated functions for cleaning board, updating board and handling players. 

4) use defines .
example:
#define CROSS    'x'
#define BUBBLE  'o'
#define EMPTY     't'
#define LONGITUDE  3
#define LATITUDE      3

Then you declare your board like this
char board[LONGITUDE][LATITUDE];

Do this for all the values you use again and again. When you later find out that EMPTY should be 'T' or LATITUDE should be 4, you just need to update the defines. 

5) validate you input
If a  player enters 4 or something not in the 0-3 range, your program will crash because it tries to access the board array outside it's boundaries, Never assume a disciplined user. with the defines above:

if(lon>LONGITUDE || lon<0)
    /* Do error handling*/



regards
/moc

---

### Post by Sinkingships7 on 2008-04-21
I know about pointers, and I know how to use them. I just don't understand why or where I should use them.

C++ could be considered my first language: I know how to encapsulate it in classes (kinda), but I wanted to learn C so I did this as a practice to implement my new knowledge of it.

I planned on fixing the goto's, and am very aware that it's bad practice. I can't honestly tell you why I did that... the whole thing was a pretty quick hack. I'll fix it for sure. It was just easier and i didn't want to lose my train of thought lol.

I'm going to attempt to clean up main() some more and divide this into more (less?) functions. I didn't even think of #define... good idea.

Lazy of me, I know, but I was going to deal with exception handling after I coded a solid foundation. *facepalm*

Thank you  very much for the Advice, moc.


I'm going to recode this and post back sometime tomorrow after school.

Anyone else have advice, please share!

---

### Post by era86 on 2008-04-21
I use global variables all the time in C.  Especially when doing systems programming.  Don't think that it is a horrible thing to do.

Goto, however, is a bad practice.  Especially when 'goto'ing back in your code.  Just do away with it.

---

### Post by scourge on 2008-04-21
> I know about pointers, and I know how to use them. I just don't understand why or where I should use them.

Then you don't really know pointers. A C programmer can't really live without them.


> I use global variables all the time in C. Especially when doing systems programming. Don't think that it is a horrible thing to do.

Agreed. But it's usually best to keep their number at a minimum. I use global variables mainly for lookup tables, hash tables, etc. Not much else.

---

### Post by Sinkingships7 on 2008-04-21
> **scourge said:**
> Then you don't really know pointers. A C programmer can't really live without them.

Then where do you propose I use them?

---

### Post by sq377 on 2008-04-21
To return alloc'd memory from a function
Alot of  libraries will return an alloc'd structure (See GTK)
If you need to dynamically create anything, you need to use malloc, which cannot be successfully used without pointers.

I honestly cannot see how you can code much without them.

---

### Post by Sinkingships7 on 2008-05-09
Alright. I'm back, along with my new code.

I dropped this project for a while (can't remember why) and I just came back to it today. In the mean time, I'd been continuing my studies on programming a bit.

Anyhow, I decided to recode the program from scratch. As you'll be able to see, things are a bit more organized than last time.

I am however, having a problem. After the user inputs a column and row, if the next player enters the same column and row, then the program should tell them that that spot is already taken. It doesn't. Not too sure what's wrong with it... could someone help me out, please?

Also, it should be obvious that this is, again, no where near complete. You can see some places commented out where I obviously plan to implement ideas later.
[PHP]
#include <stdio.h>

void first_run_display();
void new_board();
void player_1();
void player_2();
int get_col();
int get_row();
int check_taken();
void set_token(char, int, int);

char board[3][3];

int main()
{
	first_run_display();
	new_board();
	//do {
		here:
		printf("Player 1\n\n");
		player_1();
		//display_board();
		printf("Player 2\n\n");
		player_2();
		goto here;
		//display_board();
	//}while(win == TRUE || draw == TRUE || lose == TRUE);

	return 0;
}


void new_board()
{
	int x, y;
    for (x = 0; x < 3; x++) {
        for (y = 0; y < 3; y++) {
            board[x][y] = ' ';
        }
    }
}

void player_1()
{
	char token = 'x';
	int is_taken;
	int col, row;

	col = get_col();
	row = get_row();
	is_taken = check_taken();
	if (is_taken == 1) {
		printf("That spot is already taken! Try again!\n");
	}
	if (is_taken == 0) {
		set_token(token, col, row);
	}
}


void player_2()
{
	char token = 'o';
	int is_taken;
	int col, row;

	col = get_col();
	row = get_row();
	is_taken = check_taken();
	if (is_taken == 1) {
		printf("That spot is already taken! Try again!\n");
	}
	if (is_taken == 0) {
		set_token(token, col, row);
	}
}


int get_col()
{
	int number;
	printf("What column do you want to place your token in? ");
	scanf("%i", &number);

	return(number);
}


int get_row()
{
	int number;
	printf("What row do you want to place your token in? ");
	scanf("%i", &number);

	return(number);
}


int check_taken()
{
	int x, y;
	int to_return;
    for (x = 0; x < 3; x++) {
        for (y = 0; y < 3; y++) {
            if (board[x][y] == ' ') {
            	to_return = 0;
            }
            else {
            	to_return = 1;
			}
        }
    }
    return(to_return);
}


void set_token(char token, int col, int row)
{
	int x, y;
    for (x = 0; x < 3; x++) {
        for (y = 0; y < 3; y++) {
            if (x == row && y == col) {
            	board[x][y] = token;
			}
        }
    }
}


void first_run_display()
{
    printf("Welcome to Tic-Tac-Toe!\n");
    printf("To play, simply enter your desired column and row for each move.\n");
    printf("You can imagine the board as follows:\n");
    printf("\t     0   1   2 \n");
    printf("\t  0    |   |   \n");
    printf("\t    -----------\n");
    printf("\t  1    |   |   \n");
    printf("\t    -----------\n");
    printf("\t  2    |   |   \n");
    printf("-------------------------------------------------------------------\n\n");
}
[/PHP]

---

### Post by Sinkingships7 on 2008-05-10
I'm thinking that the problem is in the set_token() function or the check_taken() function.

Does anyone have any input?

---

### Post by Bichromat on 2008-05-10
Your check_taken() function should be something like this :
```

int check_taken(int row, int col){
   return(board[row][col]!=' ');
}

```

In your current version you always return the state of the last cell of your board...

Edit : and set_token should just be :
```

void set_token(char token, int col, int row) 
{ 
  board[row][col] = token;
}

```
No need for a loop.

---

### Post by Sinkingships7 on 2008-05-10
The check_taken() function you offered gives me a segmentation fault every time I run the program and enter player 1's desired coordinates.

EDIT: Nevermind. My mistake. I forgot to offer the arguments for every time I called that function. Your idea works, thank you!

---

### Post by Sinkingships7 on 2008-05-10
Okay. So, after some help from Bichromat, I was able to fix the problem where it wouldn't tell me if a spot was already taken. After that, I made the display_board() function. This works out great. My Tic-Tac-Toe game is nearly complete.

Next, I will design and implement a function to check for a win, draw, or loss, so I can finally get rid of my nasty goto statement and encase the playing functions into a loop.

After that comes code-cleanup, where I'll basically just organize my code and make things easier to read.

Thank you to everyone who's helped me thus-far.

I'll come back if I have any issues, though I'm pretty sure I know what I'm going to do.

:popcorn:

EDIT: This is my code up to this point. Once again, thank you to everyone who helped me get this far.

[PHP]
#include <stdio.h>

/* FUNCTION DECLARATIONS */
void first_run_display();
void new_board();
void display_board();
void player_1();
void player_2();
int get_col();
int get_row();
int check_taken(int, int);
void set_token(char, int, int);

/* GLOBAL VARIABLES */
char board[3][3];

/* MAIN */
int main()
{
	first_run_display();
	new_board();

	here:

	player_1();
	display_board();

	player_2();
	display_board();

	goto here;

	return 0;
}

/* FUNCTIONS */

void first_run_display()
{
    printf("Welcome to Tic-Tac-Toe!\n");
    printf("To play, simply enter your desired column and row for each move.\n");
    printf("You can imagine the board as follows:\n");
    printf("\t     0   1   2 \n");
    printf("\t  0    |   |   \n");
    printf("\t    -----------\n");
    printf("\t  1    |   |   \n");
    printf("\t    -----------\n");
    printf("\t  2    |   |   \n");
    printf("\nPLAYER 1 = X\nPLAYER 2 = O\n");
    printf("-------------------------------------------------------------------\n\n");
}


void new_board()
{
	int x, y;
    for (x = 0; x < 3; x++) {
        for (y = 0; y < 3; y++) {
            board[x][y] = ' ';
        }
    }
}

void display_board()
{
	int x, y;
	printf("\n");
	for (x = 0; x < 3; x++) {
		for (y = 0; y < 3; y++) {
			if (y == 0)
				printf(" ");
			printf("%c", board[x][y]);
			if (y != 2)
				printf(" | ");
		}
		if (x != 2)
			printf("\n-----------\n");
	}
	printf("\n\n");
}


void player_1()
{
	printf("Player 1\n\n");
	char token = 'x';
	int is_taken;
	int col, row;

	col = get_col();
	row = get_row();
	is_taken = check_taken(row, col);
	if (is_taken == 1) {
		printf("That spot is already taken! Try again!\n");
	}
	if (is_taken == 0) {
		set_token(token, col, row);
	}
}


void player_2()
{
	printf("Player 2\n\n");
	char token = 'o';
	int is_taken;
	int col, row;

	col = get_col();
	row = get_row();
	is_taken = check_taken(row, col);
	if (is_taken == 1) {
		printf("That spot is already taken! Try again!\n");
	}
	if (is_taken == 0) {
		set_token(token, col, row);
	}
}


int get_col()
{
	int number;
	printf("What column do you want to place your token in? ");
	scanf("%i", &number);

	return(number);
}


int get_row()
{
	int number;
	printf("What row do you want to place your token in? ");
	scanf("%i", &number);

	return(number);
}


int check_taken(int row, int col)
{
   return(board[row][col]!=' ');
}


void set_token(char token, int col, int row)
{
  board[row][col] = token;
}
[/PHP]

---

### Post by Sinkingships7 on 2008-10-07
Wow. I finished this quite a few months back, but I never posted my finished code.

It contains no error checking and could use a lot more comments, but it is what it is: a beginners exercise. 

For those who care to see the end result (for now), here it is:

```
[color=#BC7A00]#include <stdio.h>
[/color]
[color=#408080]*/* FUNCTION DECLARATIONS */*[/color]
[color=#B00040]void[/color] first_run_display();
[color=#B00040]void[/color] new_board();
[color=#B00040]void[/color] display_board();
[color=#B00040]int[/color] player_1();
[color=#B00040]int[/color] player_2();
[color=#B00040]int[/color] get_col();
[color=#B00040]int[/color] get_row();
[color=#B00040]int[/color] check_taken([color=#B00040]int[/color], [color=#B00040]int[/color]);
[color=#B00040]void[/color] set_token([color=#B00040]char[/color], [color=#B00040]int[/color], [color=#B00040]int[/color]);
[color=#B00040]int[/color] determine_end([color=#B00040]char[/color]);

[color=#408080]*/* GLOBAL VARIABLES */*[/color]
[color=#B00040]char[/color] board[[color=#666666]3[/color]][[color=#666666]3[/color]];

[color=#408080]*/* MAIN */*[/color]
[color=#B00040]int[/color] [color=#0000FF]main[/color]()
{
	first_run_display();
	new_board();
	[color=#B00040]int[/color] end;

	[color=#008000]**do**[/color] {
		end [color=#666666]=[/color] player_1();
		display_board();
		[color=#008000]**if**[/color] (end [color=#666666]==[/color] [color=#666666]1[/color]) {
			printf([color=#BA2121]"[/color][color=#BB6622]**\n\n**[/color][color=#BA2121]PLAYER 1 WINS![/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
			[color=#008000]**break**[/color];
		}
		[color=#008000]**if**[/color] (end [color=#666666]==[/color] [color=#666666]-[/color][color=#666666]1[/color]) {
			printf([color=#BA2121]"[/color][color=#BB6622]**\n\n**[/color][color=#BA2121]IT'S A DRAW![/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
			[color=#008000]**break**[/color];
		}

		end [color=#666666]=[/color] player_2();
		display_board();
		[color=#008000]**if**[/color] (end [color=#666666]==[/color] [color=#666666]1[/color]) {
			printf([color=#BA2121]"[/color][color=#BB6622]**\n\n**[/color][color=#BA2121]PLAYER 2 WINS![/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
			[color=#008000]**break**[/color];
		}
		[color=#008000]**if**[/color] (end [color=#666666]==[/color] [color=#666666]-[/color][color=#666666]1[/color]) {
			printf([color=#BA2121]"[/color][color=#BB6622]**\n\n**[/color][color=#BA2121]IT'S A DRAW![/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
			[color=#008000]**break**[/color];
		}
	} [color=#008000]**while**[/color](end [color=#666666]==[/color] [color=#666666]0[/color]);

	[color=#008000]**return**[/color] [color=#666666]0[/color];
}

[color=#408080]*/* FUNCTIONS */*[/color]
[color=#B00040]void[/color] [color=#0000FF]first_run_display[/color]()
{
    printf([color=#BA2121]"Welcome to Tic-Tac-Toe![/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
    printf([color=#BA2121]"To play, simply enter your desired column and row for each move.[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
    printf([color=#BA2121]"You can imagine the board as follows:[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
    printf([color=#BA2121]"[/color][color=#BB6622]**\t**[/color][color=#BA2121]     0   1   2 [/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
    printf([color=#BA2121]"[/color][color=#BB6622]**\t**[/color][color=#BA2121]  0    |   |   [/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
    printf([color=#BA2121]"[/color][color=#BB6622]**\t**[/color][color=#BA2121]    -----------[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
    printf([color=#BA2121]"[/color][color=#BB6622]**\t**[/color][color=#BA2121]  1    |   |   [/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
    printf([color=#BA2121]"[/color][color=#BB6622]**\t**[/color][color=#BA2121]    -----------[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
    printf([color=#BA2121]"[/color][color=#BB6622]**\t**[/color][color=#BA2121]  2    |   |   [/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
    printf([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]PLAYER 1 = X[/color][color=#BB6622]**\n**[/color][color=#BA2121]PLAYER 2 = O[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
    printf([color=#BA2121]"-------------------------------------------------------------------[/color][color=#BB6622]**\n\n**[/color][color=#BA2121]"[/color]);
}


[color=#B00040]void[/color] [color=#0000FF]new_board[/color]()
{
	[color=#B00040]int[/color] x, y;
    [color=#008000]**for**[/color] (x [color=#666666]=[/color] [color=#666666]0[/color]; x [color=#666666]<[/color] [color=#666666]3[/color]; x[color=#666666]++[/color]) {
        [color=#008000]**for**[/color] (y [color=#666666]=[/color] [color=#666666]0[/color]; y [color=#666666]<[/color] [color=#666666]3[/color]; y[color=#666666]++[/color]) {
            board[x][y] [color=#666666]=[/color] [color=#BA2121]' '[/color];
        }
    }
}

[color=#B00040]void[/color] [color=#0000FF]display_board[/color]()
{
	[color=#B00040]int[/color] x, y;
	printf([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
	[color=#008000]**for**[/color] (x [color=#666666]=[/color] [color=#666666]0[/color]; x [color=#666666]<[/color] [color=#666666]3[/color]; x[color=#666666]++[/color]) {
		[color=#008000]**for**[/color] (y [color=#666666]=[/color] [color=#666666]0[/color]; y [color=#666666]<[/color] [color=#666666]3[/color]; y[color=#666666]++[/color]) {
			[color=#008000]**if**[/color] (y [color=#666666]==[/color] [color=#666666]0[/color])
				printf([color=#BA2121]" "[/color]);
			printf([color=#BA2121]"%c"[/color], board[x][y]);
			[color=#008000]**if**[/color] (y [color=#666666]!=[/color] [color=#666666]2[/color])
				printf([color=#BA2121]" | "[/color]);
		}
		[color=#008000]**if**[/color] (x [color=#666666]!=[/color] [color=#666666]2[/color])
			printf([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]-----------[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
	}
	printf([color=#BA2121]"[/color][color=#BB6622]**\n\n**[/color][color=#BA2121]"[/color]);
}


[color=#B00040]int[/color] [color=#0000FF]player_1[/color]()
{
	printf([color=#BA2121]"Player 1[/color][color=#BB6622]**\n\n**[/color][color=#BA2121]"[/color]);
	[color=#B00040]char[/color] token [color=#666666]=[/color] [color=#BA2121]'x'[/color];
	[color=#B00040]int[/color] is_taken, result;
	[color=#B00040]int[/color] col, row;

	[color=#008000]**do**[/color] {
		col [color=#666666]=[/color] get_col();
		row [color=#666666]=[/color] get_row();
		is_taken [color=#666666]=[/color] check_taken(row, col);
		[color=#008000]**if**[/color] (is_taken [color=#666666]==[/color] [color=#666666]1[/color]) {
			printf([color=#BA2121]"That spot is already taken! Try again![/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
		}
		[color=#008000]**if**[/color] (is_taken [color=#666666]==[/color] [color=#666666]0[/color]) {
			set_token(token, col, row);
			result [color=#666666]=[/color] determine_end(token);
		}
	} [color=#008000]**while**[/color](is_taken [color=#666666]==[/color] [color=#666666]1[/color]);

	[color=#008000]**return**[/color](result);
}


[color=#B00040]int[/color] [color=#0000FF]player_2[/color]()
{
	printf([color=#BA2121]"Player 2[/color][color=#BB6622]**\n\n**[/color][color=#BA2121]"[/color]);
	[color=#B00040]char[/color] token [color=#666666]=[/color] [color=#BA2121]'o'[/color];
	[color=#B00040]int[/color] is_taken, result;
	[color=#B00040]int[/color] col, row;

	[color=#008000]**do**[/color] {
		col [color=#666666]=[/color] get_col();
		row [color=#666666]=[/color] get_row();
		is_taken [color=#666666]=[/color] check_taken(row, col);
		[color=#008000]**if**[/color] (is_taken [color=#666666]==[/color] [color=#666666]1[/color]) {
			printf([color=#BA2121]"That spot is already taken! Try again![/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
		}
		[color=#008000]**if**[/color] (is_taken [color=#666666]==[/color] [color=#666666]0[/color]) {
			set_token(token, col, row);
			result [color=#666666]=[/color] determine_end(token);
		}
	} [color=#008000]**while**[/color](is_taken [color=#666666]==[/color] [color=#666666]1[/color]);

	[color=#008000]**return**[/color](result);
}


[color=#B00040]int[/color] [color=#0000FF]get_col[/color]()
{
	[color=#B00040]int[/color] number;
	printf([color=#BA2121]"What column do you want to place your token in? "[/color]);
	scanf([color=#BA2121]"%i"[/color], [color=#666666]&[/color]number);

	[color=#008000]**return**[/color](number);
}


[color=#B00040]int[/color] [color=#0000FF]get_row[/color]()
{
	[color=#B00040]int[/color] number;
	printf([color=#BA2121]"What row do you want to place your token in? "[/color]);
	scanf([color=#BA2121]"%i"[/color], [color=#666666]&[/color]number);

	[color=#008000]**return**[/color](number);
}


[color=#B00040]int[/color] [color=#0000FF]check_taken[/color]([color=#B00040]int[/color] row, [color=#B00040]int[/color] col)
{
   [color=#008000]**return**[/color](board[row][col][color=#666666]!=[/color][color=#BA2121]' '[/color]);
}


[color=#B00040]void[/color] [color=#0000FF]set_token[/color]([color=#B00040]char[/color] token, [color=#B00040]int[/color] col, [color=#B00040]int[/color] row)
{
  board[row][col] [color=#666666]=[/color] token;
}


[color=#B00040]int[/color] [color=#0000FF]determine_end[/color]([color=#B00040]char[/color] token)
{
	[color=#B00040]int[/color] result;

	[color=#008000]**if**[/color] (board[[color=#666666]0[/color]][[color=#666666]0[/color]] [color=#666666]==[/color] token [color=#666666]&&[/color] board[[color=#666666]1[/color]][[color=#666666]0[/color]] [color=#666666]==[/color] token [color=#666666]&&[/color] board[[color=#666666]2[/color]][[color=#666666]0[/color]] [color=#666666]==[/color] token)
		result [color=#666666]=[/color] [color=#666666]1[/color];
	[color=#008000]**if**[/color] (board[[color=#666666]0[/color]][[color=#666666]1[/color]] [color=#666666]==[/color] token [color=#666666]&&[/color] board[[color=#666666]1[/color]][[color=#666666]1[/color]] [color=#666666]==[/color] token [color=#666666]&&[/color] board[[color=#666666]2[/color]][[color=#666666]1[/color]] [color=#666666]==[/color] token)
		result [color=#666666]=[/color] [color=#666666]1[/color];
	[color=#008000]**if**[/color] (board[[color=#666666]0[/color]][[color=#666666]2[/color]] [color=#666666]==[/color] token [color=#666666]&&[/color] board[[color=#666666]1[/color]][[color=#666666]2[/color]] [color=#666666]==[/color] token [color=#666666]&&[/color] board[[color=#666666]2[/color]][[color=#666666]2[/color]] [color=#666666]==[/color] token)
		result [color=#666666]=[/color] [color=#666666]1[/color];

	[color=#008000]**if**[/color] (board[[color=#666666]0[/color]][[color=#666666]0[/color]] [color=#666666]==[/color] token [color=#666666]&&[/color] board[[color=#666666]0[/color]][[color=#666666]1[/color]] [color=#666666]==[/color] token [color=#666666]&&[/color] board[[color=#666666]0[/color]][[color=#666666]2[/color]] [color=#666666]==[/color] token)
		result [color=#666666]=[/color] [color=#666666]1[/color];
	[color=#008000]**if**[/color] (board[[color=#666666]1[/color]][[color=#666666]0[/color]] [color=#666666]==[/color] token [color=#666666]&&[/color] board[[color=#666666]1[/color]][[color=#666666]1[/color]] [color=#666666]==[/color] token [color=#666666]&&[/color] board[[color=#666666]1[/color]][[color=#666666]2[/color]] [color=#666666]==[/color] token)
		result [color=#666666]=[/color] [color=#666666]1[/color];
	[color=#008000]**if**[/color] (board[[color=#666666]2[/color]][[color=#666666]0[/color]] [color=#666666]==[/color] token [color=#666666]&&[/color] board[[color=#666666]2[/color]][[color=#666666]1[/color]] [color=#666666]==[/color] token [color=#666666]&&[/color] board[[color=#666666]2[/color]][[color=#666666]2[/color]] [color=#666666]==[/color] token)
		result [color=#666666]=[/color] [color=#666666]1[/color];

	[color=#008000]**if**[/color] (board[[color=#666666]0[/color]][[color=#666666]0[/color]] [color=#666666]==[/color] token [color=#666666]&&[/color] board[[color=#666666]1[/color]][[color=#666666]1[/color]] [color=#666666]==[/color] token [color=#666666]&&[/color] board[[color=#666666]2[/color]][[color=#666666]2[/color]] [color=#666666]==[/color] token)
		result [color=#666666]=[/color] [color=#666666]1[/color];
	[color=#008000]**if**[/color] (board[[color=#666666]2[/color]][[color=#666666]0[/color]] [color=#666666]==[/color] token [color=#666666]&&[/color] board[[color=#666666]1[/color]][[color=#666666]1[/color]] [color=#666666]==[/color] token [color=#666666]&&[/color] board[[color=#666666]0[/color]][[color=#666666]2[/color]] [color=#666666]==[/color] token)
		result [color=#666666]=[/color] [color=#666666]1[/color];

	[color=#008000]**if**[/color] (result [color=#666666]!=[/color] [color=#666666]1[/color]){
		[color=#B00040]int[/color] x, y;
		[color=#008000]**for**[/color] (x [color=#666666]=[/color] [color=#666666]0[/color]; x [color=#666666]<[/color] [color=#666666]3[/color]; x[color=#666666]++[/color]) {
			[color=#008000]**for**[/color] (y [color=#666666]=[/color] [color=#666666]0[/color]; y [color=#666666]<[/color] [color=#666666]3[/color]; y[color=#666666]++[/color]) {
				[color=#008000]**if**[/color] (board[x][y] [color=#666666]==[/color] [color=#BA2121]' '[/color]) {
					result [color=#666666]=[/color] [color=#666666]0[/color];
					[color=#008000]**break**[/color];
				}
				[color=#008000]**else**[/color]
					result [color=#666666]=[/color] [color=#666666]-[/color][color=#666666]1[/color];
			}
			[color=#008000]**if**[/color] (result [color=#666666]==[/color] [color=#666666]0[/color])
				[color=#008000]**break**[/color];
		}
	}

    [color=#008000]**return**[/color](result);
}

```

---

### Post by British0zzy on 2008-10-08
I've noticed you have comments marking function declarations, global variables, main, and function definitions. It's even better if you change those to pragma marks.
So
```
/* FUNCTION DECLARTIONS */
```
becomes
```
#PRAGMA MARK FUNCTION DECLARATIONS
```
It helps when you start working on large projects with very big header files, because alot of text editors and IDE's can recognize pragma marks and it'll make it easier to find sections of code.

Also, in functions player1 and player2, put else statements before the second if statements so that is_taken is not called twice. It's not a very big deal, but always put else statements when the if statements are exclusive.
Same comment for the determine_end function. If the first event is true, then all others must be false (or they don't matter), so you don't have to check them.

---

### Post by dwhitney67 on 2008-10-08
The only thing different between the implementation of player_1() and player_2() is the token (either 'x' or 'o').  Consider implementing a single function that takes as a parameter the token, or better yet the player number.

Secondly, the player functions are performing two tasks... one, taking input from a user to place a token on the board, the other to determine if a win/draw situation occurs.  The latter task should be separated from the player function.  In other words, relocate the call to determine_end() outside of the player function.

Also, any particular reason you are using the C89 standards?  There are C99 (or GNU99) standards available that allows one to declare and initialize a variable in one "stroke", and also declare variables only within the programming block where they are needed.

Others have given you a little grief about global variables; well in C they are sometimes needed.  However, if you were to modularize your code, you could declare 'board' as a static variable within its own module (i.e. a .c file) and in addition provide all of the accessor functions that are required to manipulate it.  If you pull this off, then you are one step closer to understanding the basic concepts of OOD/OOP.

---

### Post by rnodal on 2008-10-08
> **Sinkingships7 said:**
> Then where do you propose I use them?

Let me give you a humble example. Eventually as you go deeper in your adventures with C/C++ you will notice that no every thought you have can be represented as an integer, char etc. So you need to create your own data structure that better reflects your idea. For example:
```

struct
{
    int ID;
    char name[30];
    char address[120];
} Person; 

```

Now, let's say that you have a function that registers a person for something (A contact list for example). Sending/Passing the whole thing to the function would be a bad idea because you will be duplicating the information. In the other hand if you pass a pointer to the struct then things will be more efficient.

Another way of thinking about it would be that if you have a heavy box filled with content and someone offers to help you sort the content then you don't move the box you just point them to where the box is and let them do the work without moving the whole box. 

Obviously this is not the only case where pointers are useful but I hope it gives you some idea.

English is not my first language so I'm pretty sure someone could express my concept in a much better way. Take care,

-r

---

### Post by Sinkingships7 on 2008-10-08
> **rnodal said:**
> Let me give you a humble example. Eventually as you go deeper in your adventures with C/C++ you will notice that no every thought you have can be represented as an integer, char etc. So you need to create your own data structure that better reflects your idea. For example:
```

struct
{
    int ID;
    char name[30];
    char address[120];
} Person; 

```

Now, let's say that you have a function that registers a person for something (A contact list for example). Sending/Passing the whole thing to the function would be a bad idea because you will be duplicating the information. In the other hand if you pass a pointer to the struct then things will be more efficient.

Another way of thinking about it would be that if you have a heavy box filled with content and someone offers to help you sort the content then you don't move the box you just point them to where the box is and let them do the work without moving the whole box. 

Obviously this is not the only case where pointers are useful but I hope it gives you some idea.

English is not my first language so I'm pretty sure someone could express my concept in a much better way. Take care,

-r

No, what you said makes perfect sense. But when I wrote that, it was months and months ago. I'm a quite a bit better than I used to be. :) Thank you, though.

---

### Post by Sinkingships7 on 2008-10-08
> **British0zzy said:**
> I've noticed you have comments marking function declarations, global variables, main, and function definitions. It's even better if you change those to pragma marks.
So
```
/* FUNCTION DECLARTIONS */
```
becomes
```
#PRAGMA MARK FUNCTION DECLARATIONS
```
It helps when you start working on large projects with very big header files, because alot of text editors and IDE's can recognize pragma marks and it'll make it easier to find sections of code.

I did not know that existed... Thanks!

---

### Post by rnodal on 2008-10-08
[QUOTE=Sinkingships7]No, what you said makes perfect sense. But when I wrote that, it was months and months ago. I'm a quite a bit better than I used to be. :) Thank you, though.[/QUOTE]

I'm glad that everything is going great.:)

-r

---

### Post by nvteighen on 2008-10-08
btw, you may want to have a look at this Tic-Tac-Toe of mine written in Python. [http://ubuntuforums.org/showthread.php?t=894509](http://ubuntuforums.org/showthread.php?t=894509)

---

### Post by Sinkingships7 on 2008-10-08
> **nvteighen said:**
> btw, you may want to have a look at this Tic-Tac-Toe of mine written in Python. [http://ubuntuforums.org/showthread.php?t=894509](http://ubuntuforums.org/showthread.php?t=894509)

It's much cleaner, that's for sure. :oops:

---

### Post by nvteighen on 2008-10-09
> **Sinkingships7 said:**
> It's much cleaner, that's for sure. :oops:
Thanks! The trick is that it was actually meant to be a library (that's why the board is a class, etc.) that accepts highly customization of the game and then I just wrote a little interface for the classic Tic-Tac-Toe... and well, I happened to have coded a game :) You could still import it and use it to create a new interface (but I'd have to write an API doc).

For your code
1. Follow dwhitney67's advice to reduce player1() and player2() into simple wrappers that prepare data to be passed to a generic function (say 'player()') that does the rest for both.

2. My Python code does extensive use of some functional programming stuff, specially to test whether someone won or not, by generating a list of what's on some row, column or diagonal and then the test is just a function that checks if all elements in that list are the same. I know C is rather limited to do exactly that unless you start using GList's from GLib of something like that, but maybe you could try to generalize the function that checks the board's status a bit more so that it isn't a bunch of almost hard-coded if's...

---

