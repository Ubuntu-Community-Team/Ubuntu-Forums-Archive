---
title: "Client for a remote control server in several languages, looking for BASIC pointers"
date: 2010-10-22
forum: Programming Talk
---

### Post by shehearsthem on 2010-10-22
**Sorry for the long post, I get lonely. short version: remote control for desktop media players based on remuco, looking for a couple of really simple tips (and maybe showing off). Scroll down past the code to get to the real meat.**

I'm interested in being able to control the music from anywhere in the house. Ampache with mplayer's demon is a good example of the idea.

In the repos and on google code is a package "remuco" which adds a very nice remote control to various desktop media players (such as Rhythmbox). It comes with clients for all kinds of java enabled phones. It's easy to use, it's pretty stable :-).

OK, but my girlfriend doesn't want to have to switch to my account to change the rhythmbox playlist.
AND when she gets her own computer, she should really be able to control my Rhythmbox from there.

Remuco almost solves this by creating something like a TCP server and hooking it up (through a plugin interface or dbus) to the desktop player. But as yet there are no desktop clients. Following is remuco's package description:

>  Remuco is a duplex remote control system for media players and mobile
 devices equipped with Bluetooth or WiFi. It allows you to control your
 favourite media player by switching to the next, previous, or any other media
 within your current playlist, as well as browse your media library, activate
 your other playlists, rate your media, adjust volume, and more. On the mobile
 device, it displays information about the current media, including cover art.
 .
 This package contains the base module as well as the client .jar for
 Remuco. You probably do not want to install this package directly, but instead
 install one of the adapters.SO....

Most likely there are tools out there to do exactly what I'm thinking :-).
But I have no internet connection at my house, and my brain is enjoying a bit of a workout making my own solution: A desktop client for remuco.



Remuco is all written in python and java, neither of which I can speak. So I basically have to do it all from scratch. That's not a problem really.
The server's protocol is some custom looking thing where most of the data is transmitted in binary. It was a real pain trying to work out how to read the messages, but I'm sure there is a reason for that.

I've got ~200 lines so far in php that allow me to read two types of messages (should be an extra five lines each for future messages) where a simple json_decode() is more along the lines of what I'm used to.

So yes, I'm having fun. (literally).
I basically can not adapt the python or java code to do my bidding (too lazy).


**The plan:**
- write a library in php which can compose, send, receive and parse the remuco messages (nearing completion)
- write a little CLI executable in php, utilising the library
- write a simple GUI to call and manipulate the executable, basically impersonating a media player frontend

**Benefits:**
- decentralised, democratic control of a centralised media library
- all the power of a desktop player, with basic control extended to a variety of locations
- I can switch to amarok or juk without my girlfriend noticing ;-)
- All the player interfaces are handled by the server, so I don't need to adapt the code for multiple players :-)

[B]Component 1 - Server:
[/B]This is provided by the package remuco-base and one or more player adapters. I don't need to touch this. It ships with support for most linux desktop music players.

[B]Component 2 - Client library:
[/B]I've almost completed this in PHP

**Component 3 - Client Executable:**
Because the client stuff is all abstracted, it is possible to have several of these!
1: Web interface - load the library in a php web page to provide a simple X/HTML interface to a player. I hope to write a BASIC little demo.
2: CLI interface - think "rhythmbox-client", but without the need to share an X session and without specifically requiring rhythmbox. This may be quite feature poor (play/pause, next, mute/unmute, previous, get_playing).
3: popen interface - For the fullest features, a popen() call where the language of your choice can manipulate stdin and stdout. I'm considering using JSON or similar to ship the data back and forth over the STDIO.

**Component 4 - GUI:**
If the client executable is of the popen-able variety (and maybe otherwise, in theory), it can be called and manipulated by a GUI. Which is basically the end result that I'm going for.



