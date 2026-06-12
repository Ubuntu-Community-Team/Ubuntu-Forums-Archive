---
title: "[SOLVED] GTK - Correct callback data parameter?"
date: 2008-02-19
forum: Programming Talk
---

### Post by montgoss on 2008-02-19
I'm trying to pass some data through to a callback and I'm getting weird behavior.  I have the type SudokuTile that has a member called "id".  I'm trying to pass a pointer to a SudokuTile (one tile out of an array of them) into the callback.  Right now, I'm just printing out the id to test.  It's almost always 4.  If I click the label fast enough, I can get some 5's and 6's in there too, but mostly 4...   :? 

So, what should go on Line 190-191 below (the call to g_signal_connect)?

```
/*
 * This program is free software; you can redistribute it and/or modify it under
 * the terms of the GNU General Public License as published by the Free Software
 * Foundation; either version 2 of the License, or (at your option) any later
 * version.
 *
 * This program is distributed in the hope that it will be useful, but WITHOUT
 * ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
 * FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more
 * details.
 *
 * You should have received a copy of the GNU General Public License along with
 * this program; if not, write to the Free Software Foundation, Inc., 51
 * Franklin St, Fifth Floor, Boston, MA 02110-1301 USA
 */

#include <gtk/gtk.h>
#include "stdio.h"

/*--------------------------------------------------------------------------------------------------*/
/* type definitions */
/*--------------------------------------------------------------------------------------------------*/

typedef struct
{
    unsigned int id;
    GtkWidget *mBoardWidget;
    GtkWidget *mLabelBox;
    GtkWidget *mEventBox;
    GtkWidget *mTileLabel1;
    GtkWidget *mTileLabel2;
    GtkWidget *mTileLabel3;
    gboolean editable;
    gboolean penciled;
    unsigned int color;
    short the_value;
    gboolean values[9];
} SudokuTile;

/*--------------------------------------------------------------------------------------------------*/
/* signal callbacks */
/*--------------------------------------------------------------------------------------------------*/

static void new_button_cb (GtkWidget * button, gpointer data);

static void check_button_cb (GtkWidget * button, gpointer data);

static void reset_button_cb (GtkWidget * button, gpointer data);

static void pause_button_cb (GtkWidget * button, gpointer data);

static void tile_button_cb (GtkWidget * button, gpointer tile_data);

static void popup_button_cb (GtkWidget * button, Popup * data);

void init_puzzle(void);

/*--------------------------------------------------------------------------------------------------*/
/* data */
/*--------------------------------------------------------------------------------------------------*/

GtkWidget *window; // main window

/* globals */
static SudokuTile mBoardTiles[81];

unsigned long mPuzzleID;
unsigned int mCurPuzzleRating;


/*--------------------------------------------------------------------------------------------------*/
/* main program */
/*--------------------------------------------------------------------------------------------------*/

int main (int argc, char **argv)
{
    GtkWidget *notebook, *icon;
    GtkWidget *box, *toolbar, *table, *details, *navigation, *w;
    GtkWidget *vsep, *hsep;
    GtkTreeViewColumn *column;
    GtkWidget *widget;
    GtkRcStyle *tile_style;
    GdkColor tile_color_blk = {0, 0, 0, 0};
    GtkToolItem *toolitem;
    GtkListStore *liststore;
    GtkTreeIter it;
    SudokuTile *data;
    
    unsigned int index;

    gtk_init (&argc, &argv);

    /* main window */
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    g_signal_connect (G_OBJECT (window), "delete-event",
                        (GCallback) gtk_main_quit, NULL);
    gtk_window_set_title (GTK_WINDOW (window), "Sudoku");

    /* main notebook */
    notebook = gtk_notebook_new ();
    gtk_container_add (GTK_CONTAINER (window), notebook);
    gtk_notebook_set_tab_pos (GTK_NOTEBOOK (notebook), GTK_POS_BOTTOM);

    /* navigation */
    box = gtk_vbox_new (FALSE, 0);
    gtk_notebook_append_page (GTK_NOTEBOOK (notebook), box,
                                gtk_image_new_from_stock (GTK_STOCK_INDEX,
                                                        GTK_ICON_SIZE_LARGE_TOOLBAR));
    gtk_container_child_set (GTK_CONTAINER (notebook), box, "tab-expand",
                            TRUE, NULL);


    /* puzzle board */
    table = gtk_table_new( 11, 11, FALSE );
    gtk_box_pack_start (GTK_BOX (box), table, FALSE, FALSE, 0);
    hsep = gtk_hseparator_new();
    gtk_table_attach( GTK_TABLE(table),
                      hsep,
                      0,
                      11,
                      3,
                      4,
                      GTK_SHRINK | GTK_FILL,
                      GTK_SHRINK | GTK_FILL,
                      0,
                      0 );
    hsep = gtk_hseparator_new();
    gtk_table_attach( GTK_TABLE(table),
                      hsep,
                      0,
                      11,
                      7,
                      8,
                      GTK_SHRINK | GTK_FILL,
                      GTK_SHRINK | GTK_FILL,
                      0,
                      0 );

    vsep = gtk_vseparator_new();
    gtk_table_attach( GTK_TABLE(table),
                        vsep,
                        3,
                        4,
                        0,
                        11,
                        GTK_SHRINK | GTK_FILL,
                        GTK_SHRINK | GTK_FILL,
                        0,
                        0 );
    vsep = gtk_vseparator_new();
    gtk_table_attach( GTK_TABLE(table),
                        vsep,
                        7,
                        8,
                        0,
                        11,
                        GTK_SHRINK | GTK_FILL,
                        GTK_SHRINK | GTK_FILL,
                        0,
                        0 );
    for( index = 0; index < 81; index++ )
    {
        mBoardTiles[index].id = index;

        mBoardTiles[index].mBoardWidget = gtk_frame_new(NULL);
       
        mBoardTiles[index].mTileLabel1 = gtk_label_new( "123" );
        mBoardTiles[index].mTileLabel2 = gtk_label_new( "456" );
        mBoardTiles[index].mTileLabel3 = gtk_label_new( "789" );
        gtk_label_set_markup( GTK_LABEL(mBoardTiles[index].mTileLabel1),
                                "<span size=\"x-small\">123</span>");
        gtk_label_set_markup( GTK_LABEL(mBoardTiles[index].mTileLabel2),
                                "<span size=\"x-small\">456</span>");
        gtk_label_set_markup( GTK_LABEL(mBoardTiles[index].mTileLabel3),
                                "<span size=\"x-small\">789</span>");

        gtk_widget_set_size_request( mBoardTiles[index].mTileLabel1, 24, 10);
        gtk_widget_set_size_request( mBoardTiles[index].mTileLabel2, 24, 10);
        gtk_widget_set_size_request( mBoardTiles[index].mTileLabel3, 24, 10);
        mBoardTiles[index].mLabelBox =  gtk_vbox_new( TRUE, 0);
        gtk_container_add( GTK_CONTAINER(mBoardTiles[index].mLabelBox), mBoardTiles[index].mTileLabel1 );
        gtk_container_add( GTK_CONTAINER(mBoardTiles[index].mLabelBox), mBoardTiles[index].mTileLabel2 );
        gtk_container_add( GTK_CONTAINER(mBoardTiles[index].mLabelBox), mBoardTiles[index].mTileLabel3 );
       
        mBoardTiles[index].mEventBox = gtk_event_box_new();
        gtk_container_add( GTK_CONTAINER(mBoardTiles[index].mEventBox), mBoardTiles[index].mLabelBox );
       
        gtk_container_add( GTK_CONTAINER(mBoardTiles[index].mBoardWidget), mBoardTiles[index].mEventBox );

        g_signal_connect( G_OBJECT(mBoardTiles[index].mEventBox), "button_press_event",
                          (GCallback)tile_button_cb, (gpointer)(&mBoardTiles[index]) );

        gtk_table_attach( GTK_TABLE(table),
                          mBoardTiles[index].mBoardWidget,
                          (index%9)+((index/3)%3),
                          ((index%9)+((index/3)%3)+1),
                          (index/9)+(index/27),
                          ((index/9)+(index/27)+1),
                          GTK_SHRINK | GTK_FILL,
                          GTK_SHRINK | GTK_FILL,
                          0,
                          0 );
    }

    
    /* let's go! */
    gtk_widget_show_all (window);
    gtk_main ();

    return 0;
}

/*--------------------------------------------------------------------------------------------------*/
/* signal callbacks */
/*--------------------------------------------------------------------------------------------------*/

static void new_button_cb (GtkWidget * button, gpointer data)
{ 
    printf("new_button_cb\n");
    init_puzzle();
}

/*--------------------------------------------------------------------------------------------------*/

static void check_button_cb (GtkWidget * button, gpointer data)
{
    printf("check_button_cb\n");
}

/*--------------------------------------------------------------------------------------------------*/

static void reset_button_cb (GtkWidget * button, gpointer data)
{
    printf("reset_button_cb\n");
}

/*--------------------------------------------------------------------------------------------------*/

static void pause_button_cb (GtkWidget * button, gpointer data)
{
    printf("pause_button_cb\n");
}

/*--------------------------------------------------------------------------------------------------*/

static void tile_button_cb (GtkWidget * button, gpointer tile_data)
{
    SudokuTile *this_tile = (SudokuTile *)tile_data;

    printf("id = %d\n", this_tile->id);
}
 
```

