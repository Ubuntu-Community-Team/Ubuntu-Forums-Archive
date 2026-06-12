---
title: "Gtk 3"
date: 2012-02-17
forum: Programming Talk
---

### Post by anewguy on 2012-02-17
I've posted in the gtk forum I know about, but I'm having some problems with something using C and GTK 3.  In particular, I'm building an application to modify several things for the easier configuration of another application.  I have several places where the color needs to be selected for various objects.  I have used gtk_label_new to create labels for each, then I want to display the default color (and when it is changed) in each of those labels.  I tried several things which did not work, including some from the net that appear not to be supported in that form in GTK 3.  I found gtk_wdget_override_color and gtk_widget_overrid_background_color in the GTK 3 documentation.  I have used them with no change.  Examples from my code are:

.
.
.
.
     GdkColor col;
     GtkWidget *panel_current_color;
     GtkWidget *panel_current_color;
.
.  These widgets are declared globaly so it can be changed in a couple of routines while the rest are local, including the window and table.
,
,
,
,
panel_current_color = gtk_button_new_with_label("Current Color");
.
.  Above defined once in a single function
.
.
.
.
gtk_widget_override_color(panel_current_color, GTK_STATE_NORMAL, &col);
gtk_widget_override_background_color(panel_current_color, GTK_STATE_NORMAL, &col);
.
.   Above used in 2 functions
.
.


The result is always the same - I have a box showing on the screen for the label with "Current Color" showing in black, but the box itself remains the default color of the screen.  col is what is return from the color wheel.

Any help would be greatly appreciated!!

Thanks in advance!

Dave ;)

---

### Post by anewguy on 2012-02-18
Okay, more info.  I found out that when it is a gtkbox with text in it (label), you have to modify the base color.  I modified the program for that and still no difference.

Dave ;)

---

### Post by anewguy on 2012-02-18
Even though the GTK 3 documentation says the colors are modifiable, they also note that "some" of the widgets can be modified in that way.  They suggest making it a label, putting the label in an event box and then changing the color of the event box.  I've done that - nothing changes and now I can't even see the text of the label.

Where or where is **GOOD** documentation for GTK 3???????????????

---

### Post by MG&amp;TL on 2012-02-19
> **anewguy said:**
> Even though the GTK 3 documentation says the colors are modifiable, they also note that "some" of the widgets can be modified in that way.  They suggest making it a label, putting the label in an event box and then changing the color of the event box.  I've done that - nothing changes and now I can't even see the text of the label.

Where or where is **GOOD** documentation for GTK 3???????????????

Well, I can't help, but I have to say I agree with you. Gtk's docs are awful for newbies to their system. 

Another point-have you considered a different language, or is C a necessity? I find vala/python better for gtk at the moment ([http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html](http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html) and [http://valadoc.org/gtk+-3.0/index.htm](http://valadoc.org/gtk+-3.0/index.htm))

So no help, but sympathy. Hope you get it eventually. UI programming is a pain.

---

### Post by pbrane on 2012-02-19
Can you post more of your code? It seems you may be missing something. I write apps in gtkmm-3.0 and I have no problems changing colors. I'm not sure exactly what you are trying to accomplish, but a simple color selection button will allow you to select and change colors and also will display the currently selected color.

EDIT: It may be that you are trying to use GdkColor instead of GdkRGBA. Here is an example from one of your previous posts using the ZetCode example. I modified it to work with Gtk+-3.0.
```

void select_font(GtkWidget *widget, gpointer label)
{

  GtkResponseType result;
  GtkColorSelection *colorsel;

  GtkWidget *dialog = gtk_color_selection_dialog_new("Font Color");
  result = gtk_dialog_run(GTK_DIALOG(dialog));

  if (result == GTK_RESPONSE_OK)
  {

    GdkRGBA color;

    GtkWidget *colorSelection;

    colorSelection = gtk_color_selection_dialog_get_color_selection(GTK_COLOR_SELECTION_DIALOG(dialog));

    gtk_color_selection_get_current_rgba(GTK_COLOR_SELECTION(colorSelection), &color);
    
    gtk_widget_override_color(GTK_WIDGET(label), GTK_STATE_NORMAL, &color);
  } 

  gtk_widget_destroy(dialog);
}

```

I compiled with
```

gcc -o color-test color-test.c $(pkg-config --cflags --libs gtk+-3.0)

```

Gtk+-3.0 is using Cairo for drawing now, GdkColor uses guints (0 to 65535) and GdkRGBA uses doubles (0.0 to 1.0) for colors. Cairo expects doubles.

---

### Post by anewguy on 2012-02-19
I'm already doing what you have posted - the problem is the color is not changing with the gtk_widget_override_color (or in my background color).  I've traced the color before the call for the wheel, what is selected on the wheel and still no update.

Someplace along the line it "magically" started just making all the backgrounds black.  I have no reference to black, it's hex representation or the rgb 0-255 values instead of their hex values.  I had to load the code from a backup, and am now trying to catch it back up.

The program is writing out a CSS file and also needs the fractional representation of the alpha.  I already know how to strip the values from the string, but the alpha value is always a large integer. As best as I can tell, CSS needs it to be in the range of 0 to 1 (like the opacity shows on the color selection wheel).  So I guess I also need to try the GdkRGBA thing in place of GdkColor in order to get the alpha I need.

Also note that I have to use gtk_color_parse to load a GdkColor from the hex RR GG BB values as well as translate an alpha frational representation back into the long integer value.  gtk_color_parse does not work with a GdkRGBA widget (at least the compiler fatals out on this with me).  So I still have no true way to get the alpha fractional value that I can see.

---

### Post by pbrane on 2012-02-19
> **anewguy said:**
> .....
Also note that I have to use gtk_color_parse to load a GdkColor from the hex RR GG BB values as well as translate an alpha frational representation back into the long integer value.  gtk_color_parse does not work with a GdkRGBA widget (at least the compiler fatals out on this with me).  So I still have no true way to get the alpha fractional value that I can see.

You want to use the gdk_rgba_xx functions, such as gdk_rgba_parse(). the gdk_color_xx functions don't seem to work for me.

---

### Post by anewguy on 2012-02-19
That would sure explain why I keep having problems.  I never knew about the gdkrgba things - I hardly know anything about gtk so I've just been trying to follow the online docs I could find.

The rgba looks very promising, as the best I can tell (and I don't know CSS either ;) ) the output CSS file uses colors in a #xxxxxx format, #xxxxxxxxxxxx format, rgb format and rbga where it appears the r, b and g values are 0-255 and the alpha is the 0 to 1 fraction.  So, rgba seems to be a good fit for it.  I just need to read up on the rgba stuff and experiment a little to see how it works.  My C is extremely rusty at best, so all in all this makes for a very challenging project for me, and I'm not afraid of looking like a complete idiot! ;)  I just need information like you are providing!

Thank you!

Dave ;)

---

### Post by pbrane on 2012-02-20
If you're out-putting to CSS then you should be able to use the **gdk_rgba_to_string** function to create a CSS3 compliant string from the rgba color.

Having devhelp installed with all the development docs can be a big help.

---

### Post by anewguy on 2012-02-20
Thanks again!  I'll get that help thing figured out and installed as well, and if you don't mind, could you point me to what you're talking about?

You've been a great help for me - thank you!

Dave ;)

