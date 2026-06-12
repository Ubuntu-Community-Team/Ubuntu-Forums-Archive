---
title: "GTK2 GUI, Infinite loop problem"
date: 2006-04-13
forum: Programming Talk
---

### Post by Aielyn on 2006-04-13
Hi all,

I am working on developing a simple binaural beat generator program (coding in C, not C++), nowhere near as powerful as SBaGen, but made specifically for ALSA audio (SBaGen is OSS-based, and doesn't seem to like AOSS on my system - I get a segfault) and realtime adjustment of output (so you can change the beat/carrier frequencies while it is running).

I already have a starter program to just handle the ALSA audio (console-based), which I used to teach myself ALSA audio coding. Works fine - Just input the carrier and beat frequencies as arguments on the command line, and it produces the desired output. Only problem, which I decided not to try to fix, was that I had to quit the program with a ctrl-c, as there is an infinite loop generating the sound, and I didn't have the patience to code up the necessary changes to have kbhit() working.

That starter program was coded up with the help of DiaSCE.

Now I have produced a GUI using Glade (in addition to DiaSCE) for the second program (the realtime one), and as a first attempt I transferred the code (slightly modified) to the "ON" button click function on the GUI.

Now for the actual problem - As it has been coded so far, when you click on the "ON" button, the GUI freezes (with the button still pushed in), and the sound is generated, but the only way to stop the program is to force it to end by repeatedly clicking the X in the top right corner.

I am assuming that this is because the "ON" button click function doesn't end (due to the infinite loop), but I cannot see how to circumvent the problem. Does anyone know how I can have an infinite loop generating sound without causing the GUI to freeze?

Please note that I am a novice at coding in C (I have more experience in Java and in Matlab).

---

### Post by nagilum on 2006-04-14
GTK runs its own endless loop to process user events like mouse moves etc. Now your sound output runs forever and prevents the events from beeing processed and the GUI freezes.
There are some things you can do about it. The easiest would be to use the gtk_events_pending() and gtk_main_iteration() functions within your audio-loop to  explicitly check for events and process them (see [http://developer.gnome.org/doc/API/2.0/gtk/gtk-General.html#id2699286](http://developer.gnome.org/doc/API/2.0/gtk/gtk-General.html#id2699286)). Another way is to make your application multi-threaded, your audio-loop will run from a seperate thread in parallel to the GUI stuff. This is the cleaner way but requires more work (see [http://yolinux.com/TUTORIALS/LinuxTutorialPosixThreads.html](http://yolinux.com/TUTORIALS/LinuxTutorialPosixThreads.html)).
You can also use forking but that requires some inter process communication to start/stop the audio loop.

HTH

---

### Post by Aielyn on 2006-04-15
Thanks, Nagilum. I'll have a go at what you suggested.

EDIT: I've implemented the multi-threading that you suggested, and I got it working. Thanks for your help.

---

