---
title: "iPod classic no longer mounting"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by hellolife on 2011-11-10
I have had a hell of a time trying to figure this out. It's basically been a month long process.
I just did a complete restore to factory settings of my iPod on a windows computer (so it is FAT32). I plugged it into my computer which is running Ubuntu 10.04. It showed up and opened in Rhythmbox. I tried transferring songs onto it and went to sleep while it was processing. I woke up and the songs had an issue transferring. No big deal. I used another computer to add all of the songs from an external hard drive into Rhythmbox so I could then transfer the songs to the iPod. After all of the songs were transfered into Rhythmbox and I was about to transfer them to the iPod, I realised... there was no iPod. It had been mounted before, showing up on the desktop and in Rhythmbox. It was as if it just disappeared (even though it was still plugged into the computer). 

WTF is going on with this stupid iPod? My fiance has an 30gb video iPod and it works perfectly. Why in the world would mine not work? It's an 80gb classic. It's newer than hers. I have had so many problems trying to figure this out. I have gone through countless ubuntu forums, ipod tutorials, things to do/undo in synaptic. I've downloaded multiple things from ubuntu software center and NOTHING IS WORKING.

Please help. I am going insane.

---

### Post by dolphin194 on 2011-11-10
Try following the procedure found at [http://blog.christinaoutlay.com/2008/05/28/ipod-wont-mount-in-ubuntu-did-you-try-to-set-a-mount-point-and-instead-screwed-up-something-try-this-fix.aspx](http://blog.christinaoutlay.com/2008/05/28/ipod-wont-mount-in-ubuntu-did-you-try-to-set-a-mount-point-and-instead-screwed-up-something-try-this-fix.aspx)

> 1. Install gconf-editor by opening the terminal and typing "sudo apt-get install gconf-editor"
2. if you find that you already have gconf-editor, then at the terminal prompt, simply type "gconf-editor"
3. The configuration manager will open.
4.  On the left, double-click on the "system" directory, then storage, then  volumes, then single-click on _org_freedesktop_Hal_devices.... (it's a  really long folder name, you get the point)
5. You should see your ipod's mount point on the right side of the Window.
6.  Right-click on your ipod entry, choose Edit Key from the pop-up menu,  and change the value. Do not put the directory or anything else; just  the name - most people just name it Ipod.
7. Now, close configuration editor and you should be all set!  The ipod should display on your desktop

---

