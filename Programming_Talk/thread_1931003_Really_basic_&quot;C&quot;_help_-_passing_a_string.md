---
title: "Really basic &quot;C&quot; help - passing a string to a function"
date: 2012-02-24
forum: Programming Talk
---

### Post by anewguy on 2012-02-24
I have some problems getting my program to run correctly when using the following code segments.  Both of these are before main.

called function:


void toggle_onoff(char wrkstr1)
{
printf("At onoff\n");
printf("At onoff: %s\n",wrkstr1);
     gtk_widget_hide(strtok(wrkstr1,","));
     gtk_widget_show(strtok(NULL,",")); 
 
     return;
 
}



called via:

     g_signal_connect(G_OBJECT (panel_background_color_active), "toggled",
                       G_CALLBACK (toggle_onoff),
                       "panel_background_file,panel_background_color");

This is the signal handler for a radio button.

The result when run from terminal and the radio button is clicked:

dave@dave-MS-7576:~/gnome_shell_css$ ./gscedit
At onoff
Segmentation fault
dave@dave-MS-7576:~/gnome_shell_css$ 

Via my tracing printf statements, it's obviously blowing out on the following statement in the called function:

printf("At onoff: %s\n",wrkstr1);

This indicates to me that wrkstr1 doesn't actually contain the string I'm trying to pass.

I had gotten this a "little" further when I used a predefined string instead of a literal string:

It ran, but the results where, well, let's say "strange", at best.  Using the printf of the string in the called function, the string was garbage, not what I put in it.

This leads me to believe I have no idea how to pass a string to a function.  On the signal connect, the variable following the callback is passed to the callback function - so I assume it's the same as if I had written toggle_onoff(my-string-here).  So that means there is something wrong in how I'm defining the string being passed in the called function definition - (char wrkstrg1).  I thought that meant a string was being passed into the function and the local variable name is wrkstrg1.  Considering the string is always garbage, I have to assume that's not correct.

Could someone please point in the right direction of what the callback would look like and what the called function would look like in order to get the actual value in the string into the called function?

Thanks in advance!

Dave ;)

---

### Post by r-senior on 2012-02-24
> **anewguy said:**
> I have some problems getting my program to run correctly when using the following code segments.  Both of these are before main.

```

void toggle_onoff(char wrkstr1)

```


You are passing a char not a string (char *). The function should be 

```

void toggle_onoff(char *wrkstr1)

```

It's going to blow up when printf tries to get what's pointed to by wrkstr1. Because it's not a pointer, it's a char.

---

### Post by Simian Man on 2012-02-24
You probably should not learn C and GTK+ at the same time.  Both are quite complicated topics.  If you want to learn C, start a whole lot smaller.  If you want to write a GUI program, I'd recommend using something much simpler like Python + Tkinter.

---

### Post by anewguy on 2012-02-24
Actually, I used to be a systems programmer on mainframes, then minis and finally micros as they came out up until 1996.  Haven't worked since.  So it's not so much a matter of being new at it, as it is 16 years of being away from it.  I think the first thing I tried was using a char string pointer, and it still failed.  I'll go back and try that again.  Also, I've tried passing as a single variable - no luck, as a pointer to that variable - no luck, and even the address of that variable - no luck.  Maybe someplace along the line I didn't try the correct combination.

Indeed, I just made a change and tried it:

Given the change (I thought I had tried this before):

void toggle_onoff(char *wrkstr1)
{

printf("At onoff\n");
printf("At onoff: %s\n",wrkstr1);
     gtk_widget_hide(strtok(wrkstr1,","));
     gtk_widget_show(strtok(NULL,",")); 
 
     return;
 
}


and the signal handler definition:

g_signal_connect (G_OBJECT (panel_background_image_active), "toggled",
                       G_CALLBACK (toggle_onoff),
                       "panel_background_color,panel_background_file");



and the same thing happens:

dave@dave-MS-7576:~/gnome_shell_css$ ./gscedit
At onoff
At onoff: &#65533;&#65533;&#65533;

(gscedit:18478): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
At onoff
At onoff: &#65533;&#65533;&#65533;

(gscedit:18478): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
dave@dave-MS-7576:~/gnome_shell_css$ 


