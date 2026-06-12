---
title: "Nothing can play AVI files - please help!"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by unknownwarrior33 on 2008-11-10
I've tried using every player known to man; Totem (default and xine versions), Kaffeine, MPlayer, Xine, Amarok, and Dragon Player, to name the ones I can think of off the top of my head.  I've looked at topics about similar problems, and downloaded every package they've mentioned, but nothing happens.  When I try to open an AVI file with Totem after running it through the terminal, I get this:

> The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 56 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
MPlayer gives a similar error.  Kaffeine and Amarok play only the audio.  Xine shows a window and quickly closes before I can even open the file, but that's a different problem.  Any ideas?

---

### Post by keplerspeed on 2008-11-10
Have you tried VLC? i believe this is the best video player, try it out, it is avaliable via synaptic.

---

### Post by unknownwarrior33 on 2008-11-10
VLC gives me the same sort of error.  Are there codecs I'm missing?  I feel like I've installed all the necessary packages, but I could be wrong.

---

### Post by patrickballeux on 2008-11-10
That looks like a memory issue or graphic issue.  

1 - How much memory do you have on your PC? How much is free? (See in System Monitor)
2 - What is your graphic card model?
3 - Can you play 3d games?
4 - Is Compiz (3D effects) enabled (Preferences - Appearance).  If so, disable it...
5 - Open "gstreamer-properties" from a Terminal or using ALT-F2.  In the Video setup, select the X11 output and try Totem (Play with the different possibilities).


That's all I can say for now...

Let me know!



> **unknownwarrior33 said:**
> I've tried using every player known to man; Totem (default and xine versions), Kaffeine, MPlayer, Xine, Amarok, and Dragon Player, to name the ones I can think of off the top of my head.  I've looked at topics about similar problems, and downloaded every package they've mentioned, but nothing happens.  When I try to open an AVI file with Totem after running it through the terminal, I get this:


MPlayer gives a similar error.  Kaffeine and Amarok play only the audio.  Xine shows a window and quickly closes before I can even open the file, but that's a different problem.  Any ideas?

---

### Post by bryncoles on 2008-11-10
just wondering, have you installed ubuntu restricted extras from synaptic....? maybe thats the problem....?

---

### Post by unknownwarrior33 on 2008-11-10
Turning off the Compiz effects did it.  Thanks!

---