---

### Post by pbrane on 2012-02-20
devhelp is a help program that will display help files from libraries like Gtk+-3.0 Cairo, etc. I used synaptic package manager to install the *-doc files for Gtk, Gtkmm, Cairo and others. All the document files should end in -doc. You should be able to install devhelp and the gtk-3 docs with this command.
```

sudo apt-get install devhelp lib-gtk-3-doc

```
You can browse the synaptic package manager for other -doc files that you may want to install as well.

---

### Post by anewguy on 2012-02-20
Thanks for the info on the help - now I'll have something easier to deal with.  I've sure been learning a lot which really does help me.

You'll have to excuse the printf's to trace things - I come from the old school, and I haven't been able to figure out how to insert my source into codeblocks (it's a single C file, not broken out into main, other functions, etc.).

Well, I'm still not getting a color change. What I think are the significant parts of the code regarding this are:

Before any functions:

```
/*
          Variable definitions
*/

     GdkRGBA col;
     GdkRGBA wrkcol;
     guint16 color_alpha = 255;

     char color_RR[3];
     char color_GG[3];
     char color_BB[3];
     char color_OPACITY[] = "255";

     int has_opacity = FALSE;
     int max_win_length;
     int max_win_height;
     int returned = TRUE;

     char text_get_color[256];
     char col_str[256];


/* 
          GTK  variables
*/

     GtkWindow *opening_window;
     GtkWidget *vbox0;
     GtkWidget *vbox1;
     GtkWidget *vbox2;
     GtkWidget *vbox3;
     GtkWidget *vbox4; 
     GtkWidget *label1;
     GtkWidget *label2;
     GtkWidget *label3;
     GtkWidget *hbox1;
     GtkWidget *hbox2;
     GtkWidget *hbox3;
     GtkWidget *hbox4;
     GtkWidget *hbox5;
     GtkWidget *hbox6;
     GtkWidget *hbox7;
     GtkWidget *hbox8;
     GtkWidget *open_existing;
     GtkWidget *new_file;
     GtkWidget *save_file;
     GtkWidget *panel_selected;
     GtkWidget *panel_win1;
     GtkWidget *panel_transparent_text;
     GtkWidget *panel_current_color;


/***************************************************************/
/*   Begin defining gnome-shell.css variables.  These are used */
/*   to default selections and to build the final css file.    */
/***************************************************************/

     char *css_panel_color_RGBA;
     char css_panel_background_color[256] = "#000000";
     int panel_background_image_active = FALSE;
     int panel_background_color_active = FALSE;

```