I also have tried before, and just reverified via testing, that if I use a variable instead, such as wrkconst1 defined as a char *, and just put that in place of the string - e.g.:

g_signal_connect (G_OBJECT (panel_background_image_active), "toggled",
                       G_CALLBACK (toggle_onoff),
                       wrkconst1);

or used a pointer def I know is wrong:

g_signal_connect (G_OBJECT (panel_background_image_active), "toggled",
                       G_CALLBACK (toggle_onoff),
                       "*wrkconst1);

or even worse yet, the address of the string:

g_signal_connect (G_OBJECT (panel_background_image_active), "toggled",
                       G_CALLBACK (toggle_onoff),
                       &wkrconst1);

The result is the same.

I know C and GTK are both not simple topics.  I'm not a rookie at C - just EXTREMELY rusty.  Things do come back to me.  GTK I have used before where I dynamically built screens, did both hide and shows of a normal gtk button.  I don't claim to know much about it - but I've gone through it before and made it work.  This time around I've needed a bunch of help because I started messing with a color button, and had to be told that existed (I never saw in dev help until AFTER I was told about it).  Originally I had written a function to do it but wasn't able to change the background color of a GTK label - that's why the gdk color button was recommended.  I've had a little trouble with the docs, but am getting better, as at first I could remember for the life of me how the syntax in the definitions got translated to usage.  I've picked back up on that, except there are still times, and the docs to me aren't clear on this, that you can't tell if you are supposed to put things like the G_OBJECT literal in the signal handler definition or if you are just supposed to put the object itself.  That's been mainly a matter of trial and error.

So, I guess what I'm saying is forgive me if a question seems stupid - but there's a reason it's being asked.  Conceptually I understand both fine - my C syntax leaves a little to be desired, and I know it, but don't remember the "correct" way now.  GTK - well, the docs are shall we say "not good".  There are also obscure things that happen: not being able to set the background color of a label, so you have to define an event box just to put the label in and change the background of the event box.  Things like having a widget defined globally, and in the above examples, instead of parsing out names of widgets just hard coding the widgets in the hide/show statements, only to have the statements further down in the code that assign a gdk button to that widget blow out in the compiler because it says I'm "changing the type of the widget" - to me that makes no sense.  That's what forced me to the way I am attempting now. the signal connect only allows passing 1 variable to the callback, so when you have more than 1 you have to play games - and I thought global widget variables would take care of that but no.  So, I string together the names of the widgets so I can parse them in the callback function - except the string never gets to the callback.  I have to assume yet that it's still something to do with that 1 variable on the signal connect definition and exactly what form and how it is passed that is causing the problem.  I don't feel like digging in to the guts of gtk to find how the signal connect is actually defined in C and how it internally sets up the callback function call and how it passes the variable to it.  Ain't in the docs.

Pressed send too early - there are images attached - it shows the screen and the button I push that triggers the callback, then shows the resulting screen (note how it hid the incorrect buttons - the radio buttons - and not color select button. It seems I can attach them on an edit, so I'll post a follow up so you can see them.

---

### Post by anewguy on 2012-02-24
Here's the images - the first is the selection screen with the mouse pointer on the radio button I'm about to click.  The second is that screen after I've clicked on that button.

The idea is simple - background image and background color are mutually exclusive.  I default to background color.  When I click on the radio button in front of background image all it is supposed to do is hide the color button that shows after background color and show the file selection button (initially hidden).  That's it.  Simple concept.  The C code and gtk crap should be easy - on the toggle of the radio button, hide the background color selection button widget, show the background file selection button widget.  The complication comes in if the widget names are hard coded, as it causes the aforementioned compiler error.  So, went to a string of the widget names so I could pass them in the 1 allowed variable to the signal handler callback function.  Again, should be easy.  Not working out as so.  Because of the garbage in place of the string, the radio buttons are being hidden and the widget names for them aren't even being passed to the callback function.

---

### Post by dwhitney67 on 2012-02-24
> **anewguy said:**
> 
```

void toggle_onoff(char *wrkstr1)
{

printf("At onoff\n");
printf("At onoff: %s\n",wrkstr1);
     gtk_widget_hide(strtok(wrkstr1,","));
     gtk_widget_show(strtok(NULL,",")); 
 
     return;
 
}

g_signal_connect (G_OBJECT (panel_background_image_active), "toggled",
                       G_CALLBACK (toggle_onoff),
                       "panel_background_color,panel_background_file");

```


Please post your code within CODE tags, like I have done above.

As for the error, you are passing a string literal to the callback function, and this string is immutable.  You should not be calling strtok() with this type of string.  That is why your program is failing.

First, declare toggle_onoff() as this:
```

void toggle_onoff(**const **char *wrkstr1)

```
Then fix the code within the function to be:
```

{
    char* tmp = strdup(wrkstr1);  // allocate a copy of the string
    char* str = tmp;              // set a reference to this copy

    gtk_widget_hide(strtok(str,","));
    gtk_widget_show(strtok(NULL,","));

    free(tmp);    // free the copy
}

```
Of course, you may want to add some error checking to the function.  But since you are probably always going to be passing the same string literal to the function, it is probably a safe bet that wrkstr1 will never be NULL, and that the strtok() will never return NULL.

---

### Post by anewguy on 2012-02-24
Thanks!  you know, I tried first with a construct, but I missed putting the 

    char* tmp = strdup(wrkstr1);  // allocate a copy of the string
    char* str = tmp;              // set a reference to this copy

in the function to get a string copy.

So, I tried this, with the following result:

```
/***************************************************************
             toggle onoff

  Hides 1st widget, shows 2nd.

****************************************************************/

void toggle_onoff(const char *wrkstr1)
{
    char* tmp = strdup(wrkstr1);  // allocate a copy of the string
    char* str = tmp;              // set a reference to this copy

printf("At onoff\n");
printf("At onoff: %s\n",str);
     gtk_widget_hide(strtok(str,","));
     gtk_widget_show(strtok(NULL,",")); 
 
     return;
 
}

```

and

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
     GdkColor  colorButton;
     GdkColor  bgcolorbutton;
     GtkWidget *button_Widget;
     GdkColor  *tmpcolor;


     int wrki_1 = 0;
     int wrki_2 = 0;

     char *wrkstr1;
     char *wrkconst1 = "panel_background_file,panel_background_color";
     char *wrkconst2 = "panel_background_color,panel_background_file";



     panel_win1 = gtk_window_new (GTK_WINDOW_TOPLEVEL);
     gtk_window_set_title (GTK_WINDOW(panel_win1), "GNOME SHELL CSS FILE EDITOR - PANEL OPTIONS");
     gtk_window_set_default_size(GTK_WINDOW(panel_win1), 640, 480);
     gtk_window_set_position (GTK_WINDOW(panel_win1), GTK_WIN_POS_CENTER);
     g_signal_connect (G_OBJECT (panel_win1), "delete_event",
                       G_CALLBACK (close_window), GTK_CONTAINER(panel_win1));
     g_signal_connect (G_OBJECT (panel_win1), "destroy",
                       G_CALLBACK (close_window), GTK_CONTAINER(panel_win1));
     if (FALSE == gdk_color_parse (default_scr_bg, &tmpcolor))
     {
         do_message("ERROR","UNABLE TO PARSE SCREEN BACKGROUND COLOR");
     }  
     gtk_widget_modify_bg(panel_win1, GTK_STATE_NORMAL, &tmpcolor);


     gtk_container_set_border_width (GTK_CONTAINER(panel_win1), 5);

     wrkbox1 = gtk_vbox_new(FALSE, 5);
     gtk_container_add (GTK_CONTAINER (panel_win1), wrkbox1);
     
     table1 = gtk_table_new(15,10,TRUE);
     label1 = gtk_label_new("Panel Color:");
     label2 = gtk_label_new("Background:");


     if (FALSE == gdk_color_parse (css_panel_color, &colorButton))
     {
         do_message("ERROR","UNABLE TO PARSE PANEL COLOR");
     }  

     panel_color = gtk_color_button_new_with_color(&colorButton);
     gtk_color_button_set_title(panel_color,"Select Panel Color and Transparency");
     gtk_color_button_set_use_alpha (panel_color, TRUE);

     panel_background_file = gtk_file_chooser_button_new("Select Panel Background Image File ",GTK_FILE_CHOOSER_ACTION_OPEN);


     if (FALSE == gdk_color_parse (css_panel_background_color, &bgcolorbutton))
     {
         do_message("ERROR","UNABLE TO PARSE PANEL COLOR");
     }  

     panel_background_color = gtk_color_button_new_with_color(&bgcolorbutton);
     gtk_color_button_set_title(panel_background_color,"Select Panel Background Color and Transparency");
     gtk_color_button_set_use_alpha (panel_background_color, TRUE);


     panel_background_image_active =  gtk_radio_button_new(NULL);
     panel_background_color_active = gtk_radio_button_new(NULL);
     gtk_radio_button_join_group( panel_background_color_active, panel_background_image_active);
     gtk_toggle_button_set_active (GTK_RADIO_BUTTON (panel_background_color_active), TRUE); 
     gtk_widget_hide(panel_background_file);

     label3 = gtk_label_new("Image:");
     label4 = gtk_label_new("Color:");

     g_signal_connect (G_OBJECT (panel_color), "color-set",
                       G_CALLBACK (update_css_panel_color),
                       NULL);

     g_signal_connect (G_OBJECT (panel_background_color), "color-set",
                       G_CALLBACK (update_css_panel_background_color),
                       NULL);


     g_signal_connect (G_OBJECT (panel_background_color_active), "toggled",
                       G_CALLBACK (toggle_onoff),
                       "panel_background_file,panel_background_color");


     g_signal_connect (G_OBJECT (panel_background_image_active), "toggled",
                       G_CALLBACK (toggle_onoff),
                       "panel_background_color,panel_background_file");

 

     gtk_table_attach (GTK_TABLE(table1), label1, 0,1,0,1,
                       GTK_EXPAND, GTK_SHRINK, 0, 0);
     gtk_table_attach (GTK_TABLE(table1), panel_color, 1,3,0,1,
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
     gtk_table_attach (GTK_TABLE(table1), panel_background_file, 3,5,1,2,
                       GTK_EXPAND, GTK_SHRINK, 0,0);
     gtk_table_attach (GTK_TABLE(table1), label4, 2,3,2,3,
                       GTK_EXPAND, GTK_SHRINK, 0, 0);
     gtk_table_attach (GTK_TABLE(table1), panel_background_color,3,4,2,3,
                       GTK_EXPAND, GTK_SHRINK, 0, 0);
     gtk_table_set_row_spacings (GTK_TABLE(table1),3);
     gtk_table_set_col_spacings (GTK_TABLE(table1),3);

     gtk_container_add(GTK_CONTAINER(wrkbox1), table1);

     gtk_widget_show(table1);
     



     gtk_widget_hide (opening_window);
     gtk_widget_show_all(panel_win1);
     gtk_widget_hide(panel_background_file);  
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

The result is the same errors, and now the screen doesn't even show anything.

```
dave@dave-MS-7576:~/gnome_shell_css$ ./gscedit
At onoff
At onoff: &#65533;z1
Segmentation fault
dave@dave-MS-7576:~/gnome_shell_css$ 


```

I still think it's actually something to do with how the signal processor passes the variable, but I could be wrong.  I have looked a lot on the net for this as well, but the only thing I could find was a C++ thing for a creating an object.context and passing it, then parsing it back out in the callback function.  I'm not aware of anything resembling a context object in normal C, so that's why I've tried the variables and then the hard coded strings.  I thought in the way I would be accomplishing the same thing - passing the 2 variable names - but maybe, not really knowing anything about C++ (while I was working I took a 2 college courses in it, but at work it was just C, so never got to use C++ in a practical way).  I've written actual context swappers in C and assembly in the main frame world, but that was a LONG time ago.

Any help is appreciated!  In the mean time, I guess I need to go back to trying to dig through the net on what type of variable is allowed on the signal processing definition and exactly how to pass that.

And you guys will have to forgive me - I get extremely frustrated with myself because of what I used to do and now not seeming to be able to do the simplest of dang things, and I know that frustration comes across in my posts even though I'm trying hard not to let it.  

Thanks again!
Dave ;)

---

### Post by anewguy on 2012-02-24
Well, further testing using local strings to the callback function shows that you apparently can't use a variable to hold the name of the widget in a gtk widget function anyway:

```
char * var1="button1";

gtk_widget_hide(var1);
```

results in a segmentation fault at runtime.

So, I had to break it out into 2 discreet functions using the actual widget names (and for some reason it compiled ok now when it didn't with the same thing previously).  Works as needed.  I'm just disappointed that I have to have 2 discreet functions instead of a single more generic one.

So, wouldn't have mattered what was done - it wasn't going to work.

Thread closed.

---

### Post by Bachstelze on 2012-02-25
I don't want to sound rude, but you wouldn't have had this problem if you had bothered to check the documentation for the functions you use.

[http://developer.gnome.org/gtk/2.24/GtkWidget.html#gtk-widget-hide](http://developer.gnome.org/gtk/2.24/GtkWidget.html#gtk-widget-hide)

```
void gtk_widget_hide(GtkWidget *widget);
```

not

```
void gtk_widget_hide(char *widget);
```

The compiler probably gave you a warning about that, as well.

---

### Post by anewguy on 2012-02-25
While I only posted what I have, the search of the net turned that up and was already tried long before I posted - it fails in the same way.  The docs aren't as gospel as some think.  I have been through them; I've been through a lot of online docs.  It's obvious that GTK is exactly as is stated many places on the web - not well documented.  As I said before, there are obscure things that aren't mentioned anywhere.

For now, nothing really matters anyway.  I have it working.  And as it turns out, adding to the project adds more gtk buttons of varying types that all have to toggle with these 2 buttons.  The net result is that they need to be discreet functions anyway.

And you did notice the thread is marked as solved?

---

### Post by pconroy on 2012-02-26
> **anewguy said:**
> 
For now, nothing really matters anyway.  I have it working. 
And you did notice the thread is marked as solved?


I'm glad its working.  Since you've been in programming for a long time, like me, I'll offer up that 'C' is notorious for "apparently" working.  :)

I've been programming in 'C' since the mid 80's and have found that paying homage to the keywords like 'const' have been invaluable.  I also refuse to let any compiler warnings go untouched.

valgrind is another wonderful tool to use from time to time.

---

### Post by anewguy on 2012-02-26
I'm sorry - I didn't really mean to be a butt-head.  With my systems programming background I know I shouldn't be as loose with the code as I am right now.  I have 4 things "working" on the screen right now - the main color selection box, 3 radio buttons that belong to a group, and each of the options that goes with those buttons - file selection box, color button and 2 color buttons and simple text combo box respectively.

The probem is that I know somehow I'm just getting lucky that it appears to work.  I have a "zillion" warnings when I compile - some of the casting errors I'm not sure matter or not, but there are other things I'm sure matter.

So, now that I got to where the major things "work" for color and background choices, I want to go back through the warnings and clean things up.  I'm hoping I even understand half them now as I'm just too rusty with my C.  I know there has to be a serious error in there somewhere, since when I activate that screen memory usage goes up and is never released with the program exits.  I'm *hoping* it's something with GTK about releasing or destroying some of the things I've used but since I can use GTK the way I want to so far doesn't mean I understand all of it yet, so it will take a *LOT* of reading and searching to figure it out.  I'm just hoping that I haven't done some things that are going to require some larger rewrites, as I *thought* I understood what I was doing with some of this now.

Thanks for your input and your concern, and again I apologize for being a butt-head.  It's just  been a lot of frustration 1 thing after the next for things that really should be (and in reality probably are) easy.

Dave ;)

---

### Post by anewguy on 2012-02-26
Well, at least I have compiler warnings down to just casting.  A lot of the GTK functions that require a widget, and show in the docs as using a widget, seem to get nicked saying things like struct widget * expected but stuct window * found.  Change the defs around and the warnings just switch places.  Since the code matches the GTK docs and the online samples, I can only assume those types of casting warnings are going to occur.

Now, about that memory leak........I installed valgrind and the GUI for it (valkyrie?) and, well, lets just say that after exiting the program it was still updating the log - way over 9000 lines.  I have no idea at this time what's going on.

---

### Post by anewguy on 2012-02-27
Looks like the small cleanup I did to get the compile down to just the casting warnings also took care of the memory leak.

I was wondering, however, if there is a list of gdk and gtk items that require release or distruction prior to program shutdown.  I've seen a few individual things that mention it when searching the docs, but no general list of them all.

Thanks in advance!
Dave ;)

---

