---
title: "(C) Writing a game in ncurses"
date: 2008-06-29
forum: Programming Talk
---

### Post by spadewarrior on 2008-06-29
I'm trying to write a clone of snake in ncurses. My problem at the moment is that once the snake starts to travel in one direction I can't get it to change. It seems that further calls to getchar() are ignored. I have turned off line buffering with cbreak() but this has not helped.

Can anyone point out what to do?

Any help appreciated.

:)

[PHP]


#include <ncurses.h>
#include <stdlib.h>
#include <ctype.h>
#include <time.h>
#include <unistd.h>

int ranN( int n );
void move_snake(WINDOW *snakeWin, int y, int x, int dir, char n, char c);
int direction(int dir, char c);


struct thing
{
    int x, y, dir;
    char n; // 'F' or 'O'
    char body[9000];
    int size;
};

int main(void)
{

    struct thing snake, food;

    snake.n = 'O';
    food.n = '*';
    snake.dir = -1;

    int winSize = 0;
    int y,x, xMax, yMax;
    char c, ch;

    int foodEaten = 0;
    int collision = 0;
    int score = 0;
    int count;

    WINDOW *snakeWin;


    // Make the snake 3 chars long
    for(count = 0; count < 2; count++)
        snake.body[count] = 'o';


    // Start ncurses mode

    initscr();

    cbreak(); // no line buffering

    snakeWin = newwin(0, 0, 0, 0);
    keypad(snakeWin, TRUE);
    getmaxyx(snakeWin, yMax, xMax);
    winSize = y*x;

    food.y = yMax %6;
    food.x = xMax %5;


    // Prepare game window

    curs_set(0); // hide the cursor
    wrefresh(snakeWin);


    food.y = ranN( yMax);
    food.x = ranN( xMax );

    //print the food on the screen!
    mvwprintw(snakeWin, food.y, food.x, "%c", food.n);
    wrefresh(snakeWin);



    // Put the snake on the screen, not where the FOOD is
    snake.x = 30;
    snake.y = 10;

    // Print the snake on the screen!
    mvwprintw(snakeWin, snake.y, snake.x, "%c", snake.n);
    wrefresh(snakeWin);

    while( foodEaten == 1 )
    {
        mvwdelch(snakeWin, food.y, food.x);

        count++;
        snake.body[count] = 'o';
        food.y = ranN( yMax);
        food.x = ranN( xMax );

        //print the food on the screen!
        mvwprintw(snakeWin, food.y, food.x, "%c", food.n);

        wrefresh(snakeWin);
    }

    // Key input (controls)

    while ( (c = getchar() ) != '\0')
    {
        snake.dir = direction(snake.dir, c);
        move_snake(snakeWin, snake.y, snake.x, snake.dir, snake.n, c);
    }


// end of main WHILE loop

    endwin(); // end ncurses mode

    return 0;
}

int ranN( int n )
{
    srand( time(NULL) );
    int num = 90000;

    while(num > n)
        num =  rand() /100;
    return num;
}



void move_snake(WINDOW *snakeWin, int y, int x, int dir, char n, char c)
{
    while ( dir == 0) // UP
    {

        mvwprintw(snakeWin, y--, x, "%c", n);
        mvwprintw(snakeWin, (y+2), x, " ");

        wrefresh(snakeWin);
        usleep(100000);


    }

    while ( dir == 1 ) // RIGHT
    {
        mvwprintw(snakeWin, y, x++, "%c", n);
        mvwprintw(snakeWin, y, (x-2), " ");
        wrefresh(snakeWin);
        usleep(100000);
    }

    while ( dir == 2) // DOWN
    {
        mvwprintw(snakeWin, y++, x, "%c", n);
        mvwprintw(snakeWin, (y-2), x, " ");
        wrefresh(snakeWin);
        usleep(100000);
    }

    while( dir == 3 ) // LEFT
    {
        mvwdelch(snakeWin, y, x);
        wrefresh(snakeWin);
        mvwprintw(snakeWin, y, x--, "%c", n);
        wrefresh(snakeWin);
        usleep(100000);
    }
}

int direction(int dir, char c)
{
    switch(c)
    {
        case 'w': //UP
        {
            dir = 0;
            break;
        }
        case 'd': // RIGHT
        {
            dir = 1;
            break;
        }
        case 's': // DOWN
        {
            dir = 2;
            break;
        }
        case 'a': // LEFT
        {
            dir = 3;
            break;
        }
        case 'q':
        {
            endwin();
            exit(1);
        }

    }
    return dir;
}
[/PHP]