Function defining main screen - note that the color is not changing on the first label when I set it:
```
/***************************************************************
            Panel Selection Options

  This routine shows the Panel items selection screen and 
  processes requests.

****************************************************************/

void panel_options()
{

     GtkWidget *wrkbox1;
     GtkWidget *wrkbutton1;
     GtkWidget *wrkbox2;
     GtkWidget *wrkbutton2;
     GtkWidget *divid1;
     GtkWidget *table1;
     GtkWidget *label2;
     GtkWidget *label3;
     GtkWidget *label4;
     GtkWidget *label5;
     GtkWidget *label6;
     GtkWidget *label7;
     GtkWidget *label8;
     GtkWidget *label9;
     GtkWidget *label10;
     GtkWidget *table11;
     GtkWidget *label12;
     GtkWidget *label13;
     GtkWidget *label14;
     GtkWidget *label15;
     GtkWidget *label16;
     GtkWidget *label17;
     GtkWidget *label18;
     GtkWidget *label19;
     GtkWidget *label20;
     GtkWidget *button1;
     GdkColor   colorButton;
     GtkWidget *button_Widget;

     GSList *group1;


     int wrki_1 = 0;
     int wrki_2 = 0;

     char wrkstr1[700]; 


     panel_win1 = gtk_window_new (GTK_WINDOW_TOPLEVEL);
     gtk_window_set_title (GTK_WINDOW(panel_win1), "GNOME SHELL CSS FILE EDITOR - PANEL OPTIONS");
     gtk_window_set_default_size(GTK_WINDOW(panel_win1), 640, 480);
     gtk_window_set_position (GTK_WINDOW(panel_win1), GTK_WIN_POS_CENTER);
     g_signal_connect (G_OBJECT (panel_win1), "delete_event",
                       G_CALLBACK (close_window), GTK_CONTAINER(panel_win1));
     g_signal_connect (G_OBJECT (panel_win1), "destroy",
                       G_CALLBACK (close_window), GTK_CONTAINER(panel_win1));


     gtk_container_set_border_width (GTK_CONTAINER(panel_win1), 5);

     wrkbox1 = gtk_vbox_new(FALSE, 5);
     gtk_container_add (GTK_CONTAINER (panel_win1), wrkbox1);
     
     table1 = gtk_table_new(15,10,TRUE);
     label1 = gtk_label_new("Panel Color:");
     label2 = gtk_label_new("Background:");
printf("At rgba parse\n");
/*     if (FALSE == gdk_rgba_parse ( &col,css_panel_color_RGBA))
     {
         do_message("ERROR","UNABLE TO PARSE PANEL COLOR");
     }  */
gdk_rgba_parse(&col,"#adadf7f7f7f7");
printf("Define panel color\n");
     panel_current_color = gtk_button_new_with_label("Current Color");
printf("Override the colors\n");
     gtk_widget_override_color(GTK_WIDGET(panel_current_color), GTK_STATE_NORMAL, &col);
     gtk_widget_override_background_color(GTK_WIDGET(panel_current_color), GTK_STATE_NORMAL, &col);
     g_signal_connect (G_OBJECT (panel_current_color), "pressed",
                  G_CALLBACK (panel_color_get), NULL);


     panel_background_image_active =  gtk_radio_button_new(NULL);
     panel_background_color_active = gtk_radio_button_new(NULL);
     gtk_radio_button_join_group( panel_background_color_active, panel_background_image_active);
     gtk_toggle_button_set_active (GTK_RADIO_BUTTON (panel_background_color_active), TRUE); 

     label3 = gtk_label_new("Image:");
     label4 = gtk_label_new("Color:");


 
printf("Start building screen table\n");
     gtk_table_attach (GTK_TABLE(table1), label1, 0,1,0,1,
                       GTK_EXPAND, GTK_SHRINK, 0, 0);
     gtk_table_attach (GTK_TABLE(table1), panel_current_color, 1,3,0,1,
                       GTK_EXPAND, GTK_SHRINK, 0, 0);
     gtk_table_attach (GTK_TABLE(table1), label2, 0,1,1,2,
                       GTK_EXPAND, GTK_SHRINK, 0, 0);
     gtk_table_attach (GTK_TABLE(table1),
                       panel_background_image_active,
                       1,2,1,2,
                       GTK_EXPAND,
                       GTK_SHRINK,
                       0, 0);
     gtk_table_attach (GTK_TABLE(table1),
                       panel_background_color_active,
                       1,2,2,3,
                       GTK_EXPAND,
                       GTK_SHRINK,
                       0, 0);
     gtk_table_attach (GTK_TABLE(table1), label3, 2,3,1,2,
                       GTK_EXPAND, GTK_SHRINK, 0, 0);
     gtk_table_attach (GTK_TABLE(table1), label4, 2,3,2,3,
                       GTK_EXPAND, GTK_SHRINK, 0, 0);

     gtk_table_set_row_spacings (GTK_TABLE(table1),3);
     gtk_table_set_col_spacings (GTK_TABLE(table1),3);

     gtk_container_add(GTK_CONTAINER(wrkbox1), table1);

     gtk_widget_show(table1);
     



     gtk_widget_hide (opening_window);
     gtk_widget_show_all(panel_win1);
     return;
/*

    padding-bottom: .15em;
    background-gradient-direction: vertical;
    background-gradient-start: rgba(0,100,0,0.9); 
    background-gradient-end: rgba(0,0,0,0.9);
    color: rgba(221,187,102,1.0); 
    border: .05em solid transparent rgba(93,252,10,0.3);
    border-top: 0px;
    border-left: 0px;
    border-right: 0px;
    height: 1.4em;
    box-shadow: 0px 5px 10px rgba(93,252,10,0.2); 
    font-size: 1.1em;
    font-weight: bold italic;
    font-family: Magik, MintSpirit, cantarell, ubuntu, serif;
    text-align: center;

*/

}


```

In addition, I'm still left in a quandry with the opacity.  The only color selection tools I could find for GTK still return the alpha in a long integer value (double?).  I still don't know how to convert that back to a fractional equivalent or do the reverse.  The code I use to allow color selection is pretty much a copy from the net.  Note that the get of the opacity alpha has been taken out for now until I find out how to do conversions.  I can't hardly put something like 65001 in a rgba string for CSS from what I've seen.  Significant code snippet follows:

```

/**************************************************************/
/*                 get_color.c                                */
/*                                                            */
/*  Displays the color selection wheel and return selection.  */
/**************************************************************/


int get_color()

{

/*– Declare the GTK Widgets used  –*/

     GtkWidget* cdialog = NULL;
     GtkWidget* sel;


/*- Variable Definitions  -*/

     gint response1;
     int result_1 = FALSE;


/*- Define and start the color selection dialog  -*/

     cdialog = gtk_color_selection_dialog_new(text_get_color);

/* set default color to current color passed on call */

     sel=gtk_color_selection_dialog_get_color_selection(GTK_COLOR_SELECTION_DIALOG(cdialog));
     gtk_color_selection_set_current_color (GTK_COLOR_SELECTION(sel),&col); 
     gtk_color_selection_set_has_opacity_control (GTK_COLOR_SELECTION(sel),
                                                  TRUE);
     gtk_color_selection_set_current_alpha(GTK_COLOR_SELECTION(sel), color_alpha);

/*     gtk_widget_show (cdialog); */
     response1 = gtk_dialog_run (GTK_DIALOG(cdialog));

/*- Handle response from color selection -*/

     if (response1 == GTK_RESPONSE_OK)
     {
          gtk_color_selection_get_current_color (GTK_COLOR_SELECTION(sel),&col);
          sprintf(col_str,"%s",gdk_color_to_string(&col));
printf("selected color as string: %s\n",col_str);
/*           strncpy(color_RR, col_str+1, 2);
          strncpy(color_GG, col_str+5, 2);
          strncpy(color_BB, col_str+9, 2);
          result_1 = TRUE;  */
     }
     else
     {
          result_1 = FALSE;
     }

/* destroys the dialog */
    gtk_widget_destroy(cdialog); 


    return result_1;
}

```