---

### Post by lnostdal on 2008-02-19
if no one else answer this for you i can take a look, but i'm tired today =) .. could you post only the *minimum* (working) code required to trigger your problem?

---

### Post by montgoss on 2008-02-19
> **lnostdal said:**
> if no one else answer this for you i can take a look, but i'm tired today =) .. could you post only the *minimum* (working) code required to trigger your problem?

There's not much superfluous there.  And I'm not actually sure what the problem is.  Maybe it's related to my layout or placement?  I haven't tested the following, but I believe it would be the minimum amount of code to see the behavior I'm referring to.

```
#include <gtk/gtk.h>
#include "stdio.h"

/*--------------------------------------------------------------------------------------------------*/
/* type definitions */
/*--------------------------------------------------------------------------------------------------*/

typedef struct
{
    unsigned int id;
    GtkWidget *mBoardWidget;
    GtkWidget *mLabelBox;
    GtkWidget *mEventBox;
    GtkWidget *mTileLabel1;
    GtkWidget *mTileLabel2;
    GtkWidget *mTileLabel3;
    gboolean editable;
    gboolean penciled;
    unsigned int color;
    short the_value;
    gboolean values[9];
} SudokuTile;

/*--------------------------------------------------------------------------------------------------*/
/* signal callbacks */
/*--------------------------------------------------------------------------------------------------*/

static void tile_button_cb (GtkWidget * button, gpointer tile_data);

/*--------------------------------------------------------------------------------------------------*/
/* data */
/*--------------------------------------------------------------------------------------------------*/

GtkWidget *window; // main window

/* globals */
static SudokuTile mBoardTiles[81];


/*--------------------------------------------------------------------------------------------------*/
/* main program */
/*--------------------------------------------------------------------------------------------------*/

int main (int argc, char **argv)
{
    GtkWidget *box, *toolbar, *table, *details, *navigation, *w;
    GtkWidget *vsep, *hsep;
    GtkWidget *widget;
    
    unsigned int index;

    gtk_init (&argc, &argv);

    /* main window */
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    g_signal_connect (G_OBJECT (window), "delete-event",
                        (GCallback) gtk_main_quit, NULL);
    gtk_window_set_title (GTK_WINDOW (window), "Sudoku");


    /* puzzle board */
    table = gtk_table_new( 11, 11, FALSE );
    gtk_container_add (GTK_CONTAINER (window), table);

    hsep = gtk_hseparator_new();
    gtk_table_attach( GTK_TABLE(table),
                      hsep,
                      0,
                      11,
                      3,
                      4,
                      GTK_SHRINK | GTK_FILL,
                      GTK_SHRINK | GTK_FILL,
                      0,
                      0 );
    hsep = gtk_hseparator_new();
    gtk_table_attach( GTK_TABLE(table),
                      hsep,
                      0,
                      11,
                      7,
                      8,
                      GTK_SHRINK | GTK_FILL,
                      GTK_SHRINK | GTK_FILL,
                      0,
                      0 );

    vsep = gtk_vseparator_new();
    gtk_table_attach( GTK_TABLE(table),
                        vsep,
                        3,
                        4,
                        0,
                        11,
                        GTK_SHRINK | GTK_FILL,
                        GTK_SHRINK | GTK_FILL,
                        0,
                        0 );
    vsep = gtk_vseparator_new();
    gtk_table_attach( GTK_TABLE(table),
                        vsep,
                        7,
                        8,
                        0,
                        11,
                        GTK_SHRINK | GTK_FILL,
                        GTK_SHRINK | GTK_FILL,
                        0,
                        0 );
    for( index = 0; index < 81; index++ )
    {
        mBoardTiles[index].id = index;

        mBoardTiles[index].mBoardWidget = gtk_frame_new(NULL);
       
        mBoardTiles[index].mTileLabel1 = gtk_label_new( "123" );
        mBoardTiles[index].mTileLabel2 = gtk_label_new( "456" );
        mBoardTiles[index].mTileLabel3 = gtk_label_new( "789" );
        gtk_label_set_markup( GTK_LABEL(mBoardTiles[index].mTileLabel1),
                                "<span size=\"x-small\">123</span>");
        gtk_label_set_markup( GTK_LABEL(mBoardTiles[index].mTileLabel2),
                                "<span size=\"x-small\">456</span>");
        gtk_label_set_markup( GTK_LABEL(mBoardTiles[index].mTileLabel3),
                                "<span size=\"x-small\">789</span>");

        gtk_widget_set_size_request( mBoardTiles[index].mTileLabel1, 24, 10);
        gtk_widget_set_size_request( mBoardTiles[index].mTileLabel2, 24, 10);
        gtk_widget_set_size_request( mBoardTiles[index].mTileLabel3, 24, 10);
        mBoardTiles[index].mLabelBox =  gtk_vbox_new( TRUE, 0);
        gtk_container_add( GTK_CONTAINER(mBoardTiles[index].mLabelBox), mBoardTiles[index].mTileLabel1 );
        gtk_container_add( GTK_CONTAINER(mBoardTiles[index].mLabelBox), mBoardTiles[index].mTileLabel2 );
        gtk_container_add( GTK_CONTAINER(mBoardTiles[index].mLabelBox), mBoardTiles[index].mTileLabel3 );
       
        mBoardTiles[index].mEventBox = gtk_event_box_new();
        gtk_container_add( GTK_CONTAINER(mBoardTiles[index].mEventBox), mBoardTiles[index].mLabelBox );
       
        gtk_container_add( GTK_CONTAINER(mBoardTiles[index].mBoardWidget), mBoardTiles[index].mEventBox );

        g_signal_connect( G_OBJECT(mBoardTiles[index].mEventBox), "button_press_event",
                          (GCallback)tile_button_cb, (gpointer)(&mBoardTiles[index]) );

        gtk_table_attach( GTK_TABLE(table),
                          mBoardTiles[index].mBoardWidget,
                          (index%9)+((index/3)%3),
                          ((index%9)+((index/3)%3)+1),
                          (index/9)+(index/27),
                          ((index/9)+(index/27)+1),
                          GTK_SHRINK | GTK_FILL,
                          GTK_SHRINK | GTK_FILL,
                          0,
                          0 );
    }

    
    /* let's go! */
    gtk_widget_show_all (window);
    gtk_main ();

    return 0;
}

/*--------------------------------------------------------------------------------------------------*/
/* signal callbacks */
/*--------------------------------------------------------------------------------------------------*/

static void tile_button_cb (GtkWidget * button, gpointer tile_data)
{
    SudokuTile *this_tile = (SudokuTile *)tile_data;

    printf("id = %d\n", this_tile->id);
}

```

---

### Post by lnostdal on 2008-02-19
ok then .. replace with this:
```
...
static void tile_button_cb(GtkWidget* button, GdkEventButton* event, gpointer tile_data)
...

```

---

### Post by montgoss on 2008-02-19
That did it.  Thanks!

---

