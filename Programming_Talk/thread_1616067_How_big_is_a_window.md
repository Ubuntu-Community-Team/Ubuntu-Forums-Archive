---
title: "How big is a window?"
date: 2010-11-07
forum: Programming Talk
---

### Post by worksofcraft on 2010-11-07
Not that long ago I started a simple project to make a [new terminal emulator]("https://launchpad.net/biditerm") that supports bidirectional text working with the KISS bidi-text algorithm from yours truly :P

So after a quick test of concept coding start I kind of got stuck into some other projects but subconsciously it musta been in my mind because I think I'll go finish it now as my first priority.

After a quick incursion into X11, Qt, proportional font spacing and the idiosyncrasies of Gtk::Textview I decided the right way to do this is by allocating an n*m character matrix for the display and simply scaling that to whatever size the window is on a Gtk:: DrawingArea (which is fundamentally the same thing as an X11 window with some higher level graphical abstractions).

So what about history that scrolled off the screen you may wonder?... well that's where polymorphism comes in. This terminal emulator is a base class, and we can derive from it to make one with a history... but even so I would put it in a drop down menu to open a history window and not as a scroll facility of the main window as other terminal emulators have done.

... and what about proportional fonts then and when they are all scrunched up because the user shrunk the window? Well easy... if you shrink the window your glyphs all shrink with it and I'm going to ignore the font spacing metrics and simply plot each one at it's appropriate position in the orthogonal matrix: Keep It Simply Stupid - end of story.

So what I'm wondering is if anyone wants to offer constructive criticism of my "back of a Ciggy-packet design" before I start coding the next phase?
;)

---

### Post by nvteighen on 2010-11-08
Pardon, but what's the issue with GtkTextView... ok, yes, it's a bit "cumbersome" because it follows an MVC design pattern, separating GtkTextView and GtkTextBuffer as Model and View, respectively, and the set of callbacks as Controller... But, that's actually a great design, IMO.

The problem I see could be summarized with a question: What about ncurses?

Like it or not, ncurses needs a terminfo-based terminal and yours is not... you're developing a POSIX incompatible terminal and you'll soon see many common applications fail because they won't be able to set attributes they assume to be in any terminal, emulated or not. And like it or not, stuff as essential as the less pager (therefore, the manpage reader) needs ncurses...

An emulator is an emulator, not a new kind of terminal. You have to follow the interface the programs are expecting from a regular Linux console... ok, you can expand its functionality, but you have to comply to what's expected to work and how it is expected to work.

What I fail to see in your graphical-based approach is that emulation layer... there's something missing between the "client" program and the particular way you've found to display text on screen. You seem to assume all a program does to a terminal is I/O, but that's false, as there are two APIs for terminal manipulation that you have to offer "bindings" for: terminfo and termcap (that should make ncurses and everything work as it should)... well, termcap is almost obsolete, but I read there's still some stuff using it.

---

### Post by worksofcraft on 2010-11-08
> **nvteighen said:**
> Pardon, but what's the issue with GtkTextView...
Well no, that's not my issue with GtkTextView at all. In fact the first draft of my "biditerm", which is the one on launchpad explicitly uses GtkTextView. The problem with this widget is it's integral logic for rendering text: It bases assumptions about directionality on the character set and sadly when mixing text from left to right and right to left character sets it behaves erratically. Similar problem with QT.

> **nvteighen said:**
> 
The problem I see could be summarized with a question: What about ncurses?

It's a good thing you ask. ncurses et al. address the display as a fixed pitch character grid and so it malfunctions when you work with proportially spaced fonts. Support for ncurses is however an imperative design objective for my terminal emulator and your PycTacToe game as well as the snakes game I saw elsewhere are intended test cases. I am fully aware of the need for terminfo support and I had already started on experimenting how to do that (not sure if it is in the version on launchpad atm).

What you must realize is that this is a **new project** and so far I have only spent a few hours on it. Most of that was researching **how** to do things. Thus the code is only at the proof of concept stage... or in the case of GtkTextView and QT at the stage of proving that they were not suitable.

