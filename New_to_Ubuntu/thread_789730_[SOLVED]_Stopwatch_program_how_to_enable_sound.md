---
title: "[SOLVED] Stopwatch program: how to enable sound?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by grashdur on 2008-05-10
I'm using the Stopwatch program (version 3.5, downloaded straight from Add/Remove Programs). It would be a lot more useful if it would give some kind of audible notification when time reaches zero. The instructions for the program say that it activates some kind of bell sound, but in actual use it's silent. Does anybody know about this?:confused:

---

### Post by grashdur on 2008-06-10
I hope this fix is helpful to somebody: 

This little program, written by Don Libes, is available in the repositories. Without tweaking the program, Stopwatch is unable to make a notification sound when it reaches zero (at least in Ubuntu, and on my computer). You can find its program file in /usr/bin.

Once you open the program file, there's a place at the top where you can make easy changes, like making the program not display milliseconds, and count down (“backward”) by default -- depending on your individual tastes and needs.

To make a functioning notification sound, you can replace the command “bell” (do an auto search in the Stopwatch program file to find it) with “exec aplay -q [path/filename]”. 

For those of you as ignorant as I am: “Exec” means execute a command; “aplay” is the command that will play a sound file, “-q” will prevent some random error message from coming up and freezing the program when it stops and plays this file. You need to type the full path and filename for the desired sound file. (You can paste your sound file into the folder of your choice so that it will be available for this command to use.) So, for example, the full line to type or paste in here could be, “exec aplay -q /etc/gong.wav”. 

Also for those like myself: Remember that everything is case-sensitive, including the file name. And if you don’t find the program file, you can type “which stopwatch” at the command line and you’ll get its full path/location.

Once you save these changes, the Stopwatch program will work perfectly for you. I recommend it. :KS

---

