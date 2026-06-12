---
title: "How to set user-defined colours on a command line screen?"
date: 2011-07-04
forum: Programming Talk
---

### Post by resander on 2011-07-04
I am on Ubuntu 10.04.

I want to make a simple user interface for C/C++ that supports simple menus and drop-downlist/panes for command line processing.

I have tried curses/ncurses and that works, but there are only eight colours (black,red, green, brown, blue, magenta, cyan, white).
These look awful when used in lists and panes. The curses spec mentions init_color(paletteindex, r,g,b) that changes the colour associated with palettindex. However, the capability enquiry function can_change_color() returns false.

I also wrote some functions that use escape sequences and console codes, e.g.

    static void myreset ( )
    {
    printf("\033[0m" );
    fflush(stdout);
    }

    static void mysetcol ( int val )
    {
    printf("\033[%dm", val );
    fflush(stdout);
    }

    static void mygotoxy(int x, int y)
    {
    printf("\033[%d;%df", y, x);
    fflush(stdout);
    }

    used like:

    int main( )
    {
    mygotoxy ( 3 , 4 ) ;
    mysetcol ( 33 ) ; // text
    mysetcol ( 44 ) ; // backgound
    printf ( "Testing only") ;
    getch ( ) ;
    return 0 ;
    }



The val parameter in mysetcol typically specifies a text or background colour, but only the same eight colours available via curses; otherwise the myxxx routines also work fine.

Is there a way to change the 8-colour palette so I can get different colours for curses or the myxxx functions? OR is there some other palette e.g a 256 colour palette that I may be able to use perhaps without making any changes?

I want the change the colours on the fly in the command line program only, not permanently for the Terminal.

Ken

---

### Post by ziekfiguur on 2011-07-04
As far as I know it's not possible to change the palette. But, there are a couple more colors you can use: 90 - 99 for foreground and 100 - 109 for background in the escape codes give some brighter colors.

---

### Post by nvteighen on 2011-07-04
If can_change_color() returns false, then your terminal doesn't support color redefinition. What terminal (emulator) are you using to test this?

---

### Post by johnl on 2011-07-04
Try doing:

```

TERM=xterm-256color ./run-your-program

```

Using gnome-terminal, with this set, you get 256 colors which you can redefine as you want.

---

### Post by resander on 2011-07-10
Many thanks for the info...

Ziekfiguur,
The extra colours worked fine when using mysetcol, but are not available via curses, only the eight basic colours are (defined COLOR_BLACK=0, COLOR_RED=1..).

nvteighen,
When using the Code::Blocks IDE I am setting 'gnome-terminal' in the preferences. The Terminal emulator looks the same when bringing up the command line, so I assumed it is also a 'gnome-terminal', but echo $TERM shows xterm. 

johnl,
I issued TERM=xterm-256 color from the command line and checked it had been set by echo $TERM, but I don't know how to select text and background colours from the program. Nor do I know how to read and process arrow and home keys. Have only experimented with curses and myxxx sequences and never used them for user interfaces. 

I think 256 colours would be enough to make the dropdown list and panes look reasonable, so this is probably the best way.


The user interface program needs to read the arrow, home, end keys etc. Curses provide small integers for these macro-defined KEY_UP and KEY_DOWN etc. When pressing a key the small integer is returned.

When pressing an arrow key without curses using another getch (see below) then multiple charcodes are returned, like this on Ubuntu 10.04 displayed as printablechar(charcode):
```

left arrow  
   char is=(7)
   char is=[(91)   
   char is=D(68)
right arrow
   char is=(7)
   char is=[(91)
   char is=C(67)
up arrow
   char is=(7)
   char is=[(91)
   char is=A(65)
down arrow
   char is=(7)
   char is=[(91)
   char is=B(66)
home arrow
   char is=(7)
   char is=O(79)
   char is=H(72)
home arrow
   char is=(7)
   char is=O(79)
   char is=F(70)
page up
   char is=(7)
   char is=[(91)
   char is=5(53)
   char is=~(126)
page down
   char is=(7)
   char is=[(91)
   char is=6(54)
   char is=~(126)

```

I can determine the key pressed by comparing the characters received against the patterns above, but I don't know how general that would be. Would it be valid for this Ubuntu, all Ubuntus, some Linuxes, most Linuxes or all Linuxes?
 