> **nvteighen said:**
> 
An emulator is an emulator, not a new kind of terminal. You have to follow the interface the programs are expecting from a regular Linux console... ok, you can expand its functionality, but you have to comply to what's expected to work and how it is expected to work.

This is where terminfo comes in. The terminal emulators that are based on the vte widge take the view that terminfo defines what functions the terminal should emulate. However that **NOT** is what terminfo was designed for. Terminfo is there to tell host computers about what functions a terminal device **does** support! So like if you plug in a genuine VT100 terminal as opposed to say VT220 then the system knows what escape sequences work and what ones don't: The "dumb" terminal does not get instructions from terminfo about how to behave.

Certainly there will be a minimal set that is required for ncurses to be able to work. e.g. I have already established that if I don't include a "clear to end of line" escape sequence in my terminfo database, other programs actually generate a whole series of spaces (depending on the cursor position and terminal character width) and then back space to where it was. A yet to be answered question is what minimal set of terminal capabilities would be required for effective operation as I really don't see the point in duplicating all the logic that is already present in packages like ncurses.

While vte widget does have comprehensive support for all the possible terminfo/termcap entries... to the extent where you can't even fit them all in the same terminfo entry... it completely fails to render right to left text. This is for the simple reason that there is no such concept in the terminfo repertoire.

NOte: When I think of the legions of software contractors financed by middle-east oil wealth who got rich programming support for Arabic onto ancient text terminals... and the number of such terminals that were sold to those countries... it really makes me wonder what they thought they were achieving without addressing the problem at it's root :shock:

---

### Post by worksofcraft on 2010-11-08
ANyway... thanks for those thoughts. IDK how you guys go about designing something from scratch but I seem to need lots of input to help me get a clear vision of what I'm actually aiming for.

So back to the real topic... you see there is a command line utility called "resize" and with the -s option specifying rows and columns (yes it IS in character postitions so once again proportional fonst don't work here!)...

... well it resizes the text terminal dimensions and obviously one can't do that with a physical terminal! So just what would you expect it to do?

In my mind it sets the number of rows and columns that your terminal can handle. Gnome-terminal actually changes the window dimensions to match... not sure what it does when it won't fit on the screen... However to my way of thinking it should simply rescale the graphics to fit so many rows and columns in the window that you already got :shock: Or at least fit one dimension and have the other as a scroll bar that you can accommodate by resizing the window if necessary...

So from that you can see that to my way of thinking, resizing the window does NOT change the terminal "dimensions" in terms of rows and columns of characters.

That brings me on to a real issue: line wrap. I see two main possibilities... One is where the lines wrap onto the next line and the other is where they simply get clipped by the eastern margin. Now I like the idea of case 2 where you simply set a larger width and all the clipped text appears then! What do you think?

---

### Post by nvteighen on 2010-11-09
I've been researching about this quite a couple of hours.

Let's see, when I talked about "terminfo", I was confusing it with "termios", which is what I wanted to mean. That's the POSIX terminal interface (serial port I/O, actually) you have to comply with in order to emulate a terminal. Of course, this means you have to create a serial port in order to make this work and have programs be "tricked" to run on your terminal.

I know ncurses very well and I can tell you it's not only based on character display. For instance, it sets cooked/raw mode, creates a particular non-blocking input system, it can handle mouse events, etc. All of this has to be addressed in your terminal, of course.

But those are just details I wanted to clarify. My actual point is the following:

I fail to see what plans do you have to make a GtkDrawingArea be able to act as a text area such that it can emulate everything a POSIX terminal can do. I don't say it's impossible, I just think it's over-complex: you'll have to create something that takes the "drawing" in the GtkDrawingArea and converts it into text so that the serial port accepts it... and viceversa with input. Remember programs will have to be tricked to use your terminal for stdout and stdin when executed from there, for example. In the end, I fear you'll be implementing something almost like an OCR recognition system.

IMO, you need to use a text-based "something", or at least not a pixel-based one.

According to my experience, GtkTextView works flawlessly for this... I've been able to code a simple textbox and start playing with Arabic, as you can see in my picture (I don't know any... just typing random letters... I hope not to have written anything offensive by chance). It's as easy as changing the keyboard layout, which is the correct way to change scripts, not typing Unicode directly; this is what Pango-support is really about. It doesn't behaive erraticaly at all; if you've got any trouble manipulating text in a GtkTextView, chances are you were using GtkTextIter incorrectly or maybe not even using it (in my code, I don't use any as it's irrelevant... I'm not manipulating the text input).