Maybe I should just give up and tell everyone who wanted the tool that I've failed, as I seem to be getting nowhere on what seems like something that should be extremely easy.

The resulting screen is in the attachment - notice there is no color even though I set it to yellow - at least I *thought* I did ;)

---

### Post by MG&amp;TL on 2012-02-20
> **anewguy said:**
> 
You'll have to excuse the printf's to trace things - I come from the old school, and I haven't been able to figure out how to insert my source into codeblocks (it's a single C file, not broken out into main, other functions, etc.).


In the unlikely event that you want to remove your printf clauses (I like them too!), gdb is a good option. Compile with the -ggdb flag and then:

```
gdb yourapp
```

There's much better tutorials on the web for gdb than I can say here.

---

### Post by pbrane on 2012-02-20
```

if (response1 == GTK_RESPONSE_OK)
     {
          gtk_color_selection_get_current_**rgba** (GTK_COLOR_SELECTION(sel),&col);
          sprintf(col_str,"%s",gdk_**rgba**_to_string(&col));
printf("selected color as string: %s\n",col_str);
/*           strncpy(color_RR, col_str+1, 2);
          strncpy(color_GG, col_str+5, 2);
          strncpy(color_BB, col_str+9, 2);
          result_1 = TRUE;  */
     }
     else
     {
          result_1 = FALSE;
     }

```

Change any calls to xx_color to xx_rgba, in other words don't use gdk_color anymore, use gdk_rgba everywhere. Remember gdk_color is using guints and gdk_rgba is using gdoubles. Cairo is used for drawing now and uses doubles for colors in the range 0.0 to 1.0.

---

### Post by anewguy on 2012-02-20
I had to laugh at myself - I have all of that help already installed and didn't even remember it!  Here I've been going online to view the same documents! ;) ;)

Well, I made those changes and indeed the rgb values now come back as 0-255, however there's no alpha in the string return from the color selector.  So I'm trying to figure out - do I still need to do a call to get the alpha, and how is it going to come back - still as a double?  If so, I still need to know what I have to do to convert it to a 0.0 to 1.0 range.

Also, still no color change on the button.  I read in some of the docs somewhere that sometimes you have to define a gtk event box, pack the widget into the event box and change colors on the event box instead.  Last time I tried that is when everything changed to black, and even after removing the code everything stayed black so I had to roll back from a backup and start a lot of it over again.

Sure seems like they make things complicated - let the user select the color (they got that right), return a rgba string that includes the alpha (so far I don't know how the heck to get this and have convert it to a fraction), change the background and/or foreground color of a button (so far, at least for me, this is not working).

I'm about ready to just give it up.  I really do appreciate your help.
Thanks again!!

Dave ;)

---

### Post by anewguy on 2012-02-20
Ok, I'm on to something, but I'm not exactly what to do about it.  I got the color change of the widget to work, however I had to change the widget from a button to a label.  That results in only the text on the screen instead of a box of the color.  Maybe this is why the documents said to put the widget in event box and change the color on the event box.  I'm going to try that later tonight and see if I can get it to work this time without screwing everything up again.

If you have any ideas on this I'd appreciate knowing!

Dave ;)

---

### Post by anewguy on 2012-02-21
I've tried the event box thing again with the button inside it - still not working as needed.

If the event box is set as on top:

- holding the mouse button down on the button changes the color until the mouse is released - even if just a click.  BUT.....it apparently doesn't generate a signal, as the action is not taken.

If the even box is set to be on the bottom:

- the color NEVER changes, but mouse clicking at least generates a signal.


So, maybe by now what I'm trying to do has gotten lost, so I thought I would restate it again:

- I want a widget on the screen that shows a color and is clickable to trigger a callback.  I want to be able to change the color of the widget at will.

- a label widget "half" works - it only show the color for the text

- a button widget doesn't show any color except as noted above and that is when it's in an event box

Maybe I never stated it like that, but that's what I need - like you see in a lot of programs but for some reason I don't seem to be able to do.

---

### Post by pbrane on 2012-02-21
I would use color selection buttons instead, they will show the current color as well as allow you to click and select a new color. Also you can convert the double alpha value to integer in the range of 0-255 like this:
```

int int_alpha = double_alpha * 255;

```
You may need to round as this will truncate.

---

### Post by anewguy on 2012-02-21
I'll go looking to see what gtk or gdk has for built-ins for using color buttons.  I was using the color wheel since it was what I found for color selection.

Thanks for the tip on the alpha value - I'll see if I can figure out how to use it.

Thanks again!
Dave ;)

---

### Post by pbrane on 2012-02-21
The color selection button brings up a standard gtk color selector when clicked.

---

### Post by anewguy on 2012-02-21
Thanks!!!!  FINALLY!!!!  Something that does what I needed!!

I still have to figure out the alpha thing - it's still returned as a double and I don't think I understand how to get it to the CSS format of 0.0 to 1.0.  Once I know that I should really be on my way.  Next up:  font selection and color (hopefully using the font selection dialog as I found in the docs will do it?).

Thank you ***_SO_*** much!!  I don't understand why the other didn't work, but I guess it doesn't matter for now (until the time I want to change a button from "GO" on a green background to "STOP" on a red background, but that's not coming until later).

Dave ;)

---

### Post by pbrane on 2012-02-21
If you need the alpha value as a double for CSS then you should be set. You can format the output to the precision you need.

---