mygetch:
```

static int mygetch ( )
   {
   struct termios oldt, newt;
   int ch;
   tcgetattr( STDIN_FILENO, &oldt );
   newt = oldt;
   newt.c_lflag &= ~( ICANON | ECHO );
   tcsetattr( STDIN_FILENO, TCSANOW, &newt );
   ch = getchar();
   tcsetattr( STDIN_FILENO, TCSANOW, &oldt );
   return ch;
   }

```

Ken

---

### Post by ziekfiguur on 2011-07-10
> **resander said:**
> I can determine the key pressed by comparing the characters received against the patterns above, but I don't know how general that would be. Would it be valid for this Ubuntu, all Ubuntus, some Linuxes, most Linuxes or all Linuxes?

I think this depends on the terminal you're using, so as long as you have the same terminal this should be the same on all linuxes. However, ncurses was created to offer one single interface that should work on (almost) all terminals. Therefore, if you want your program to be used by anyone other than yourself, it's by far the best to use ncurses.

To change the colors with xterm-256color, have you checked that can_change_color() returns true? If so, i think you could use color_set(short,void*); which is also defined by ncurses. To see how to use it you should look up the ncurses documentation

---

### Post by nvteighen on 2011-07-10
> **resander said:**
> 
The user interface program needs to read the arrow, home, end keys etc. Curses provide small integers for these macro-defined KEY_UP and KEY_DOWN etc. When pressing a key the small integer is returned.

When pressing an arrow key without curses using another getch (see below) then multiple charcodes are returned, like this on Ubuntu 10.04 displayed as printablechar(charcode):
```

left arrow  
   char is=(7)
   char is=[(91)   
   char is=D(68)
right arrow
   char is=(7)
   char is=[(91)
   char is=C(67)
up arrow
   char is=(7)
   char is=[(91)
   char is=A(65)
down arrow
   char is=(7)
   char is=[(91)
   char is=B(66)
home arrow
   char is=(7)
   char is=O(79)
   char is=H(72)
home arrow
   char is=(7)
   char is=O(79)
   char is=F(70)
page up
   char is=(7)
   char is=[(91)
   char is=5(53)
   char is=~(126)
page down
   char is=(7)
   char is=[(91)
   char is=6(54)
   char is=~(126)

```

I can determine the key pressed by comparing the characters received against the patterns above, but I don't know how general that would be. Would it be valid for this Ubuntu, all Ubuntus, some Linuxes, most Linuxes or all Linuxes?


Don't go that low-level! It's unnecessary and as you already suggest, it may be unportable. Use the ncurses macros, which exist for a reason: they guarrantee portability in all systems that use ncurses because however the key is defined in each system, you'll be referring to it using the macro... And ncurses is available in any OS that comes from UNIX or is a Unix-like system; that includes GNU/Linux, of course.

Look at this example:
```

/* Compile with -lcurses */

#include <curses.h>

void print_key(WINDOW *scr, int input)
{
    /* This can surely be improved a bit... */

    switch(input)
    {
    case KEY_UP:
        (void) waddstr(scr, "Up!\n");
        break;
    case KEY_DOWN:
        (void) waddstr(scr, "Down!\n");
        break;
    case KEY_LEFT:
        (void) waddstr(scr, "Left!\n");
        break;
    case KEY_RIGHT:
        (void) waddstr(scr, "Right!\n");
        break;
    default:
        (void) waddch(scr, input);
        (void) waddch(scr, '\n');
        break;
    }

    (void) wrefresh(scr);
}

int main(void)
{
    /* I prefer getting the returned WINDOW * and pass it around using the w-
     * named functions because it's more structured than relying on the globally
     * defined stdscr WINDOW *. */
    WINDOW *myscr = initscr();

    /* Input */
    (void) cbreak(); /* Input is char-based */
    (void) raw(); /* No signals will be interpreted */
    (void) keypad(myscr, TRUE); /* Gives us access to the function keys,
                                 * including direction keys */

    /* Output */
    (void) noecho();

    /* Useful reminder */
    (void) waddstr(myscr, "Press q to quit!\n");
    (void) wrefresh(myscr);

    int input = 0;
    while((input = wgetch(myscr)) != 'q')
        print_key(myscr, input);

    (void) endwin();
    return 0;
}

```