Here's the code, compile it and play with it... I haven't seen any issue with it; even line-wrapping works flawlessly.

(In the screenshot, you'll see that I originally split the code into several modules and even used a Makefile to compile it... well, that's because I used this occasion to test some other stuff which I've removed from the code below :P):
```

#include <gtk/gtk.h>

GtkWidget *make_my_window(const gchar *title, gint size)
{
    GtkWidget *window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_window_set_title(GTK_WINDOW(window), title);
    gtk_window_set_default_size(GTK_WINDOW(window), size, size);

    g_signal_connect(G_OBJECT(window), "delete-event", 
                     G_CALLBACK(gtk_widget_destroy), 
                     NULL);
    g_signal_connect(G_OBJECT(window), "destroy", G_CALLBACK(gtk_main_quit), 
                     NULL);

    return window;
}

GtkWidget *make_my_text_area(void)
{
    GtkWidget *text_view = gtk_text_view_new();
    gtk_text_view_set_wrap_mode(GTK_TEXT_VIEW(text_view), GTK_WRAP_WORD_CHAR);

    GtkWidget *scroll_win = gtk_scrolled_window_new(NULL, NULL);
    gtk_scrolled_window_set_policy(GTK_SCROLLED_WINDOW(scroll_win),
                                   GTK_POLICY_AUTOMATIC,
                                   GTK_POLICY_AUTOMATIC);
    gtk_scrolled_window_add_with_viewport(GTK_SCROLLED_WINDOW(scroll_win),
                                          text_view);

    return scroll_win;
}

int main(int argc, char **argv)
{
    gtk_init(&argc, &argv);

    GtkWidget *main_window = make_my_window("Window", 300);
    GtkWidget *text_area = make_my_text_area();

    gtk_container_add(GTK_CONTAINER(main_window), text_area);

    gtk_widget_show_all(main_window);

    gtk_main();

    return 0;
}

```

---

### Post by worksofcraft on 2010-11-09
> **nvteighen said:**
> 
Let's see, when I talked about "terminfo", I was confusing it with "termios", which is what I wanted to mean....


Ah ok, that's alright then.. I already worked all that out... that's mostly what the version of biditerm on launchpad was about. Admittedly I didn't put any mouse events in and hadn't got round to the cursor movement although that's not exactly going to be like "rocket science".

> 
...In the end, I fear you'll be implementing something almost like an OCR recognition system.


lol no, I just maintain a rectangular grid of characters to plot at each position. The drawing area is only for display.
Things like ncurses define positions in terms of characters and that doesn't work with proportional fonts so I need to work with pixel positions when moving the cursor up and down.

> 
According to my experience, GtkTextView works flawlessly for this... 
Here's the code, compile it and play with it... I haven't seen any issue with it; even line-wrapping works flawlessly...


Yes thanks for that :)

With QT the problem I had was it placing single digit numbers at the wrong end of the Arabic text and then it "hopped" them over to the other end when they went into double digits. ATM I can't remember what problem I ran into with GtkTextView, but if I can make it behave sensibly then that will be much easier...

... so I copied your code... alas the gremlins musta been at my computer in the night because trying to compile it I'm getting:
```

$>  gcc bidiview.c `pkg-config --cflags --libs gtk+-2.0`
/usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../lib/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld returned 1 exit status


```