---

### Post by dwhitney67 on 2008-06-29
Question... how do you exit from the while-loops in move_snake()??  I think you may need to revisit your logic in each of the while-loops, and in general with the overall logic in move_snake().

I mean, if the direction is UP, why would you proceed to check if it is DOWN, LEFT, or RIGHT.  The snake can only move in one direction at a time.  When you are done processing that direction, exit the function.

Also, why does direction() take in the first parameter 'dir'.  That should be a local variable that is returned.

---

### Post by spadewarrior on 2008-06-29
Yeah, I thought my logic might be screwy. Do you think it would be better to have a separate function for each direction?

---

### Post by dwhitney67 on 2008-06-29
No, I think one function is fine.

If I understand the premise of the game, you want the user to set the direction of movement for the snake, and then have the snake move in that direction until told otherwise.  Is this correct?

If so, you may need to consider using a select() call that can monitor stdin.  If no key is pressed in a certain time period, the snake keeps moving in the last requested direction.  Otherwise, if a key is pressed, you handle it.

Here's some thoughts you can run with:
[PHP]int dir = 0;

while (true)
{
  move_snake(..., dir,...);

  if (select(..., timeout) > 0)
  {
    char c = getchar();
    int newDir = direction(c);
    
    // check if user wants to quit
    if (newDir == -1)
      break;

    // only set new direction if input is valid
    if (newDir != -2)
      dir = newDir;
  }
}[/PHP]

---

### Post by spadewarrior on 2008-06-29
Thanks, that sounds like a nice idea. I'd not heard of that function.

---

### Post by dwhitney67 on 2008-06-29
Maybe you don't need the select().  Maybe just using getch().
[PHP]while (true)
{
  char c = getch();

  int dir = direction(c);

  // etc
}[/PHP]

---

### Post by dwhitney67 on 2008-06-29
Here's something that I got to work:
[PHP]
  ...
  // Game Engine
  //
  struct timeval timeout = { 0, 500000 };   // 0.5 seconds
  fd_set rfds_save;
  FD_ZERO(&rfds_save);
  FD_SET(fileno(stdin), &rfds_save);

  cbreak(); // no line buffering
  snake.dir = 0;

  while (true)
  {
    fd_set rfds = rfds_save;

    if (select(1, &rfds, 0, 0, &timeout) > 0)
    {
      int newDir = direction( getchar() );

      // check if user wants to quit
      if (newDir == -1)
        break;

      // only set new direction if input is valid
      if (newDir != -2)
        snake.dir = newDir;
    }

    // move the snake in the desired direction
    move_snake(snakeWin, &snake);
  }
  ...
[/PHP]
Note that I have modified the move_snake() function to accept the entire snake structure.  This was done so that when the position of the snake is modified, the x-y coordinates can be retained within the structure.  Otherwise, as you originally implemented the code, the information is lost.

---

### Post by spadewarrior on 2008-06-29
Is getch() and halfdelay() a no-goer? I'm afraid that select() is a bit beyond me at this stage. Do you know of a nice introduction to the function? The man page is not newbie-friendly! :)

---

### Post by dwhitney67 on 2008-06-29
The select() library function is easy to use.  It takes 5 parameters:
- the value of the largest file descriptor contained in 'read' set + 1.
- the 'read' set
- the 'write' set (which I never use)
- the 'error' set (which I never use)
- the time-out period (if any)

Generally select() is used when someone wants to monitor activity on say, one or more network sockets, opened files, or even stdin.  Of course stdout and stderr could be used too, but I can't think of a reason why one would monitor these.

This is helpful in that it reduces code complexity and obviates the need to poll each file/socket descriptor for activity (which can be time consuming).  select() will report any activity, and set a bit in the 'read' set corresponding to the file/socket descriptor.

There are macros functions such as FS_ZERO(), FD_SET(), and FD_ISSET() to manage the 'read' set.  Initially it is zeroed out, then each file/socket descriptor is added to the set, and then the set is passed to select().  When select() indicates that there is activity, then the FD_ISSET() can be used to determine on which file/socket descriptor the activity is occurring on.

Anyhow, in the tidbit of code I provided, select() reports any stdin activity.  If no activity is detected, then select() will block until the time-out period expires.  If the time period expires, the snake will continue to move in the same direction as previously set.

