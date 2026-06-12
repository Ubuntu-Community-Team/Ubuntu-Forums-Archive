---
title: "Detect Arrow keys using termios.h"
date: 2015-04-30
forum: Programming Talk
---

### Post by ravenslock on 2015-04-30
[SIZE=3][FONT=courier new]I googled about getting input from C in the terminal without the enter key in relation to article:

[http://ubuntuforums.org/archive/index.php/t-225713.html](http://ubuntuforums.org/archive/index.php/t-225713.html)
[http://ubuntuforums.org/showthread.php?t=225713](http://ubuntuforums.org/showthread.php?t=225713)

I remember from past experience that the arrow keys returns 2 values and the variable used must be an integer not character. I played around with the code and tried 3 variables and with luck it worked.

```

/*
http://ubuntuforums.org/archive/index.php/t-225713.html
*/

#include <stdio.h>
#include <unistd.h>
#include <termios.h>

int getch(void);

int main()
{
 int x = ' ';
 int y = ' ';
 int z = ' ';

 printf("Press any key to continue...\n");
 x = getch();

 if (x == 27)
 {
  y = getch();
  z = getch();
  printf("Key code y is %d\n", y);
  printf("Key code z is %d\n", z);
 }
 printf("Key code x is %d\n", x);
 printf("The key you entered is: %c \n", x);

 if (x == 27 && y == 91)
 {
  switch (z)
  {
   case 65:
   printf("up arrow key pressed\n");
   break;

   case 66:
   printf("down arrow key pressed\n");
   break;

   case 67:
   printf("right arrow key pressed\n");
   break;

   case 68:
   printf("left arrow key pressed\n");
   break;
  }
 }

 return 0;
}

int getch(void)
{
 int ch;
 struct termios oldt;
 struct termios newt;
 tcgetattr(STDIN_FILENO, &oldt); /*store old settings */
 newt = oldt; /* copy old settings to new settings */
 newt.c_lflag &= ~(ICANON | ECHO); /* make one change to old settings in new settings */
 tcsetattr(STDIN_FILENO, TCSANOW, &newt); /*apply the new settings immediatly */
 ch = getchar(); /* standard getchar call */
 tcsetattr(STDIN_FILENO, TCSANOW, &oldt); /*reapply the old settings */
 return ch; /*return received char */
}

```
[/FONT][/SIZE]

---

