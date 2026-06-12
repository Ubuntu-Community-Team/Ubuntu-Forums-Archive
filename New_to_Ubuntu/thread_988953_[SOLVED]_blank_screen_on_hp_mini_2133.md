---
title: "[SOLVED] blank screen on hp mini 2133"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by elliah on 2008-11-21
i just installed xubuntu 8.04.1 on a hp mini 2133 using the alternate cd on a usb stick.  the installation worked fine however when i try to boot the computer, where the log-in screen is supposed to show i get a black blank screen.  
another thing i noticed is that as the blue status bar fills up as xubuntu is loading is near full, the blue becomes a series of white horizontal lines, like the screen is messed up.
a few forum posts i found mentioned a bug with the via chrome driver but i can't even get to the desktop so how do i fix this?

---

### Post by cozmicharlie on 2008-11-21
Can you boot to a shell?  At boot up, grub should give you an option to start in safe mode.  That should take you to a shell prompt to log in.  It sounds like a device driver problem and you may need to go to your xorg.conf and manually configure it.  I am not sure what driver the 2133 uses but a search of the forums or the hp forums might tell you.  What you want to do at the prompt is edit your xorg.conf.  It should be at /etc/X11 so type in the following command.
```
sudo nano /etc/X11/xorg.conf
```
Then you want to edit under section Device.  When I had this problem with one of my computers I just added vesa and it worked fine.  So under device you add:
Driver    vesa 
Close and save and see if that works.  However, before you do this check the forums and see if another driver is preferred.  

Hope this helps

---

### Post by elliah on 2008-11-21
i found this thread that mentions installing the via chrome 9 driver...and i downloaded the tar.gz but i don't know how to install it via the console...

---

### Post by cozmicharlie on 2008-11-21
Normally below is how to do this but since you can't get into your computer try it with vesa first.  Then if that works and you can get a desktop you can do the following but most likely it will give you an option to add the hardware and you won't need to do this.

Is this a linux driver or a Windows driver?  If it is a Linux driver then extract the file (right click - extract here). Their should be a text file Readme or Install.  Open it in an editor and hopefully it will have intructions.  Typically the procedure for installing a source file is the following.

Extract the file
Open a terminal
change the directory to the extracted file.  If you extracted to your desktop this is the command.  For yourname this would be whatever name your you use for your home folder.  File name is the entire name of the extracted directory.
```
cd /home/yourname/desktop/file name
```
So for example, if the file name is viachrome.tar, I would write the following at the prompt:
$cd /home/cozmicharlie/desktop/viachrome.tar
(or, write cd at the prompt and drag the file to the terminal it will show the path).
Once at the directory for the file type the following in the terminal at the prompt one line at a time.

```
./configure
make
sudo make install
```

If this is a windows driver then you need to install it through ndswrapper.  Search the forums, thier are lots of good tutorials on how to do this.  It is fairly simple but if you get stuck post back.

---

### Post by cozmicharlie on 2008-11-21
I did some searching in the forums.  What I told you to do will not work.  The vesa drivers don't work.  Read through this thread - it will help you.
[http://ubuntuforums.org/showthread.php?t=967198&highlight=hp+2133&page=3](http://ubuntuforums.org/showthread.php?t=967198&highlight=hp+2133&page=3)

---

### Post by elliah on 2008-11-21
i actually got it to work after replacing my xorg.conf with the one i downloaded off that thread u mentioned...thanks...

---

### Post by cozmicharlie on 2008-11-21
Glad to here it.  You may want to give the details of how you did it.  Also, if you believe your problem is solved, please mark the thread as solve.

Great to here it worked for you.

By the way, how do you like the HP 2133?

---

### Post by luvit on 2008-11-25
i had that exact same problem.  the solution you're looking for is detailed in [[COLOR="Blue"]_**this thread**_[/COLOR]]("http://www.hp2133guide.com/forums/viewtopic.php?p=7176#7176")
.

---