### Post by anewguy on 2012-02-21
I'll have to try do to some more checking, but it looks so far that the CSS alpha value is always expected as 0.0 to 1.0, and that's as a printed string such as 0.5.  I can work internally in the alpha double, but when it comes time to create the css file as far as I know it has to be the printed fraction format.

I've got plenty of other things to work on besides the alpha, so I may just slowly work my way through more pieces (and I'm sure plenty more dumb questions).

---

### Post by anewguy on 2012-02-22
Okay, I spent part of the late night adding in the color selection stuff for the background color - sure was easy since you pointed me to that color selection button (I had searched for such a thing but kept coming up with stuff for the color wheel).

I did run into something weird and am wondering if it's a bug.  I store the selected variables internally in css_xxxxx variable names.  I started noticing that even after I updated, if I went back to the main screen, selected the option for panel options and had the panel options screen come back up, for some reason the apparent value of those css_xxxxx variables seemed to change.  Further testing determined it wasn't the css_xxxxx variables, but the rather the gdk_rgba_parse that doesn't seem to be working correctly.  Given the below code snippet:



     if (FALSE ==  gdk_rgba_parse(&col,css_panel_color_RGBA))
     {
         do_message("ERROR","UNABLE TO PARSE PANEL COLOR");
     }  
printf("css_panel_color_RGBA at build of selection screen: %s\n",css_panel_color_RGBA);
printf("col at build of selection screen: %s\n",gdk_color_to_string(&col));


The output shows as:


dave@dave-MS-7576:~$ cd gnome_shell_css
dave@dave-MS-7576:~/gnome_shell_css$ ./gscedit
css_panel_color_RGBA at build of selection screen: #adadf7f7f7f7
col at build of selection screen: #b5b53fe5feff
css_panel_background_RGBA at build of selection screen: #0f0f0f0f0f0f
dave@dave-MS-7576:~/gnome_shell_css$ 


Notice that in the code I show the value that was loaded into the GdkColor "col", followed immediately by a convert back to string of the GdkColor "col"'s color value.  They should be identical.  Instead, the value that was supposed to get loaded was:

css_panel_color_RGBA at build of selection screen: #adadf7f7f7f7

while the immediate convert back to string is:

col at build of selection screen: #b5b53fe5feff


I put some tracing through the program where I changed the color, etc., and the value show in the first output is correct.  However, the string conversion of that string after it was loaded into a GdkColor is wrong.

Maybe there's something stupid there I'm not seeing, but I think there is a bug.

Any ideas what to do about the problem?

Thanks again!
dave ;)

---

### Post by pbrane on 2012-02-22
In the gdk_rgba_parse function are you passing the spec string with the '#' included? An rgba spec should not have the '#', just the hex string. there is a definition of the arguments to gdk_rgba_parse in devhelp under GDK 3 Reference Manual.

and one more thing:
```

printf("col at build of selection screen: %s\n",gdk_**rgba**_to_string(&col));

```
change the call to gdk_**color**_to_string to gdk_**rgba**_to_string. That may have a lot to do with the apparent discrepancy. Remember GdkColors are integers and GdkRGBAs are doubles. Big difference.

---

### Post by anewguy on 2012-02-22
Man, I don't know what I'd be doing without your help.  I've been away from C for a long, long time (I've only written maybe 2 programs since I quit working in 1996), and I just don't remember a dang thing.  All of the gdk color/rgba stuff is completely new to me.  I've used GTK in 1 program prior to now (it was a lot simpler than this).  I feel like an idiot considering I worked as a programmer/analyst for a few years and then a systems programmer for the remaining part of over 2 decades in the field.

So, I'll look that up and try again.

Thank you so much, and thank you very much for your patience!

Dave ;)

---

### Post by pbrane on 2012-02-22
There's a big difference between C programming and GUI programming. And Gtk just underwent some big changes from 2.0 to 3.0. Your C programming seems fine, it's just learning Gtk 3 that's tough. I've been using Gtkmm 2.0 for several years now and I have to constantly look up function calls still, not to mention all the new changes when porting to Gtkmm 3.0.

---

### Post by anewguy on 2012-02-22
I now have officially the biggest can of worms of errors I have had to date.  I don't know what I'm doing wrong, and I'm tired of fighting it.

Project officially dead thanks to my stupidity.

Thanks for your help, though - it has been extremely helpful for me!