**Further Goals:**
I've had some slight experience in Qt4 and it is the most brilliant thing ever in C++. But I neglected to learn basic C, and in Ubuntu the focus is on Gtk. So now it's time for me to give Gtk a whack.
So I'll sharpen the saw in Python, C and GTK.


I'll post some code (without warranty and released by me as the author into the public domain, where applicable, or with the most liberal possible license otherwise). I apologize in advance for the total lack of comments :-(

This is all prototyping and making myself familiar with things.


Here's what my first "test" interface looked like, with the goal of simplicity:

```
   +------------------------------------------------------------------------+
   | O O O Chris's Controller:: Dethklok - Hatredcopter                     |
   |------------------------------------------------------------------------|
   | Play/Pause     |             |           |         |         |         |
   |----------------+-------------+-----------+---------+---------+---------|
   |                | Previous    | Next      |         |         |         |
   +------------------------------------------------------------------------+
```Which in GtkBuilder xml:
```
<?xml version="1.0"?>
<interface>
  <!-- interface-requires gtk+ 2.12 -->
  <!-- interface-naming-policy toplevel-contextual -->
  <object class="GtkWindow" id="window1">
    <property name="title" translatable="yes">Chris's Controller:: Looking for Rhythmbox...</property>
    <property name="window_position">center</property>
    <property name="icon">favicon.ico</property>
<!--    <signal name="destroy" handler="Gtk::main_quit"/>-->
    <child>
      <object class="GtkHBox" id="hbox">
        <child>
          <object class="GtkTable" id="table1">
            <property name="visible">True</property>
            <property name="n_rows">2</property>
            <property name="n_columns">6</property>
            <property name="column_spacing">2</property>
            <property name="row_spacing">2</property>
            <property name="homogeneous">True</property>
            <child>
              <object class="GtkButton" id="button2">
                <property name="label">Previous</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <signal name="clicked" handler="snkprevious"/>
              </object>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
                <property name="top_attach">1</property>
                <property name="bottom_attach">2</property>
              </packing>
            </child>
            <child>
              <object class="GtkButton" id="button3">
                <property name="label">Next</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <signal name="clicked" handler="snknext"/>
              </object>
              <packing>
                <property name="left_attach">2</property>
                <property name="right_attach">3</property>
                <property name="top_attach">1</property>
                <property name="bottom_attach">2</property>
              </packing>
            </child>
            <child>
              <placeholder/>
            </child>
            <child>
              <placeholder/>
            </child>
            <child>
              <placeholder/>
            </child>
            <child>
              <placeholder/>
            </child>
            <child>
              <placeholder/>
            </child>
            <child>
              <placeholder/>
            </child>
            <child>
              <placeholder/>
            </child>
            <child>
              <placeholder/>
            </child>
            <child>
              <placeholder/>
            </child>
            <child>
              <object class="GtkButton" id="button1">
                <property name="label">Play/Pause</property>
                <property name="can_focus">True</property>
                <property name="can_default">True</property>
                <property name="has_default">True</property>
                <property name="receives_default">True</property>
                <signal name="clicked" handler="snkplaypause"/>
              </object>
            </child>
          </object>
          <packing>
            <property name="padding">6</property>
            <property name="position">0</property>
          </packing>
        </child>
      </object>
    </child>
  </object>
</interface>
```Now here's the PHP version of the GUI (just quickly abusing rhythmbox-client for the test) ... Note the use of a main function - this is just to make the code a bit more analogous to the C and Python versions...:
[PHP]#! /usr/bin/env php
<?php
dl('php_gtk2.so');


function get_title() {
    return 'Chris\'s Controller:: '.`rhythmbox-client --print-playing`;
}


function snkplaypause() {
    echo `rhythmbox-client --play-pause`;
}


function snkprevious($widget) {
    echo `rhythmbox-client --previous`;
    $widget->window->set_title(get_title());
}


function snknext($widget) {
    echo `rhythmbox-client --next`;
    $widget->window->set_title(get_title());
}


