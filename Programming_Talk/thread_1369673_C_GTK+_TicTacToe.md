---
title: "C GTK+ TicTacToe"
date: 2010-01-01
forum: Programming Talk
---

### Post by lewisforlife on 2010-01-01
I have been working on TicTacToe over the past week.  I am pretty new to C and GTK+ so I am positive I have made a lot of rookie mistakes.  I've almost got the game completed, but I am having trouble clearing the game board after someone wins and was hoping to get some advice on this.  Here is my program.

```

/* main.c */

#include <stdio.h>
#include <string.h>
#include <stdbool.h>
#include <gtk/gtk.h>
#include "close.h"
#include "testwin.h"

int iLocation [2];
char cBoardLoc[3][3] = { {'E', 'E', 'E'}, {'E', 'E', 'E'}, {'E', 'E', 'E'} };
char cTurn = 'X';
GtkWidget *fixed_main;


static gboolean get_x_loc (GtkWidget *widget, GdkEvent *event, gpointer data)
{
    iLocation [0] = (int) data;
    
    return FALSE;
}

static gboolean get_y_loc (GtkWidget *widget, GdkEvent *event, gpointer data)
{
    iLocation [1] = (int) data;
    
    return FALSE;
}

static gboolean make_move (GtkWidget *widget, GdkEvent *event, gpointer data)
{
    bool bWon;
    int x = 0, y = 0;
    int iXPos = 0;
    int iYPos = 0;
    GtkWidget *player;
    GtkWidget *dialog_win, *dialog_invalid;
    char cImgLoc [16] = "./images/";
    strcat (cImgLoc, &cTurn);
    strcat (cImgLoc, ".png");
    
    if (cBoardLoc [iLocation [0]][iLocation [1]] == 'E')
    {
        cBoardLoc [iLocation [0]][iLocation [1]] = cTurn;
    
    
        while (x < iLocation [0])
        {
            
            iXPos += 200;
            x++;
        }
            
        while (y < iLocation [1])
        {
            
            iYPos += 160;
            y++;
        }
            
        player = gtk_image_new_from_file (cImgLoc);
        gtk_fixed_put (GTK_FIXED (fixed_main), player, iXPos, iYPos);
        gtk_widget_show (player);
        
        bWon = check_win (cTurn, cBoardLoc);
        
        if (bWon == true)
        {
            printf ("%c Won the game\n", cTurn);
            
            dialog_win = gtk_message_dialog_new (NULL,
                                                GTK_DIALOG_MODAL,
                                                GTK_MESSAGE_INFO,
                                                GTK_BUTTONS_CLOSE,
                                                "%c has won the game\n", cTurn);
                                                
            //gtk_message_dialog_format_secondary_text (GTK_DIALOG (dialog_win), "test");                        
            gtk_dialog_run (GTK_DIALOG (dialog_win));
            gtk_widget_destroy (dialog_win);
            
          [COLOR=Red]  // code to clear game board[/COLOR]
        }
        else
        {
        
            if (cTurn == 'X')
                cTurn = 'O';
            else
                cTurn = 'X';
        }
            
        
    }
    else
    {
        g_print ("Invalid move!\n");
            dialog_invalid = gtk_message_dialog_new (NULL,
                                                GTK_DIALOG_MODAL,
                                                GTK_MESSAGE_ERROR,
                                                GTK_BUTTONS_CLOSE,
                                                "%c has mad an invalid move, try again!", cTurn);
                                                
            gtk_dialog_run (GTK_DIALOG (dialog_invalid));
            gtk_widget_destroy (dialog_invalid);
    }
    
    
    return TRUE;
}

int main (int argc, char *argv[])
{
    
    int x, y;
    int iXPos = 0;
    int iYPos = 0;
    
    GtkWidget *window_main;
    GtkWidget *image_board;
    GtkWidget *eventbox_main;
        
    gtk_init (&argc, &argv);
    
    window_main = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    g_signal_connect (G_OBJECT (window_main), "delete_event", G_CALLBACK (delete_event), NULL);
    g_signal_connect (G_OBJECT (window_main), "destroy", G_CALLBACK (destroy), NULL);
    gtk_window_set_title (GTK_WINDOW (window_main), "Tic-Tac-Toe");
    
    image_board = gtk_image_new_from_file ("./images/full_board.png");
    
    fixed_main = gtk_fixed_new ();
    gtk_container_add (GTK_CONTAINER (window_main), fixed_main);
    gtk_fixed_put (GTK_FIXED (fixed_main), image_board, 0, 0);
    
    
    for (y = 0; y <= 2; y++)
    {
        for (x = 0; x <= 2; x++)
        {
            eventbox_main = gtk_event_box_new ();
            g_signal_connect (G_OBJECT (eventbox_main), "button_press_event", G_CALLBACK (get_x_loc), (gpointer) x);
            g_signal_connect (G_OBJECT (eventbox_main), "button_press_event", G_CALLBACK (get_y_loc), (gpointer) y);
            g_signal_connect (G_OBJECT (eventbox_main), "button_press_event", G_CALLBACK (make_move), NULL);
            gtk_widget_set_size_request (eventbox_main, 200, 160);
            gtk_fixed_put (GTK_FIXED (fixed_main), eventbox_main, iXPos, iYPos);
            gtk_event_box_set_visible_window (GTK_EVENT_BOX (eventbox_main), FALSE);            
            gtk_widget_show (eventbox_main);
            
            
            iXPos +=200;
        }
        iYPos += 160;
        iXPos = 0;
    }
    
    gtk_widget_show (image_board);
    gtk_widget_show (fixed_main);
    gtk_widget_show (window_main);
    
    gtk_main();


    return 0;
}


```