Dave ;(

---

### Post by MG&amp;TL on 2012-02-22
> **anewguy said:**
> I now have officially the biggest can of worms of errors I have had to date.  I don't know what I'm doing wrong, and I'm tired of fighting it.

Project officially dead thanks to my stupidity.

Thanks for your help, though - it has been extremely helpful for me!

Dave ;(

:(

Dead projects are very sad. While it's your choice, I've been there, and it's a lot more satisfying to finish it than be sad about it. I hope you carry on with it, unofficially ;)

Have fun, whatever you do.

---

### Post by anewguy on 2012-02-23
I just can't get the hang of this gtk/gdk stuff.  gtk I thought I was doing okay with for what I needed to do, but since I needed the gdkcolor stuff in order to get that extremely easy color button, everything has gone to heck.  I changed every reference I had to a gdk color to be sure it was referencing what I thought were the correct gdk functions.  I've looked through the help many time and recognized that ok, now that I was pointed in the right direction, I need to use this function in place of that function to do the things I want.  The only problem is everything went to heck.  My rgba variable, when converted to strings using the rgba function, come out with 0's in the color members and a double in the alpha.  Shouldn't be zeros, and I don't know why they are.  They only references I have found in the gdk docs that make it easier to use have a rgba syntax of 'rbga(red,green,blue,alpha)' - but I try that and the errors compound.  I've got so many warnings about the gtk function expecting widget but getting rgba instead (when there doesn't seem to be a gdk function equivalent), so many warnings about expecting this type instead of that.  I'm back to all black screens.  I've color buttons, but the gdk rgba to string of the color values returned still show 0's in the red, green and blue members.  Nothing is remembered.  At least a day ago everything was remembered.  Right now I have no clue where to even start to try to fix things, or what is wrong to begin with.  It's making me feel extremely stupid and extremely frustrated.

---

### Post by anewguy on 2012-02-23
Here's just a small example of my problems:

given:

```

/*
          Variable definitions
*/

     GdkRGBA col;
     GdkRGBA wrkcol;
     GdkRGBA wrkcol1;
     GdkRGBA pbg_col;
     guint16 color_alpha = 255;

     char color_RR[3];
     char color_GG[3];
     char color_BB[3];
     char color_OPACITY[] = "255";

     int has_opacity = FALSE;
     int max_win_length;
     int max_win_height;
     int returned = TRUE;

     char text_get_color[256];
     char col_str[256];
     char *default_scr_bg = "A4FFE3";
     


/* 
          GTK  variables
*/

     GtkWindow *opening_window;
     GtkWidget *vbox0;
     GtkWidget *vbox1;
     GtkWidget *vbox2;
     GtkWidget *vbox3;
     GtkWidget *vbox4; 
     GtkWidget *label1;
     GtkWidget *label2;
     GtkWidget *label3;
     GtkWidget *hbox1;
     GtkWidget *hbox2;
     GtkWidget *hbox3;
     GtkWidget *hbox4;
     GtkWidget *hbox5;
     GtkWidget *hbox6;
     GtkWidget *hbox7;
     GtkWidget *hbox8;
     GtkWidget *open_existing;
     GtkWidget *new_file;
     GtkWidget *save_file;
     GtkWidget *panel_selected;
     GtkWidget *panel_win1;
     GtkWidget *panel_transparent_text;
     GtkWidget *panel_current_color;
     GtkWidget *panel_background_color;


/***************************************************************/
/*   Begin defining gnome-shell.css variables.  These are used */
/*   to default selections and to build the final css file.    */
/***************************************************************/

     char *css_panel_color_RGBA = "0,0,0,6.9475519216084197e-310";
     double  css_panel_color_alpha = 38000;

     char *css_panel_background_RGBA = "0,0,0,6.9475519216084197e-310";
     double css_panel_background_alpha = 58525;
     int panel_background_image_active = FALSE;
     int panel_background_color_active = TRUE;

```

And:

```
/***************************************************************
            Panel Selection Options

  This routine shows the Panel items selection screen and 
  processes requests.

****************************************************************/

void panel_options()
{

     GtkWidget *wrkbox1;
     GtkWidget *wrkbutton1;
     GtkWidget *wrkbox2;
     GtkWidget *wrkbutton2;
     GtkWidget *divid1;
     GtkWidget *table1;
     GtkWidget *label2;
     GtkWidget *label3;
     GtkWidget *label4;
     GtkWidget *label5;
     GtkWidget *label6;
     GtkWidget *label7;
     GtkWidget *label8;
     GtkWidget *label9;
     GtkWidget *label10;
     GtkWidget *table11;
     GtkWidget *label12;
     GtkWidget *label13;
     GtkWidget *label14;
     GtkWidget *label15;
     GtkWidget *label16;
     GtkWidget *label17;
     GtkWidget *label18;
     GtkWidget *label19;
     GtkWidget *label20;
     GtkWidget *button1;
     GdkColor   colorButton;
     GtkWidget *button_Widget;

 

     int wrki_1 = 0;
     int wrki_2 = 0;

     char wrkstr1[700];


     panel_win1 = gtk_window_new (GTK_WINDOW_TOPLEVEL);
     gtk_window_set_title (GTK_WINDOW(panel_win1), "GNOME SHELL CSS FILE EDITOR - PANEL OPTIONS");
     gtk_window_set_default_size(GTK_WINDOW(panel_win1), 640, 480);
     gtk_window_set_position (GTK_WINDOW(panel_win1), GTK_WIN_POS_CENTER);
     g_signal_connect (G_OBJECT (panel_win1), "delete_event",
                       G_CALLBACK (close_window), GTK_CONTAINER(panel_win1));
     g_signal_connect (G_OBJECT (panel_win1), "destroy",
                       G_CALLBACK (close_window), GTK_CONTAINER(panel_win1));
     gtk_container_set_border_width (GTK_CONTAINER(panel_win1), 5);
     gtk_widget_override_background_color(GTK_WIDGET(panel_win1),
                                          GTK_STATE_NORMAL,
                                          &default_scr_bg);     
      
     wrkbox1 = gtk_vbox_new(FALSE, 5);
     gtk_container_add (GTK_CONTAINER (panel_win1), wrkbox1);

     table1 = gtk_table_new(15,10,TRUE);

     label1 = gtk_label_new("Panel Color:");
     
     label2 = gtk_label_new("Background:");

     strcpy(wrkstr1,"'rgab(");
     strcat(wrkstr1,css_panel_color_RGBA);
     strcat(wrkstr1,")'");

printf("Before parse of panel color\n");
     if (FALSE ==  gdk_rgba_parse(&col,wrkstr1))
     {
         do_message("ERROR","UNABLE TO PARSE PANEL COLOR");
     }  
printf("css_panel_color_RGBA at build of selection screen: %s\n",css_panel_color_RGBA);
printf("col at build of selection screen: %s\n",gdk_rgba_to_string(&col));



     panel_current_color = gtk_color_button_new_with_color(&col);
     gtk_color_button_set_use_alpha(panel_current_color,
                                    TRUE);
     gtk_color_button_set_title (panel_current_color,"Select Panel Color and Transparency");
     g_signal_connect (G_OBJECT (panel_current_color), "color-set",
                       G_CALLBACK (update_css_panel_color), NULL);
     gtk_color_button_set_alpha(panel_current_color, css_panel_color_alpha); 

     panel_background_image_active =  gtk_radio_button_new(NULL);

     panel_background_color_active = gtk_radio_button_new(NULL);

     gtk_radio_button_join_group( panel_background_color_active, panel_background_image_active);
     gtk_toggle_button_set_active (GTK_RADIO_BUTTON (panel_background_color_active), TRUE); 


     label3 = gtk_label_new("Image:");

     label4 = gtk_label_new("Color:");

     if (FALSE ==  gdk_rgba_parse(&pbg_col,css_panel_background_RGBA))
     {
         do_message("ERROR","UNABLE TO PARSE PANEL COLOR");
     }  
printf("css_panel_background_RGBA at build of selection screen: %s\n",css_panel_background_RGBA);

     panel_background_color = gtk_color_button_new_with_color(&pbg_col);
     gtk_color_button_set_title (panel_background_color,"Select Panel Background Color and Transparency");
     gtk_color_button_set_use_alpha(panel_background_color,
                                    TRUE);
     g_signal_connect (G_OBJECT (panel_background_color), "color-set",
                       G_CALLBACK (update_css_panel_background), NULL);
     gtk_color_button_set_alpha(panel_background_color, css_panel_background_alpha); 

 
     gtk_table_attach (GTK_TABLE(table1), label1, 0,1,0,1,
                       GTK_EXPAND, GTK_SHRINK, 0, 0);
     gtk_table_attach (GTK_TABLE(table1), panel_current_color, 1,3,0,1,
                       GTK_EXPAND, GTK_SHRINK, 0, 0);
     gtk_table_attach (GTK_TABLE(table1), label2, 0,1,1,2,
                       GTK_EXPAND, GTK_SHRINK, 0, 0);
     gtk_table_attach (GTK_TABLE(table1),
                       panel_background_image_active,
                       1,2,1,2,
                       GTK_EXPAND,
                       GTK_SHRINK,
                       0, 0);
     gtk_table_attach (GTK_TABLE(table1),
                       panel_background_color_active,
                       1,2,2,3,
                       GTK_EXPAND,
                       GTK_SHRINK,
                       0, 0);
     gtk_table_attach (GTK_TABLE(table1), label3, 2,3,1,2,
                       GTK_EXPAND, GTK_SHRINK, 0, 0);
     gtk_table_attach (GTK_TABLE(table1), label4, 2,3,2,3,
                       GTK_EXPAND, GTK_SHRINK, 0, 0);
     gtk_table_attach (GTK_TABLE(table1), panel_background_color, 3,4,2,3,
                       GTK_EXPAND, GTK_SHRINK, 0, 0);

     gtk_table_set_row_spacings (GTK_TABLE(table1),3);
     gtk_table_set_col_spacings (GTK_TABLE(table1),3);

     gtk_container_add(GTK_CONTAINER(wrkbox1), table1);

     gtk_widget_show(table1);
     



     gtk_widget_hide (opening_window);
     gtk_widget_show_all(panel_win1);
     return;
/*

    padding-bottom: .15em;
    background-gradient-direction: vertical;
    background-gradient-start: rgba(0,100,0,0.9); 
    background-gradient-end: rgba(0,0,0,0.9);
    color: rgba(221,187,102,1.0); 
    border: .05em solid transparent rgba(93,252,10,0.3);
    border-top: 0px;
    border-left: 0px;
    border-right: 0px;
    height: 1.4em;
    box-shadow: 0px 5px 10px rgba(93,252,10,0.2); 
    font-size: 1.1em;
    font-weight: bold italic;
    font-family: Magik, MintSpirit, cantarell, ubuntu, serif;
    text-align: center;

*/

}
```


Results in the following:

dave@dave-MS-7576:~/gnome_shell_css$ ./gscedit
Before parse of panel color

(gscedit:5581): Gtk-WARNING **: Attempting to add a widget with type GtkLabel to a GtkDialog, but as a GtkBin subclass a GtkDialog can only contain one widget at a time; it already contains a widget of type GtkBox
css_panel_color_RGBA at build of selection screen: 0,0,0,6.9475519216084197e-310
col at build of selection screen: rgba(0,0,0,0)

(gscedit:5581): Gtk-WARNING **: Attempting to add a widget with type GtkLabel to a GtkDialog, but as a GtkBin subclass a GtkDialog can only contain one widget at a time; it already contains a widget of type GtkBox
css_panel_background_RGBA at build of selection screen: 0,0,0,6.9475519216084197e-310
css_panel_background_RGBA at end of update:
        red: 2.17389E-322
      green: 2.17389E-322
       blue: 2.17389E-322
Before parse of panel color

(gscedit:5581): Gtk-WARNING **: Attempting to add a widget with type GtkLabel to a GtkDialog, but as a GtkBin subclass a GtkDialog can only contain one widget at a time; it already contains a widget of type GtkBox
css_panel_color_RGBA at build of selection screen: 0,0,0,6.9475519216084197e-310
col at build of selection screen: rgba(0,0,0,0)
css_panel_background_RGBA at build of selection screen: rgba(0,0,0,6.9492881446696641e-310)
dave@dave-MS-7576:~/gnome_shell_css$ 


I can only assume the 5581 Gtk warnings must be coming from:

     if (FALSE ==  gdk_rgba_parse(&col,wrkstr1))
     {
         do_message("ERROR","UNABLE TO PARSE PANEL COLOR");
     }  

which is parsing the gdk color built up in to the 'rgba(r,g,b,alpha)' syntax, as the program appears to be going through my do_message routine 2 times - but the "ERROR" and "UNABLE TO PARSE PANEL COLOR" texts aren't showing in the message, and nothing has changed in the message routine that has always worked fine (it' copied from something I did a few years ago and was working find until I changed this to gdk_rgba).  All of these things started happening when I did the changes over to gdk_rgba things as suggested due to the problems I was having.

So, it still doesn't "remember" the colors, and I can't get rid of the run time warning let alone the compiler warnings.  It also doesn't show the default color on the selection wheel when it calls it up.

It seems like it SHOULD be so simple:

store a color value internally in the program for the initial screen background color

load that color to a gdk_rgba color

change the background color to the gdk_rgba_color

for now, initially take a hard-coded value for a button color(it will be loaded/converted from a CSS file value later) and convert it to a default color for button backgrounds

define a gdk rgba color button

set the background color of that button to the previously built color

when the user presses the button, show the current color on the color wheel

when user exits color selection screen, store the color and alpha selected

eventually, when the user has decided they are done with their changes, write out a CSS file containing the values, as in this snippet:

#panel {
    color: #XXXXXX, #XXXXXXXXXXXX, rgb numbers, rgba format of 'rgba(red value of 0.0 to 1.0, green value of 0.0 to 1.0, blue value of 0.0 to 1.0, alpha value of 9.9 to 1.0)
  ** note that the rgba numbers must be in printed fraction format, not a double, and int or anything else -> they must actually show as something like "0.4".
    background-color: same type of color formats as above
-or-
    background-image: ...the proper syntax of a file selected....
.
.
.
.

This seems like it should be SO easy - that's why I took it on.  It has turned into such a frustration that it just doesn't seem worth it.  1 step forward, 5 back doesn't get me anywhere.

---

### Post by anewguy on 2012-02-23
Okay, I think I have determined what got me into this big mess.  I wanted a color selection button that showed the currently selected color, so it was suggested to use gdk_color_button, which resulted in some interesting results.  It looked like I wanted, but some things weren't working, so the suggestion was made to convert to rgba type variables.  This really made a mess.

I have now found out there is a GTK color button - and I've been using GTK.  I think the mixture of gdk and GTK doesn't agree.  I've looked at the gdk docs and can't see how to make my app, but if I go back to all GTK variable and use the GTK color button, I *think* I'll get what I want and have it work right (except of course for that dang pesky color alpha stuff).

So, back to a backup and use gtk_color_button.  I'll let you know what happens.

 dave

---

### Post by anewguy on 2012-02-23
Yes!  It took a while, but I'm back to where I can select panel color and background color and it is remembered correctly, using regular gdkcolors, not the rgba colors.  So, I'm going to reopen this thread.

Next step is to try to add a file selector.

Coming soon:  font selection

Thanks everyone for your help  -  I obviously didn't understand how to apply things.

Dave ;)

---

### Post by anewguy on 2012-02-23
Ok, I've run into something that I know is just a programming syntax thing, but I don't remember how it works.

I put my main function at the button of my C file because it used a lot of functions that needed to be defined first.  I've finally gotten to a point where I have a button definition and callback defined and put the callback before the function using it.  Only trouble is the callback wants to hide one button and show another, but the callback, being before the function where the buttons are defined, treats them as widgets and not as buttons, so it errors out when it get to the defining function saying that the definition is being changed.

I also know there's supposed to be a way to make each of these functions a separate C file and then just compile *.c.

So, I seem to remember something called function prototyping - I think that would get around the first problem.  Trouble is, I don't seem to be able to do it correctly since I do things like:

void somefunction();

before any functions are defined, then define somefunction:

void somefunction ()
{
   ....does stuff....
}

when it hits the define of the function with the code in it, it errors out saying the function already exists.

So:

- what do I have to do to prototype the functions and have the set of prototypes loaded 1st in the gcc string so that the rest of the functions following it know about all the other functions?  Is this something that instead I need to make a header file for and include the header file in each .c source file, even if it doesn't use the other functions?

- how can I break this all up by function and still have global variables declared once like I do now (at least I think that's what they are when they are before any function definitions in a C file).

Right now I'm at the point I really do need to set things up "correctly" as I'm in a catch-22 of the chicken before the egg before the chicken with the buttons.

Also, I can't find anything in the docs nor on line that says how to hide a GTK button.  Quite simply, the file selector and the color selection are mutually exclusive for the background color stuff I'm generating.  I defined 2 toggle buttons as a group, then wanted to hide the color selection button and show the file selection button when toggle 1 is pressed, and the opposite when toggle 2 is pressed.  Hopefully the image I'm attaching can give you an idea - it's shows the background color as the selected option, but I haven't figured out how to hide the file selection (or at least make it non-clickable) while the background color is selected.

As always, any help would be greatly appreciated!

Dave ;)

---

### Post by MG&amp;TL on 2012-02-23
> **anewguy said:**
> So, I'm going to reopen this thread.


:D

Well done, love to hear things are going well.

---

### Post by anewguy on 2012-02-23
Well, I reall could use some help again.  I can't get the function prototyping thing to work without it causing errors for some reason.  If I put in a prototype such as:

void testit();

Then the code for main makes the window appear as per above.  I still have main at the end, but put the actual function testit at the end as well.  Main activates the panel_options function which draws and handles the 2nd screen.  Panel_options still comes before main in the code.  Panel options defines gtk buttons, in particular gtk color buttons and a gtk file selection button.  The signal handler definition in panel options for one of those buttons is specified as testit.  The compiler kicks it out saying testit isn't defined.  I don't really understand - I prototyped it even if the actual definition isn't until the end.

I'm also running into a problem where testit wants to hide one of the gtk buttons - but there appears to be no function to do so.  In addition, if I try just to use gtk_widget_hide on the button, I get an error when the compiler gets into the calling code saying the type is changing.

It's a button - I thought a button was a widget.  The definition of the widget is global (above all the code).  So why does a hide of a widget prior to the setting of the widget to a button cause the setting of the widget to a button to error out in the compiler?

If you need sample code, let me know.

Thanks in advance again!

Dave ;)

---

### Post by anewguy on 2012-02-24
I think I'm going to close this thread, since I have had my initial questions answered.  I will open new threads specific to new problems.

Thanks to everyone for all their help!

Dave ;)

---