function main() {
    $xmlFile = dirname(__FILE__).'/interface.xml';
    $builder = new GtkBuilder();
    $builder->add_from_file($xmlFile);
    
    $window = $builder->get_object('window1');
    $builder->connect_signals();
    $window->connect_simple('destroy', array('gtk', 'main_quit'));
    
    $window->show_all();
    $window->set_title(get_title());
    Gtk::main();
}


main();
[/PHP]And in python (my first python app ever, go easy)
```
#! /usr/bin/env python
# -*- coding: utf-8 -*-

import gtk
import os



def get_title():
    return "Chris's Controller:: "+os.popen("rhythmbox-client --print-playing", "r").read()

def snkplaypause(widget, window):
    os.system("rhythmbox-client --play-pause")
    
def snknext(widget, window):
    os.system("rhythmbox-client --previous")
    window.set_title(get_title())
    
def snkprevious(widget, window):
    os.system("rhythmbox-client --next")
    window.set_title(get_title())


def main():
    
    xmlFile = os.path.abspath("./interface.xml")
    builder = gtk.Builder()
    builder.add_from_file(xmlFile)
    
    window  = builder.get_object("window1")

    the_signals = {
    "snkplaypause":snkplaypause,
    "snknext":snknext,
    "snkprevious":snkprevious
    }
    builder.connect_signals(the_signals, window)
    window.connect("destroy", gtk.main_quit)
    
    window.show_all()
    window.set_title(get_title())
    gtk.main()
    
main()

```And finally in C, which I used to convert my PHP prototype to the python version (the amusement of API/binding differences :-))
[PHP]#include <gtk/gtk.h>
#include <stdio.h>


char* get_title() {
    FILE *fp;
    char path[PATH_MAX];
    char *feedback;    
    
    fp = popen("rhythmbox-client --print-playing", "r");
    if (fp == NULL) {
    return "Not Playing (Player not found? Error?)";   
    }
    feedback = "Chris's Controller:: ";
    while (fgets(path, PATH_MAX, fp)) {
    feedback = g_strconcat(feedback, path, NULL);
    }
    
    pclose(fp);
    return feedback;
    
}



void snkplaypause(GtkWidget *widget, gpointer data) {
    system("rhythmbox-client --play-pause");
}


void snkprevious(GtkWidget *widget, gpointer window) {
    system("rhythmbox-client --previous");
    
    
    gtk_window_set_title (GTK_WINDOW (window), get_title());
}


void snknext(GtkWidget *widget, gpointer window) {
    
    system("rhythmbox-client --next");
    
    gtk_window_set_title (GTK_WINDOW (window), get_title());
    
}


