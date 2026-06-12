---
title: "Xorg/Server ScreenSaver Lockup after Xorg 3/16 Update"
date: 2005-03-16
forum: Repositories &amp; Backports
---

### Post by mseney on 2005-03-16
Hey all,

This morning I sat at my Hoary Preview machine for just a few minutes and decided to check for some updates. Bam yes new ones, I smiled. So I noticed one for nautilus and xorg, etc. and afterwards logged out of Gnome and restarted the Xserver w/ CTL+ALT+BACKSPACE. I then logged back in and locked my screen and the matrox screensaver started and I shut off my monitor. I then decided to turn back on the monitor and shutdown the pc for the day only to find the machine totally locked. I powered it off and left for work. I will probably have to look in the xserver log later and see what happened but I'm guessing that the update maybe has a bug w/ OpenGL? I have a Matrox GL400 AGP card. Watch when I get home there will be an update that fixes this or something but hey I felt like making a post today heh.

~ Mike

---

### Post by mseney on 2005-03-16
Hrmm, now I am unable to simulate it again and logs aren't really pointing to anything. Maybe it was a fluke? Hey as long as it doesn't happen again all is well. Below is from the time last logged right before it happened this morning. I held in the Power Buttom until it powered off so this sort of doesn't make sense to me?
> 
Mar 16 06:08:09 localhost shutdown[10051]: shutting down for system halt
Mar 16 06:08:11 localhost gconfd (xxxx-9889): Received signal 15, shutting down cleanly
Mar 16 06:08:11 localhost gconfd (xxxx-9889): Exiting;
* xxxx = my username

---

### Post by mseney on 2005-03-17
Well it hasn't happened again, which is really good heh. Also note that there have been two (2) updates to xorg between last night and this morning. I am now running  6.8.2-5.1. I love updates!

---

### Post by LongTooth on 2005-03-17
Let me jump in on this one. Not with any advice but with a cry for help. I too checked for updates last night. Did them, surfed the net for a while before I shut the machine down. And this morning I can't log in. My PC starts up and I get this error message:

"I can not start the Xserver (your graphical interface). It is likely that it is not set up correctly. Would you like to view the Xserver output to diagnose the problem". 

Which I do and of course I can't make heads or tails of it. I end up at the log on screem where I log in but no GI interface. A 'startx' will do nothing but give me some error messages I can't understand. 'GDM' will inform me that only 'root' can start GDM. When I use 'sudo gdm' I get the message that it can't run Xserver.

Luckily I have another PC I can use to write this. So all communications is not lost. But woe is me. Woe is me.  

And here I sit. Not know where to go from here. I've put a lot of work into this system and I'd like to save it. Can't bear to think of starting all over again. Can someone give me a hand? Thanks.

---

### Post by oracledarren on 2005-03-17
Just a note but ...

I have now got into the habbit of reconfiguring xserver if i notice it is being reinstalled

as superuser its just dpkg-reconfigure xserver-xorg

and this resolves any of the issues occuring in the first place.

As for the monitor and screensaver, I suspect that it is probably a case of your monitor getting locked.  If you are still able to get to the menu on the monitor try degaussing it from time to time, that would also prevent any locks like that too.

Hope this helps you guys and it is not teaching you to suck eggs etc hehe

Take care

---

### Post by LongTooth on 2005-03-17
I saw this at another post. The same 'dpkg-reconfigure xserver-xorg' as yours. Boy, oh, boy! Was I ever glad to get over this problem. I had put so much into my Hoary that I dreaded a reinstall. I'll make a note of this tip just in case and keep an eye on what is being upgraded. By the way, what caused the problem? I know this has never happened to me before. 

One other thing, did this have any effect on my Nvidia driver? Is that anything I should be concerned with. 

And last be not least, thanks once more.

---

### Post by oracledarren on 2005-03-18
As far as I know it shouldnt do, the driver itself is setup elsewhere for NVIDIA the xorg bit is simply reseting the config back to what it should be when you originally configured your box (apt i believe installs the standard distributed config)

By the sounds of things though it all worked and you are a happy bunny  :p

---

