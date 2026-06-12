---
title: "Black screen after install proprietary nvidia driver"
date: 2013-11-27
forum: New to Ubuntu
---

### Post by nilsoncabrita on 2013-11-27
Greetings ...


I recently install Lubuntu 13.10 on my old pc, with nouveau drivers goes well but i can't watch videos in fullscreen on firefox they are very slow and i have to press escape several times to return to normal mode, i try to install the proprietary nvidia driver recommended by Lubuntu (version 173) installed without problems but when i restarted the machine after appearing logo Nvidia does nothing the screen goes black the features of my pc they are:


MSI 915GLM-V
Pentium IV 3.0 GHz
2 gb ram ddr (2x1024)
Point Of View FX5500 256mb AGP
DD Wester Digital 80GB Sata


Thanks in advance for the help you can provide me :)

P.D: sorry for my english, isn't my mother tongue i use google translator

---

### Post by DuckHook on 2013-11-27
Hello nilsoncabrita,

Welcome to Ubuntu and the forums. I always admire people who post here when English is not their native language.

Your video card is rather old and not very powerful by today's standards, and this is probably the reason why the open-source driver was struggling to paint videos full screen. It is probably offloading a lot of the decoding to the CPU, which is also rather old.

1. What is the resolution of your monitor? Is it high, like 1920 x 1080?
2. How did you install the NVidia driver? Was it through the repositories or from their web site?
3. Does anything show on your screen? Even a flashing underscore character?
4. Do you get past the GRUB screen? When does the NVidia logo pop up?

Try <Ctrl>+<Alt>+<F1> to see if this gets you to a text console. If this works, then log in and do```
sudo cp /etc/default/grub /etc/default/grub.old
``````
sudo nano /etc/default/grub
```This will make a backup copy of the GRUB configuration file and call it "grub.old". The second command will open a text editor that will let us make changes to it. Find the line looking something like```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` and add "nomodeset" so that it looks as follows```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```We are dealing with system files, so *make sure* that you are spelling correctly. Remember, case is important in Linux. Then do:```
sudo update-grub
``````
sudo reboot
```Let us know how it goes.

---

### Post by nilsoncabrita on 2013-11-27
Thanks for the reply and welcome DuckHook i try to learn different languages[COLOR=#000000] :)
[/COLOR]
i know my video card is to old i don't pretend watch videos in hd but youtube videos in 360p looks great

> **DuckHook said:**
> 
1. What is the resolution of your monitor? Is it high, like 1920 x 1080?

1280X1024 is a LG Flatron L1730S
> **DuckHook said:**
> 
2. How did you install the NVidia driver? Was it through the repositories or from their web site?

Additional drivers 
> **DuckHook said:**
> 
3. Does anything show on your screen? Even a flashing underscore character?

Nothing.
> **DuckHook said:**
> 
4. Do you get past the GRUB screen? When does the NVidia logo pop up?

Yes the system get past the grub screen, after this the logo of nvidia appears and then goes black i try that you suggest and let you know :)

EDIT:
it work i writing this post from lubuntu and i can watch videos on youtube in 360p in fullscreen without problems thank you so much for the help[**[COLOR=#000000] DuckHook[/COLOR]**]("http://ubuntuforums.org/member.php?u=1256508") i'm really appreciate it :D

---

### Post by DuckHook on 2013-11-27
Good show. Please mark thread "solved" using thread tools. Happy Lubuntuing!

---