```

/* close.c */

#include <gtk/gtk.h>
#include "close.h"

gboolean delete_event (GtkWidget *widget, GdkEvent *event, gpointer data)
{
    
    return FALSE;
}

void destroy (GtkWidget *widget, gpointer data)
{
    gtk_main_quit ();
}


```

```

*/ close.h */

gboolean delete_event (GtkWidget *widget, GdkEvent *event, gpointer data);
void destroy (GtkWidget *widget, gpointer data);


```

```

/* testwin.c */

#include <stdio.h>
#include <stdbool.h>
#include "testwin.h"

bool check_win (char cPlayerTurn, char cPlayerBoardLoc [][3])
{
    int x, y, i;
    
    bool bWin = false;
    
    if (bWin == false)
    {
        // check horizontal
        for (y = 0; y <= 2; y++)
        {
            for (x = 0; x <= 2; x++)
            {
                if (cPlayerBoardLoc [x][y] == cPlayerTurn)
                    i++;
            }
            if (i == 3)
            {
                bWin = true;
                break;

            }
            i = 0;
        }
    }
    
    if (bWin == false)
    {
        // check vertical
        for (x = 0; x <= 2; x++)
        {
            for (y = 0; y <= 2; y++)
            {
                if (cPlayerBoardLoc [x][y] == cPlayerTurn)
                    i++;
            }
            if (i == 3)
            {
                bWin = true;
                break;
            }
            i = 0;
        }
    }
    
    if (bWin == false)
    {
        // check horiz right
        for (x = 0; x <= 2; x++)
        {
            if (cPlayerBoardLoc [x][x] == cPlayerTurn)
            {
                i++;
                if (i == 3)
                {
                    bWin = true;
                    break;
                }
            }
        }
        
        i = 0;
    }
    
    if (bWin == false)
    {
        // check horiz left
        for (x = 2; x >= 0; x--)
        {
            if (cPlayerBoardLoc [x][x] == cPlayerTurn)
            {
                i++;
                if (i == 3)
                {
                    bWin = true;
                    break;
                }
            }
        }
    }
    return bWin;
    
}


```

```

/* testwin.h */

bool check_win (char cPlayerTurn, char cPlayerBoardLoc [][3]);


```

I have hilighted the comment in red in main.c where the gameboard code to clear it would be, or it would be a function call to clear the game board.  Any help would be much appreciated.  Also, there are 3 images that are needed, they need to go in /directory/game/is/in/images.  I have attached the images.

Thanks.

---

### Post by wmcbrine on 2010-01-01
This would be easier for others to test if you bundled up your source files, image files and makefile, and posted the archive. (Not that you shouldn't *also* have posted them inline -- that was good that you did that, too.)

---

### Post by lewisforlife on 2010-01-01
> **wmcbrine said:**
> This would be easier for others to test if you bundled up your source files, image files and makefile, and posted the archive. (Not that you shouldn't *also* have posted them inline -- that was good that you did that, too.)

That would make it easier wouldn't it :P

---

### Post by lewisforlife on 2010-01-01
Like I said, I am pretty new to C programming, I think I might have found my solution to my problem.  The reason I was having a problem clearing my board is because I didn't know how to write a function to reset all of my variables because some of my variables were initialized in main () so I didn't know how to reset them from a different function.  I think my solutions is to use pointers though:
```

#include <stdio.h>

void test_function (int *b)
{
  *b = 15;
}

int main (int argc, char *argv[])
{
  int a = 10;

  printf ("a = %d\n", a);

  test_function (&a);

  printf ("a = %d\n", a);

  return 0;
}
```

This demonstrates how to change a variable in a function that it was not initialised in, so I think this is what I will have to do to reset my tictactoe game board.  Please still feel free to comment and give suggestions though.

thanks.

---

### Post by lewisforlife on 2010-01-02
I finished my TicTacToe project, I figured I would post it in case anyone that has helped me was curious about it's progress.  I am releasing it under the GNU/GPL ver 3.

There are a lot of amateurish things that I have done in this project, but have learned a lot and am planning on fixing these mistakes in my future projects with a lot more planning and better programming structure.

---

### Post by lewisforlife on 2010-01-02
Oh yeah, one more thing, I don't really know how to do a Makefile, is there any good tutorials out there.  Here is how I compile this program.

```
gcc -Wall main.c initboard.c testwin.c close.c -o tictactoe `pkg-config --cflags --libs gtk+-2.0`
```What would the Makefile look like to do this same thing?

---

### Post by dwhitney67 on 2010-01-02
Here's a Makefile you could use; note, this is the most basic of Makefiles -- so feel free to augment it if you like.
```

# your application's name
APP = tictactoe

# list of source files
SRCS = main.c initboard.c testwin.c close.c

# convert source file names to object file names
OBJS = $(SRCS:.c=.o)

# flags used to compile
CFLAGS = -Wall `pkg-config --cflags gtk+-2.0`

# flags used to link
LDFLAGS = `pkg-config --libs gtk+-2.0`

.PHONY: clean


# Link the application
$(APP) : $(OBJS)
        $(CC) $^ $(LDFLAGS) -o $@

# Utility to clean up
clean :
        $(RM) $(OBJS)
        $(RM) $(APP)

```

P.S.  Statements that follow rules (eg. $(APP) or clean) are indented using a single tab-space.  Do not use spaces, or the Makefile won't work.

---

