---
title: "GUI problem, no desktop loading"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by ilseraeves on 2012-04-21
first of all: I'm just a beginner so please forgive me
problem: I think there is something wrong with the GUI:confused:
how or when did it happen: I was using VLC media player to watch a video on my tv via my laptop (so with video cable)
after wathcing the video I closed of my programs and laptop, same way I usualy do, via the menu to stop, so not via button on laptop.
next time I started my laptop again, I got the grub menu (I have dual boot: windows XP pro & ubuntu 11.10 oneric)
when I selected to start ubuntu, I saw the start thing (with ubuntu and the dots) but I did not get to my desktop
The only thing that still works is to start in "herstelmodus" (fixmode? sorry, I speak Dutch) and I can get to the Kernel
I tried a few standard sollutions I found in the community, but no luck.
Can anyone please help me, I can not fix it and (stupid me) I did not back up all my files yet, so there are still a few photo's 
and some mail items on that I would like to have back before I have to reinstall the thing (If needed ofcourse)
maybe there is some way to copy my files before reinstalling?
But ofcourse I would prefer a simple fix :-)
THANKS in advance!

---

### Post by cmcanulty on 2012-04-21
if it gives you a command prompt try reading this
[http://askubuntu.com/questions/1220/how-can-i-restart-x-server-from-the-command-line]("http://askubuntu.com/questions/1220/how-can-i-restart-x-server-from-the-command-line")
or also try ctrl+alt+t to get a terminal to open then do as article suggests won't hurt anything

---

### Post by ilseraeves on 2012-08-19
tried it, no luck, tried several other things I read in suggestions, no luck again
is there a way I can copy my files to a usb stick so I can reïnstall the thing?

thank u

---

### Post by Jimmyfj on 2012-08-19
If you in any way can make yourself the root user try the command:

```
dexconf
```

Thes should generate a new x-conf.

---

### Post by LordEager on 2012-08-19
You say you don't get a desktop, but you should be more precise, do you get the display manager (login window) ? Are you able when in the black screen stuck, to switch to an xterm by pressing ctrl+alt+F3 ? In any case you can backup all data you want to a USB stick through the recovery mode.

---

### Post by ilseraeves on 2012-08-22
by no desktop I mean the graphic interface, the desktop manager, the screen I should get when I log in, with al the menu's and stuff, like I used to get, like you get in windows

---