The reason why I'm casting to void all those functions is because I'm dismissing the return values for convenience while showing that something is actually being returned. In a real application, you should check them, as they may signal errors and other conditions.

---

### Post by resander on 2011-07-11
The IBM PC was announced 12 August 1981. It displayed 16 colours.
As far as I know (n)curses displays 8 colours 2011. This makes overlapping lists and pane/panels come out looking extremely ugly for this app.

ncurses offers portability and a very large set of easy-to-use functions. With the capability to change colours I would definitely choose it, but ncurses 'can_change_color' function returns false, so I don't know yet.


Googled and found that (all,most?) linux terminal emulators use VT220 escape sequences with VT100 being a subset. Indeed the arrow, home, page-up keys in my previous post are VT220 sequences as were function key codes etc that I dumped out a short while ago.

[http://www.termsys.demon.co.uk/vtansi.htm](http://www.termsys.demon.co.uk/vtansi.htm)       -- VT100
[http://en.wikipedia.org/wiki/ANSI_escape_code](http://en.wikipedia.org/wiki/ANSI_escape_code) 
[http://www.connectrf.com](http://www.connectrf.com)                        -- VT220
[http://linux.die.net/man/4/console_codes](http://linux.die.net/man/4/console_codes)        -- linux console codes

so application programs using VT220 sequences for input and output should be fairly portable too when interfacing to conio.


The linux console codes link above mentions a 'private mode' linux escape sequence ESC ] P nrrggbb that puts rgb value rr,gg,bb at palette index n with nrrggbb given in hex and another sequence ESC ] R that resets the palette. However, the 'Bugs' section at the end says:

'The OSC (set palette) sequence is a greater problem, since xterm may interpret this as a control sequence which requires a string terminator (ST). Unlike the setterm sequences which will be ignored (since they are invalid control sequences), the palette sequence will make xterm appear to hang (though pressing the return-key will fix that). To accommodate applications which have been hardcoded to use Linux control sequences, set the xterm resource brokenLinuxOSC to true.'

I don't understand the bug description above; in particular I don't know if there might be any nasty lasting consequences (like the terminal emulator being damaged) if I try changing the palette. Anyone?

  
Johnl suggested setting TERM xterm-256color and then run the program. I don't know how to select the colours and make them come out, but tried ncurses in a small command-line test program after having set TERM=xterm-256color:
```

  int res = init_pair(1, 20, COLOR_RED);
  attron(COLOR_PAIR(1));
  mvprintw ( 2, 2, "Red background" ) ;
  .....

```
 
but variable res was set to ERR (-1) probably because the foreground colour 20 is out of range (0..7).

The colour parameters of init_pair function are short integers able to set pairs for a 32767 colour palette, but ncurses does not seem to allow that. Monitors nowadays can display millions of colours. It would be unreasonable and unnecessary to expect ncurses to handle that, but I think it should be able to show more than eight. A 256 colour palette for ncurses seems about right, but I could not make it work. Is there a way?

Ken

---

### Post by johnl on 2011-07-11
> **resander said:**
> 
Johnl suggested setting TERM xterm-256color and then run the program. I don't know how to select the colours and make them come out, but tried ncurses in a small command-line test program after having set TERM=xterm-256color:
```

  int res = init_pair(1, 20, COLOR_RED);
  attron(COLOR_PAIR(1));
  mvprintw ( 2, 2, "Red background" ) ;
  .....

```
 
but variable res was set to ERR (-1) probably because the foreground colour 20 is out of range (0..7).


My comment was that setting TERM=xterm-256color, at least for me in gnome-terminal, will cause can_change_color() to return true.

When can_change_color() returns true, you can create a color:

```

/* here r,g,b are between 0-1000.  index is between 0 and COLORS */
init_color(color_index, r_value, g_value, b_value);
/* That color index is then available for usage in a color pair < COLOR_PAIR: */
init_pair(pair_index, color_fg, color_bg);

```

If you already knew all this, I apologize.

**Edit:**

Here's a small example program which takes colors as arguments and prints them out using curses in color:

```

/* e.g. "TERM=xterm-256color ./test_colors 3366FF FF0000 3a4682" */
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <ncurses.h>
#include <unistd.h>

int main(int argc, char* argv[]) 
{
    int i;
    
    initscr();
    start_color();
    
    if (!can_change_color()) {
        printw("can't change colors :(\n");
        refresh();
        sleep(2);
        endwin();
        exit(0);
    };
    
    printw("can change colors.\n");
    printw("%d colors, %d pairs available\n", COLORS, COLOR_PAIRS);
    
    int color_index = 3;
    int pair_index  = 2;
    double magic = 1000/255.0;
    
    /* init_color( */
    for(i = 1; i < argc; ++i) {
        const char* hexcolor = argv[i];
        int r, g, b;
        if (hexcolor[0] == '#') {
            ++hexcolor;
        }
        
        sscanf(hexcolor, "%02x%02x%02x", &r, &g, &b);
        init_color(color_index,
                   (int)(r * magic),
                   (int)(g * magic),
                   (int)(b * magic));
        init_pair(pair_index, color_index, 0);
        attrset(COLOR_PAIR(pair_index));
        printw("#%02x%02x%02x\n", r, g, b);
        refresh();
        ++pair_index;
        ++color_index;
    }
    
    sleep(5);
    
    
    endwin();
}

```

---

### Post by nvteighen on 2011-07-11
Hm... This works for me perfectly on the Linux console: it shows COLOR_BLUE as red after redefining it! But gnome-terminal doesn't support color redefinition, so it fails.

```


#include <stdlib.h>
#include <curses.h>

void exit_with_error(WINDOW *scr, const char *msg)
{
    waddstr(scr, msg);
    waddch(scr, '\n');
    wrefresh(scr);
    wgetch(scr); // Force waiting
    endwin();
    exit(EXIT_FAILURE);
}

int main(void)
{
    WINDOW *myscr = initscr();
    
    int color_able = start_color();
    if(color_able == ERR)
    {
        exit_with_error(myscr, "Terminal doesn't support color");
    }

    if(!can_change_color())
    {
        exit_with_error(myscr, "Terminal doesn't support color redefinition");
    }

    /* The experiment consists in redefining blue as red */

    int color_init_ok = init_color(COLOR_BLUE, 1000, 0, 0);
    init_pair(1, COLOR_BLUE, COLOR_WHITE);
    if(color_init_ok != ERR)
    {
        attron(COLOR_PAIR(1));
        waddstr(myscr, "OK!\n");
    }
    else
    {
        waddstr(myscr, "Nope\n");
    }

    wrefresh(myscr);

    wgetch(myscr);
    endwin();
    
    return EXIT_SUCCESS;
}

```

---

### Post by resander on 2011-07-13
johnl:
Many thanks...
Your test program showed how to change the colours together with other curses functions. Very useful!

Setting TERM=xterm-256color before running the program enabled colour definition and also output of 256 colours from the palette.

I wrote a test program that outputs all colours and they look fairly similar to the picture in [http://www.mudpedia.org/wiki/Xterm_256_colors](http://www.mudpedia.org/wiki/Xterm_256_colors)
```

static void prtcpnl ( bool showpairval , int pairval )
   {
   if ( showpairval )
      {
      int usecp = 255 ;
      init_pair ( usecp , COLOR_WHITE , COLOR_GREEN ) ;
      attron(COLOR_PAIR(usecp));
      printw("p%d\n" , pairval) ;
      }
   else
      {
      printw("\n") ;
      }
   }

static void tryuse2 ( int initcpair , int startbg )
   {
   printw ( " TWO " ) ;
   int cpair = initcpair ;
   int fg = 0 ;
   int bg = startbg ;
   init_pair(cpair, fg, bg);
   attron(COLOR_PAIR(cpair));
   printw("bg=%03d cp=%d   ", bg , cpair );
   cpair++ ;
   bg++ ;
   init_pair(cpair, fg, bg);
   attron(COLOR_PAIR(cpair));
   printw("bg=%03d cp=%d", bg , cpair );
   }


static void tryuse256cols ( int startk , int startcp , bool use2more ,
                            bool showcpval )
   {
   int cp = startcp ;
   int fgcol = 0 ;
   int bgcol ;
   char * fmt = "%03d " ;
   int column = 0 ;
   int k = startk ;
   while ( k < 16 )  // basic colours
      {
      if ( column == 8 )
         {
         //printw("\n" ) ;
         prtcpnl( showcpval , cp-1 ) ;
         column = 0 ;
         }
      bgcol = k ;
      init_pair(cp, fgcol, bgcol);
      attron(COLOR_PAIR(cp));
      printw(fmt, bgcol);
      cp++ ;
      column++ ;
      k++ ;
      }

   prtcpnl( showcpval , cp-1 ) ;
   column = 0 ;
   fgcol = 7 ;
   while ( k < 232 )
      {
      if ( column == 18 )
         {
         prtcpnl ( showcpval , cp-1 ) ;
         column = 0 ;
         fgcol = 0 ;
         }
      bgcol = k ;
      init_pair(cp, fgcol, bgcol);
      attron(COLOR_PAIR(cp));
      printw(fmt, bgcol);
      cp++ ;
      column++ ;
      k++ ;
      }
   prtcpnl ( showcpval , cp-1 ) ;
   printw("\n" ) ;
   column = 0 ;
   fgcol = 7 ;
   while ( k < 256 )
      {
      if ( column == 8 )
         {
         prtcpnl ( showcpval , cp-1 ) ;
         column = 0 ;
         fgcol = 0 ;
         }
      bgcol = k ;
      init_pair(cp, fgcol, bgcol);
      attron(COLOR_PAIR(cp));
      printw(fmt, bgcol);
      cp++ ;
      column++ ;
      k++ ;
      }
   if ( use2more )
      {
      sleep ( 6 ) ;//getch() ;
      tryuse2 ( 250 , 254 ) ;
      }
   prtcpnl ( showcpval , cp-1 ) ;
   refresh();
   }

static void chgcolours ( int argc , char * argv[] )
   {
   //   change every eighth colour of 256 to red or blue (alternating)
   bool usered = true ;
   int k = 0 ;
   while ( k < 256 )
      {
      if ( usered )
         {
         init_color( k, 1000 , 0 , 0 ) ;
         usered = false ;
         }
      else
         {
         init_color( k, 0 , 0 , 1000 ) ;
         usered = true ;
         }
      k += 8 ;
      }
   }


int main(  int argc , char * argv[] )
   {
   setenv ( "TERM" , "xterm-256color" , 1 ) ;
   char * termname = getenv( "TERM" );

   initscr();
   start_color();

   if (!can_change_color()) {
       printw("can't change colors :(\n");
       refresh();
       sleep(2);
       endwin();
       return 0 ;
   };
   printw("can change colors.\n");
   printw("%d colors, %d pairs available TERM=%s\n",
          COLORS, COLOR_PAIRS, termname ) ;

   bool use2more = false ;  // output 2 additional items
   bool showcpval = true ;
   int startk = 0 ;
   int testwhat = 1 ;
   if ( testwhat == 0 )  // using 256 colours start-cpair 1
      {
      tryuse256cols ( startk , 1 , use2more , showcpval ) ;
      }
   else if ( testwhat == 1 ) // using 256 colours start-cpair 4
      {
      tryuse256cols ( startk , 4 , use2more , showcpval ) ;
      }
   else if ( testwhat == 2 ) // changing colours then show with start-cpair 1
      {
      chgcolours ( argc , argv ) ;
      tryuse256cols ( startk , 1 , use2more , showcpval ) ;
      }

   refresh ( ) ;
   getch ( ) ; //sleep(5);

   endwin();
   return 0 ;
   }

```

The screenshot startcp1.png shows the 256 colours using character-pair (cp) start value 1. The last colour 255 should come out as the lightest of grey but is black. The cp value used is 256.

I then selected cp start value 4 and the outcome is shown by screenshot startcp4.png. The last 4 colours come out with black background.
Screenshot startcp4pxxx.png shows the same with cp value of the item before displayed as white on green background.

These experiments show cp values 256, 257, 258 delivering the wrong output, but the number of COLORPAIRS is 32767. Have I misunderstood this or made  mistakes?

Screenshot chgcolour.png shows the outcome of changing every 8th item in the palette to red or blue alternating and then displaying all colours.
The colour change works, but there are some colour changes that I don't understand. The background colour of the screen has changed to red and the text colour where it should be black has also changed to red. 
Hope someone can explain.

Ken

---

