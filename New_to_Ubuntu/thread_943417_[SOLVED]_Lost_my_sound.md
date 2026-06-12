---
title: "[SOLVED] Lost my sound"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Chris Edgell on 2008-10-10
Two nights ago I was hearing videos, but the following day when I tried to listen, the sound was gone.  The sound icon on the top panel shows 100%, is there another place that I could have inadvertently muted the sound?

When I plugged in the light green insert-prong into the light green-marked hole for the first time three days ago-it didn't produce any sound--when I moved it to the purple spot just above--I got sound...but as I say two days later I had no sound and can't seem to find it no matter what I do.

Thank you

---

### Post by Pro-reason on 2008-10-10
Try the &#8220;alsamixer&#8221; command, and this guide: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting).

---

### Post by Chris Edgell on 2008-10-10
What IS a shell?  The white banner space in the top where you can type adresses or whatever?  (I'm thinking yes.)  So where do I type "alsa-mixer command.  I went to the guide and got mind-boggled...may try again after I find out where to put the alsa-mixer command.
Thanks

---

### Post by Orange_and_Green on 2008-10-10
> **Chris Edgell said:**
> The white banner space in the top where you can type adresses or whatever?

No, that's the address bar of your browser. To open up a shell, click on "Applications" at the top left corner of the screen, then "Accessories", then "Terminal".

You can think of it as an interface to navigate through your directories and files, and to launch programs, a bit like the DOS prompt was back in the day.

---

### Post by Pro-reason on 2008-10-10
On standard Ubuntu, it's a program called “Terminal”.  You can find it in the menus along with all the other applications.  Once it's open, you can do all sorts of powerful stuff by typing commands.

See also:
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by w4ett on 2008-10-10
Here is a good tutorial for using the Shell (terminal)

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by Chris Edgell on 2008-10-10
When I went into the terminal and entered Alsa-Mixer, it said, "Command not found"
But at least I learned where the terminal is located. Thanks to w4ett for where to find a good tutorial for using the shell. 

If I thank you individually "by star pressing", are you made aware of it?  Thank you all, I have so many avenues to go to study--I wonder if lots of people "here" are like me, not just new to ubuntu but to the computer in general.....

---

### Post by Pro-reason on 2008-10-10
> **Chris Edgell said:**
> When I went into the terminal and entered Alsa-Mixer, it said, "Command not found"

It's &#8220;alsamixer&#8221;, in lower case.

---

### Post by Chris Edgell on 2008-10-10
can't believe I didn't copy that as you originally stated-let me be more careful.

I've set volume control to 100% and now go to terminal to tell you what I see.
3D Contr and Mic Boos only have small sq. box containing letters MM.
Line-In says Bass Out.
Mic-In M says Center/L
IEC958 5 has that small box with MM inside

---

### Post by M4rotku on 2008-10-10
You could go into the volume control and see if anythings muted via that.  I find it more understandable than the 'alsamixer' command.

I know on regular ubuntu, one can simply right-click on the sound icon and choose to 'open volume control'.  Look around and make sure nothing relevant is muted.

---

### Post by Chris Edgell on 2008-10-10
Thank you Pro-reason for bringing me to the knowledge about terminal-what a study that looks like
Long story short-I have sound.  Don't really know how.
It was invaluable to see the panel volume and compare with the alsamixer graphic--It did dawn on me that the red zones at 100% were not good and I adjusted them to mid range...Like, could there be some guard that prevents blowing out your speakers... I don't know what else I did.  
It reminds me of that adage  "If it goes away by itself, it just might come back by itself"  but then again, there must be a more reasonable explanation, woukldn't you say, Pro-reason?  
Again thanks all.

---

