---
title: "Beginner trying to &quot;debug&quot; a X11 keyboard intercept program"
date: 2012-11-17
forum: Programming Talk
---

### Post by squakie on 2012-11-17
EDIT:  I've see there have been many people looking at this thread, and I suspect why.  So, if you are looking at this thread with the idea of finding some capture someone's keystrokes for your own use, you're looking in the wrong place.



I've been trying to help a user in the Absolute Beginners forum who wants to use the Dvorak keyboard layout but maintain some of the function keys (ctrl-c, ctrl-v, ctrl-w, etc.) as qwerty.  They point to [this]("http://code.google.com/p/dvorak-qwerty/downloads/list") link for program xdq.c. 

The user also pointed to [this]("http://askubuntu.com/questions/143573/is-there-any-way-to-use-qwertys-keyboard-shortcut-position-while-the-dvorak-lay") thread as the description of what they were trying to do, and the origin of looking at the xdq.c program.  From what I could gather, you start xdq in a terminal window, then open something like the editor and you should be able to do a qwerty ctrl-c with a dvorak keyboard layout.

I downloaded this, compiled it as per the comments in the program, remapped to dvorak and then started the program in a terminal window as per the instructions.  The keys appear not to be remapped.  After further "debugging" - I added some fprintf's to stderr - it appears that this piece of code is not trapping the key actions:


```
   for (;;) {
    XEvent event;
    XNextEvent(display, &event);

fprintf(stderr,"\ngot event\n");

    switch (event.type) {
      case KeyPress:  
      case KeyRelease: {
        if (event.xkey.send_event) {
          fprintf(stderr, "SendEvent loop?\n");
          break;
        }
.
.
.
.
.

```Looking at the documents I could find on line, and trying to understand them, I believe the structure "display" is still looking at the window the program started in, not at any other window.  The only place the structure "display" is set is at the very beginning of main() with this statement:

  Display *display = XOpenDisplay(NULL);

Which I understand returns the display structure for the default display as held in the environment variable "DISPLAY".

After getting the display, it sets a default window via:

  Window window = DefaultRootWindow(display);


Before it gets to the loop shown in the code snippet above, it never does anything more with display or window, leading me to believe it is only trapping X keyboard events for the terminal window it was run in.  I put the fprintf in after the:

    XNextEvent(display, &event);

to see if it ever got an xevent, and it never does hit the fprintf.  

This leads me to believe that it is looking for xevents only in the terminal window that xdq was run in, not from ANY X window opened, such as a gedit window.

I'd really like some input from someone who does understand the xdq program's usage of the X calls, and what might be done to actually trap events from any X window.  Also, please be sure to let me know what I might be misunderstanding - I don't have a clue about this X stuff outside of looking up the man pages, etc., on the net.

---

### Post by squakie on 2012-11-19
Ok, I *think* I understand very basically the display and window things used in the program, so it would appear it's supposed to pick up all communication between the xserver and the xclient, so it should the keystrokes from any window.  However, it still never reports anything on the fprintf following the xnextevent statement.

I decided to try xtrace to see if I could understand what was going back and forth and therefore maybe trace the problem.  Well, I can't get the xtrace to work.  I tried just xtrace and it wanted a default display - I tried :0 since that's the value of the $DISPLAY environment variable.  Got nothing.  So I tried the same thing with -o <filename> and the resulting file is empty.  I then tried xtrace -d: 09 -o <filename> (I did put my own file name in - just put the generic in what I'm posting here).  This results in an error message about something such that xtrace isn't even running.  

So, I could use some help getting xtrace to work as well so I can try to trace the problem.  Is there a possibility that none of this works for some reason in ubuntu 12.10 64-bit?

---

### Post by squakie on 2012-11-24
Apparently no one has a clue about this.  I'm leaving this open and will bump it from time to time in the hopes someone is able to give some help.

---

### Post by sqweek on 2012-12-15
For xtrace to be useful, you can't just run the program you want to debug as normal. You need to tell it to connect to xtrace rather than the normal X server. It has to be arranged this way, as it's not possible for xtrace or any other program to start inspecting the communication between an X client and server. (well, technically you can probably do that but only with root privs)

Looks like xtrace defaults to listening for connections as though it is an X server with DISPLAY=:9. So, after starting xtrace in one terminal, open another and run:

 DISPLAY=:9 xdq

and you should see the X protocol communication dumped in the xtrace window.

btw, if you haven't seen syntax like "DISPLAY=:9 xdq", it's shorthand for:

 export DISPLAY=:9
 xdq

except the one-line form only changes the environment of the newly spawned xdq process.


Disclaimer: i don't use ubuntu and haven't actually used xtrace yet, just stumbled on this thread looking for an x11 protocol monitoring tool and thought i may be able to offer some insight. As a dvorak user, i think the approach of changing letters when pressed with ctrl is pretty much bats**t crazy, but each to their own ;)

I've got some x11 debugging to do in the next few days, so if I notice any glaring errors in my description of xtrace I'll return to correct myself.

---

### Post by squakie on 2013-06-25
The user who needed this has moved on.

SOLVED? - NO

Me interested? - NO.

---

