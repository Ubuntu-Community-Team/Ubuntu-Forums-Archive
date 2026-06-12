---
title: "Greeting application crashes during boot"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Gow524 on 2008-08-19
Hi, 

I need some serious help to get my laptop back.  I am totally new to Ubuntu.  I don't know how to navigate in the command line or the necessary commands to repair my problem.  I have Ubuntu 7.10 install and I was customizing my desktop when I got the error. I want to change my my default log in background.  So, I down loaded some backgrounds and it work ok.  I kept changing the log in screens to see the difference and which suit me best.  On the last attempt I install one and then reboot it to see it.  And thats when I end up with the following error "greeting application crash" follow by "click ok" to continue as Ubuntu attempts to use a usuable log in background, only go into a loop.  

I have try the Ctrl+_Alt+F1 keys which takes me to the command line.  I input the info, and it seems to work except I don't know what else to do after that.  My screen name is visible and it works, my password I just don't know because its obscure and I can not tell if it work.  So, I go back to Ctrl+Alt+F7 to swap to the graphical side and I end up with the same error loop.

So, how I remove or go back to the default background log in menu? 

Help, anybody?

---

### Post by meanburrito920 on 2008-08-19
in the console, type startx to get a desktop running. this will bypass gdm's start screen. Then go and revert the setting using the gui tool you used in the first place.

---

### Post by Gow524 on 2008-08-20
Thanks man, I will give it a shot.  You rock!  Do you recommend any books on the ubuntu and the command line?

---

### Post by Gow524 on 2008-08-20
Hi again, I am sorry to report that it didnot work. What I got is as follows on the command line;

Fatal Server error:
Server is already active for the display 0
if this server is no longer running, remove /tmp./.xo-lock and start again

follow by the following;

Xlib: connection to ":0.0" refused by server.
Xlib: Invalid Mit-Magic-cookie1 key
giving up
Xinit: unable to connect to X server
Xinit: No such process (error 3): server error.
Luis@Luis-laptop:~$

What I did was to turn on the laptop, then Ubuntu attempted to boot only for the greeting application to crash.  At that point I press the Ctrl+Alt+F1 key which took me to the command line.  Then, I typed the startx and got the error message above.

What am i doing wrong? and why can I by pass the greeting error?

---

### Post by meanburrito920 on 2008-08-20
at the command line, type 

$ killall gdm

it may give you an error about permissions, if it does, then type

$ sudo killall gdm

Your problem right now is that it is already running a session of X. If it still isnt working, type $ ps -e | more
and find the PID of your Xserver, then kill it with

$ kill PID (where PID is the PID number of your Xserver)

also, try using startx multiple times. sometimes it allows you to start another server simultaneously.

---

### Post by Gow524 on 2008-08-23
thanks, it work. I managed to get into my desktop, however when I try to access the "Login Window" under System to set the default log in screen, the "Login Window" is not  available under system on the desktop.  Do I have to re-install Ubuntu?

---

