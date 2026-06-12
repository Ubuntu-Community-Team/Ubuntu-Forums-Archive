---
title: "[SOLVED] Can't even get to login..."
date: 2008-08-05
forum: New to Ubuntu
---

### Post by I am &gt;= Wes on 2008-08-05
My friend gave me a computer to run ubuntu on.  I love him for it because I can't run it on any of my computers because they're owned by my parents who won't let me install it.  

Beyond this, we installed ubuntu 2 days ago and it worked fine.  Today it decided not to work.  I first noticed something when I couldn't open the terminal, it was just a pure white box with no text.  My friend told me to do something that didn't work at all, I can't even remember what it was.  Now when I start up the computer it goes through all the motions but once I get passed the loading screen I get a black screen with a blinking white cursor.  The cursor blinks twice and then disappears so that I'm only left with a black screen.

I have been told that this problem is caused by the X server.  I'm not quite sure what to do to fix it.  Please help.

With boundless respect,
--Wes

---

### Post by tuxxy on 2008-08-05
Yes it sounds as if it is a X issue, ok when you get the screen try pressing CTRL + ALT + F1 to bring up a terminal.  

Now you could try and reconfigure the xorg by entering this command and follow the process through.  

```
sudo dpkg-reconfigure xserver-xorg
```

This should then bring you back into GNOME you may need to reboot, if you have to do this from terminal type

```
sudo shutdown -r now
```

---

### Post by I am &gt;= Wes on 2008-08-05
Thank you very much.  I knew I had to use a terminal command of some sort, but I wasn't sure quite what it was or even how to get to the terminal, seeing as how all I had was a big black screen.  I can't thank you enough.

---

### Post by bpowell2005 on 2008-08-05
I've dorked up my xorg settings before too, and have been lucky to just reboot and at the Grub menu, select the "recovery mode" and boot into that....I then just do a restart, and my original installation is working again...I don't know what happens there, but it's nice!

---

### Post by tuxxy on 2008-08-05
No problem wes, let us know if you get it back up and running :)

---

### Post by I am &gt;= Wes on 2008-08-06
Yes, the terminal method worked, everything is up and running.  I have a messed up screen resolution though.  I'm using my 30" wide screen TV and sadly have to connect via an S-Video cable.  Ubuntu is only allowing me to choose 800x600 or 640x480 in the screen resolution window under system preferences.  Everything is giant on the screen and it's bothering me because I had it at a higher resolution before.

Is there some way that I can set it higher?

---

### Post by tuxxy on 2008-08-06
If its an nvidia card you could try running nvidia-settings or install it

---

