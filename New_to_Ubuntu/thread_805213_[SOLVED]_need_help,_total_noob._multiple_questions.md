---
title: "[SOLVED] need help, total noob. multiple questions..."
date: 2008-05-23
forum: New to Ubuntu
---

### Post by no1cares on 2008-05-23
i just installed and downloaded latest updates for ubuntu 8.04 LTS on my computer.  This is my first time using it, so be understandable if these questions are simple, or stupid... 

1st question: i have a external hard drive that connects through a USB port, i plug it in and nothing happed.. how do i locate it on ubunutu??

2nd question: i have a bluetooth (logitech mx1000) mouse and when i click on the bluetooth icon in the upper right corner, the bluetooth preferences box opens and i see my mouse there, but have no clue how to get it to work.  when i right click on the bluetooth icon (in upper right) and go to browse devices i see my mouse there and when i click connect and hit the button on the mouse to make it visible i get an error (i copy and pasted what the error says at bottom).   i did a google search and found this [http://ubuntuforums.org/showthread.php?t=594624](http://ubuntuforums.org/showthread.php?t=594624) but have no clue what to do or what it means... i tried typing in the getting started into the terminal thing and it just says cannot find.

3rd question i want the 3d box thing that all the you tube videos have. i went to the appearance preferences, under visual affects and checked the extra box. it then downloaded some stuff for my vid. card and restarted.  i get wobble windows and stuff. but i want all the affects... i think there is an options menu to turn off and on different things but i dont know where that is located either...

any help would be awsome, 
thanks.

Error
Couldn't display "obex://[00:07:61:4B:C8:FC]/".
Error: Host down
Please select another viewer and try again.

---

### Post by HotShotDJ on 2008-05-23
> **no1cares said:**
> but i want all the affects... i think there is an options menu to turn off and on different things but i dont know where that is located either...Well, you really, REALLY don't want ALL the effects, or you'll bog down your system.. but there are some really cool effects that are not available by default... you need to install compizconfig-settings-manager using System --> Administration --> Synaptic Package Manager

---

### Post by saj0577 on 2008-05-23
3rd question is you make your workspace have 4 disks and then turn on rotating, click your mouse button in and your sorted. (all settings needed to be changed are in ccsm)

Sorry its not very detialed when I am on my machine later il add much better instructions but they might help you for now.

Saj

---

### Post by no1cares on 2008-05-23
thanks 
that has already helped, got some of the compiz affects to work. and playing around with some others... 

anyone know the answer to the question of how i can get my files off my external drive??

---

### Post by HotShotDJ on 2008-05-23
> **no1cares said:**
> anyone know the answer to the question of how i can get my files off my external drive??I'm not sure what the problem is with that, but let's see what we can find out.  Please connect the drive to your USB port.  Make sure the drive is plugged into the wall if necessary and that its power switch (if it has one) is switched on.  After a few moments, please open Applications --> Accessories --> Terminal and type in ```
fdisk -l
``` That last letter is a lower-case "L".  Please post the output of that command.

---

### Post by no1cares on 2008-05-23
i typed fdisk -l into terminal and it did nothing...

and
ok, well i get the rotate thing, but its not a cube, its only 2 sides... i turned on the desktop cube, cube rotation, and expo. in compiz settinggs.... how do i get the four sides??

---

### Post by HotShotDJ on 2008-05-23
> **no1cares said:**
> i typed fdisk -l into terminal and it did nothing.OOPS... My bad.  You need "sudo" (without quotes) in front of the command.  Sorry about that.
> **no1cares said:**
> ok, well i get the rotate thing, but its not a cube, its only 2 sidesSystem --> Preferences --> Advanced Desktop Effects Settings.  Open General Options.  Click on the Desktop Size tab.  Set Horizontal Virtual Size to 4.  Keep the other two sliders set to 1.  Close and enjoy your cube.

By the way, I'll have to pass you on to somebody else at this point.  Its a Friday night, and while I have extreme affection for newbies who need help, I am NOT sitting in my office on a Friday night. Heading out in just a few minutes.  Best of luck.

---

### Post by no1cares on 2008-05-23
no problem, thanks a lot HotShotDJ.   hopefully someone will post and help me with other problems... the cube one is solved...

---

### Post by Frak on 2008-05-23
What brand is your external Hard Drive.

---

### Post by m_ad on 2008-05-23
your external isn't in the Places menu?

---

### Post by no1cares on 2008-05-23
its a seagate, free agent..

---

### Post by mgmiller on 2008-05-23
First, you need to figure out where it is being seen in /dev
so run the command:
```
sudo fdisk -l
```

and look for the entry for the drive.  You may need to unplug and replug the USB cable for it to appear.

Once you know the device name use the pmount command to mount it.

If the fdisk command showed you the drive is /dev/sdg and you want to mount it as "backup"
enter the command:
```
pmount /dev/sdg1 backup
```

Look in /media and you will see a new folder called backup.  

To unmount the drive, use the command pumount with the name of the mount point.
For our example:
```
pumount backup
```
and the entry should disappear from /media

You can now make buttons for your panel to mount and unmount and save a bookmark in nautilus for the mounted location to semi automate the whole thing. 

To make the buttons on your panel, right click a blank area of the panel and select "Add to Panel" 

From the dialog window that opens select "Application Launcher".  You can now put in the commands that you used from terminal earlier.  Click on the icon button on the left side and pick a nice icon, the save it.

Do the same thing for the pumount command and you have 2 buttons side by side that mount and unmount the drive.

As an aside, I have only had this problem with external USB drives that I bought pre assembled.  I have also built 2 of them using an enclosure kit and old drives I had sitting around and they both work great without any tinkering.  Insanely simple to build, it almost takes longer to take them out of the box than it does to build them.  Turn them on and they appear and mount, click to unmount when done and turn them off.  Simple.

Hope this helps.


Oh yeah,  you should also install the simple compiz config manager.  It makes setting up compiz effects much easier.
```

sudo apt-get install simple-ccsm
```

This will add an extra choice in the System > Preferences > Appearance window on the visual effects tab, called "Custom".  You just click the Preferences button next to it and it makes setting up live corners for the mouse to trigger effects and a bunch of other stuff much easier.  The regular ccsm is pretty dense and complex.  It'll still be there for you to do extra tweaking if you need to.  In fact, I had the ccsm installed in Gutsy and when I upgraded to Hardy, none of the effects worked correctly until I uninstalled the ccsm and installed the simple-ccsm which also reinstalls the old ccsm (got all that?).

Anyway, welcom to Ubuntu and have fun...:lolflag:

---

### Post by no1cares on 2008-05-23
lol ok, thats ******** i unplugged it accidentally when i was trying to find the name on it, and when i plugged it back in, it found it... thanks m_ad

---

