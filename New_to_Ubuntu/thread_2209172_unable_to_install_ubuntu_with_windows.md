---
title: "unable to install ubuntu with windows"
date: 2014-03-04
forum: New to Ubuntu
---

### Post by ojs2 on 2014-03-04
hello guys,
I am using sony vaio svs13a15gg and i am not able to install ubuntu in it with windows.
though i create partition but it does not detect my linux partition. help me!!

---

### Post by david98 on 2014-03-04
Did you manually create the partition in which you want to install buntu to and also what did you format it to ? It would of been easier to use the ubuntu installer and then clicked on the option to install alongside windows. Could you boot buntu into a live session and open a terminal by pressing ctrl+alt+t then paste the outcome of this command [COLOR=#000000][FONT=Ubuntu Mono]sudo fdisk -l


Ps the more information you can provide the better what version of buntu hdd size partition size etc[/FONT][/COLOR]

---

### Post by ajgreeny on 2014-03-04
You should always shrink the windows partition using windows own Disk Management tool, and make sure you only move the right hand end of the windows partition to the left, leaving unallocated space, or you could be in trouble.

The ubuntu installer should now find the free unallocated space you made earlier and install to that.  It is much easier to see exactly what is going on if you use the "Something Else" option in the installation process.

---

### Post by AlwaysRemind on 2014-03-04
Not sure if you figured this out yet but I just spent all of yesterday hutning around for this answer to. I finally got it working and have a link to the tutorial that helped me (assuming you have a UEFI problem). Also, Ubuntu didn't recognize Windows 8 for me (it mentions it in the tutorial in fact) and it was not a problem. I shrunk my C:\ drive in Windows and gave myself about 200 gig of free space before starting. I didn't format it, I wanted to let Ubuntu do that for me and it worked great.

Here's the thread:
[http://ubuntuforums.org/showthread.php?t=2209117](http://ubuntuforums.org/showthread.php?t=2209117)

---