I'm sure that's a "main" I see there so I think ld is having me on :confused:

---

### Post by worksofcraft on 2010-11-09
Anyway ok so the gremlins left and your suggestion of changing the keyboard is a big help too :)

So what's the problem with GtkTextView?

Well try this: Type some English then switch to Arabic keyboard and put in some Arabic... Note: indeed I can't read it either so I also hope I'm not typing utter profanities in my ignorance. I did go to [google translate]("http://translate.google.com/#") and got the Arabic word "Camel" but when I pasted it into the text view it looked NOTHING like what the one from google looked like :shock:

Whatever, now we go back to our US keyboard and wish to continue our English sentence with a number after the Arabic word. Unexpectedly it appears to the **left** of my Arabic, but... hang on... I was back on US keyboard and I wanted to continue on to the **right** like it does with English letters :confused:

Well it's not just numbers... I mean I switched back to US keyboard and instead of ) it puts in a ( and so on it goes... I'm sure it's all really intelligently designed and expertly coded in accordance with the Unicode standards, but I'm sorry Mr and Mrs consortium attendants... I really can't work with it :P That's why I want **to create** something **simple** that even I can understand :D

---

### Post by nvteighen on 2010-11-10
> **worksofcraft said:**
> 
Whatever, now we go back to our US keyboard and wish to continue our English sentence with a number after the Arabic word. Unexpectedly it appears to the **left** of my Arabic, but... hang on... I was back on US keyboard and I wanted to continue on to the **right** like it does with English letters :confused:

Well it's not just numbers... I mean I switched back to US keyboard and instead of ) it puts in a ( and so on it goes... I'm sure it's all really intelligently designed and expertly coded in accordance with the Unicode standards, but I'm sorry Mr and Mrs consortium attendants... I really can't work with it :P That's why I want **to create** something **simple** that even I can understand :D

Interestingly, Gedit does all of this perfectly well :P Try typing on Gedit changing layouts back and forth and you'll be surprised. So, this has been done before; the issue is we both don't know how to do it :D

EDIT: No, wait, my program does it right too... Ok, there are times where some weird stuff happens, but if your right-click on the GtkTextView, you'll get the menu for inserting a Unicode control character to fix it the way you like.

---

### Post by worksofcraft on 2010-11-10
> **nvteighen said:**
> Interestingly, Gedit does all of this perfectly well :P Try typing on Gedit changing layouts back and forth and you'll be surprised. So, this has been done before; the issue is we both don't know how to do it :D

EDIT: No, wait, my program does it right too... Ok, there are times where some weird stuff happens, but if your right-click on the GtkTextView, you'll get the menu for inserting a Unicode control character to fix it the way you like.

lol - well once again thanks for that tip :)
I hadn't realized there was a LRE/RLE/RLO/LRO/LRM/RLM insert option on right clicking :D... I do remember finding it quite difficult to get the order I wanted when typing bidi text into my source code with gedit and eventually I just put "'s in and pasted the Arabic in there "Xft: ""&#1575;&#1576;&#1578;&#1579;&#1580;"" € ""&#38646;&#22777;&#36144;&#21441;"
I would not have wanted to insert directional overrides because I wanted to see what it does with a known sequence of codes. Note: Chinese is neither l2r nor r2l and can be even written d2u and u2d :shock:

However I think my point still remains valid: It's far too convoluted deciphering whether I have a strong/weak character l/r switch and which one of those 6 overrides I need... specially where part of the output is being generated externally by something like gettext.

IMHO all one needs are **TWO** directional codes: one to say "here comes some l2r" and the other to say "here is r2l". When we use the wrong one then our text comes out back to front, which is really quite easy to spot and if consistent and predictable it is also very easy to fix. For those cases where there are **no** directional codes embedded we just have a default direction toggle for the whole window, so the user can flip it at will :P

I suppose we know not how usable my idea will be in practice until I get it to work. Meanwhile I'm discovering about all sorts of stuff :)

---