Here's a modified version of the snake.c code, which is primarily lifted from the code you provided in the OP.  Note that there is a run-time bug in the move_snake() function when the snake makes a 90-degree turn.  
[PHP]
#include <ncurses.h>
#include <stdlib.h>
#include <ctype.h>
#include <time.h>

#include <sys/time.h>
#include <sys/types.h>
#include <unistd.h>
#include <stdio.h>
#include <string.h>


struct Thing
{
    char   n;     // 'F' or 'O'
    int    x, y;
    int    dir;
    size_t size;
};


int ranN(int n);
void move_snake(WINDOW *snakeWin, struct Thing *snake);
int direction(char c);


int main(void)
{
  // Start ncurses mode
  initscr();

  WINDOW *snakeWin = newwin(0, 0, 0, 0);
  int xMax, yMax;

  keypad(snakeWin, TRUE);
  getmaxyx(snakeWin, yMax, xMax);

  // Prepare food
  struct Thing food;
  food.n = '*';
  food.y = ranN(yMax);
  food.x = ranN(xMax);

  // Prepare snake
  struct Thing snake;
  snake.n = 'O';
  snake.dir = -1;
  snake.x = 30;
  snake.y = 10;
  snake.size = 3;


  // Prepare game window
  curs_set(0); // hide the cursor
  wrefresh(snakeWin);

  //print the food on the screen!
  mvwprintw(snakeWin, food.y, food.x, "%c", food.n);
  wrefresh(snakeWin);

  // Print the snake on the screen!
  mvwprintw(snakeWin, snake.y, snake.x, "%c", snake.n);
  wrefresh(snakeWin);

  //int foodEaten = 0;

  //while (foodEaten == 1)
  //{
  //}

  // Game Engine
  //
  struct timeval timeout = { 0, 250000 };   // 0.25 seconds
  fd_set rfds_save;
  FD_ZERO(&rfds_save);
  FD_SET(fileno(stdin), &rfds_save);    // 0 == stdin

  cbreak(); // no line buffering
  snake.dir = 0;

  while (true)
  {
    fd_set rfds = rfds_save;

    if (select(fileno(stdin)+1, &rfds, 0, 0, &timeout) > 0)
    {
      int dir = direction( getchar() );
    
      // check if user wants to quit
      if (dir == -1)
        break;

      // only set new direction if input is valid
      if (dir != -2)
        snake.dir = dir;
    }

    // move the snake in the desired direction
    move_snake(snakeWin, &snake);

    if ( snake.y == food.y && snake.x == food.x)
    {
      mvwdelch(snakeWin, food.y, food.x);

      ++snake.size;

      food.y = ranN( yMax);
      food.x = ranN( xMax );

      //print the food on the screen!
      mvwprintw(snakeWin, food.y, food.x, "%c", food.n);

      wrefresh(snakeWin);
    }
  }

  endwin();

  return 0;
}

int ranN(int n)
{
  srand(time(0));

  int num = 90000;

  while (num > n)
    num =  rand() / 100;

  return num;
}

void move_snake(WINDOW *snakeWin, struct Thing *snake)
{
  switch (snake->dir)
  {
    case 0:  // UP
        mvwprintw(snakeWin, --snake->y, snake->x, "%c", snake->n);
        mvwprintw(snakeWin, (snake->y+snake->size), snake->x, " ");
        break;

    case 1:  // RIGHT
        mvwprintw(snakeWin, snake->y, ++snake->x, "%c", snake->n);
        mvwprintw(snakeWin, snake->y, (snake->x-snake->size), " ");
        break;

    case 2:  // DOWN
        mvwprintw(snakeWin, ++snake->y, snake->x, "%c", snake->n);
        mvwprintw(snakeWin, (snake->y-snake->size), snake->x, " ");
        break;

    case 3:  // LEFT
        mvwprintw(snakeWin, snake->y, --snake->x, "%c", snake->n);
        mvwprintw(snakeWin, snake->y, (snake->x+snake->size), " ");
        break;
  }

  wrefresh(snakeWin);

  // up the game tempo as the snake grows bigger!
  usleep(325000 - (snake->size * 25000));
}

int direction(char c)
{
  switch (c)
  {
    case 'w': return 0;       // UP
    case 'd': return 1;       // RIGHT
    case 's': return 2;       // DOWN
    case 'a': return 3;       // LEFT
    case 'q': return -1;      // QUIT
  }

  return -2;                  // ERROR
}
[/PHP]

---

### Post by spadewarrior on 2008-06-30
Thanks for you help. I'm still getting my head around select() but it's starting to make sense.

---