int main( int argc, char *argv[] ) {
    
    GtkWidget* window;
    GError* error = NULL;
    char* title;
    
    
    gtk_init (&argc, &argv);
    
    
    GtkBuilder* builder = gtk_builder_new ();
    if (!gtk_builder_add_from_file (builder, "./interface.xml" , &error))     {
    g_warning ("Couldn't load builder file: %s", error->message);
    g_error_free (error);
    }
    
    
    
    window = GTK_WIDGET ( gtk_builder_get_object (builder, "window1"));
    gtk_builder_connect_signals(builder, window);
    g_signal_connect (window, "destroy", G_CALLBACK (gtk_main_quit), NULL);
    
    
    gtk_widget_show_all  (window);
    gtk_window_set_title (GTK_WINDOW (window), get_title());
    
    
    gtk_main ();
    
    
    return 0;
}
[/PHP]C version should compile with the following:
```
gcc -o 'test' test.c -Wl,--export-dynamic `pkg-config --libs --cflags gtk+-2.0 gmodule-export-2.0`
```Note that rhythmbox-client seems to lean on dbus all the way so if it was strictly for rhythmbox it might be good to cut out the middleman... (And the unmute option doesn't work in mine!!)


**Time for the questions!**
First, on string concatenation...
```
    feedback = g_strconcat(feedback, path, NULL);
```The GTK+ docs where I read this stated:
> Concatenates all of the given strings into one long string. The returned string should be freed with g_free() when no longer needed.g_free() ?? Remember that I come from a background with garbage collection and don't laugh. How do I actually use g_free() in my code? Do I put it straight after my while loop? What exactly am I supposed to be freeing here? What happens when I don't free it?
Should I just be using sprintf()? (I know this is a terrible question,I googled it but the "normal" answer with malloc() or 65535-length strings makes me want to cut my face off)

Basically, if it is needed, can you just show me the code to demonstrate?
I'm going to finally do the UI in python with GTK (good gtk support, all comes preinstalled, easily patched by hand...) but I still want to know The Right Way of doing things.



SECOND QUESTION:
Besides object orientation (the messaging library is all done with classes and objects, but I didn't see a real need to go crazy on it in half a page of code) what can I do to just tidy it up?

Frankly it looks good to me, but is there some heinous mistake that I've made? Should I be declaring my own destroy/shutdown handler and referring back to it in the interface definition?
Should the UI be broken up into several files?
Is it wrong to write out the whole UI in XML? I notice that rhythmbox doesn't do it.


THIRD QUESTION:
To write the messaging/protocol code, I've had to refer back to the original python and java a lot. Nothing is directly copied, but some parts are obviously inspired by their serverside cousins.
If I were to distribute that component, would I need to make it GPL3 like the code that inspired it? Or could I give it a more open BSD or MIT style license (should I feel so inspired)? Can one even say for sure without seeing the actual code? I'd be best to ask the actual author, right?



Basically I think I've got it sorted for the most part but I'm certainly open to tips, especially about the string concatenation and memory freeing.
I have a casual interest in similar projects too, if you are using any.






Obviously one day I will have to learn some java.




Thanks in advance for your interest and any help you can offer!
If I don't reply it means I'm afk, but this is my first ever post to the internet so yes, I will come back and read it.

Have a day :-|

---

### Post by saulgoode on 2010-10-22
> **shehearsthem said:**
> First, on string concatenation...
```
    feedback = g_strconcat(feedback, path, NULL);
```The GTK+ docs where I read this stated:
g_free() ?? Remember that I come from a background with garbage collection and don't laugh. How do I actually use g_free() in my code? Do I put it straight after my while loop? What exactly am I supposed to be freeing here?
The glib string functions (that return char pointers) will allocate memory for the resulting string from the heap (free system memory). It is the calling program's responsibility to free that block of memory after it is no longer needed. In your code, the variable 'feedback' will point to the allocated block of memory. 

You would free the memory after the string is no longer needed. In the code you provided you would include a 'g_free()' at the end of your 'snkprevious' and 'snknext' procedures.
```
void snkprevious(GtkWidget *widget, gpointer window) {
    char *s;

    system("rhythmbox-client --previous");
    
    
    gtk_window_set_title (GTK_WINDOW (window), s=get_title());
    g_free(s);
}

```
> What happens when I don't free it? 

The allocated memory will not be available. If your program isn't using the memory, it should be free'd so that it can be used by other programs (or elsewhere by your programs). 

> Should I just be using sprintf()?
With sprintf, you'd still have to provide memory for a strcat operation. Unless you provide a static buffer, you would have to allocate/free some memory for the result. For dynamically allocated strings, you might as well let glib do the work. But if you know beforehand the maximum extent of the string -- and you are going to be do a lot of passing of the string between functions -- then you may want to employ a static buffer (char array).

---

### Post by shehearsthem on 2010-10-27
Hey thank you very much, Saulgoode :-)

The example is a BIG help, and I will follow your suggestion with the static buffer / char array. I was going to free memory in completely the wrong function.

I have a lot to implement for the little toy and there will be a LOT of passing string values between functions so it's good to know how to do it right.

Thanks again




EDIT: Not to get too carried away, but time to have a real play with valgrind...

---

