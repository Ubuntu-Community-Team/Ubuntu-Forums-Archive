---
title: "Retrieving files from unclean NTFS using Ubuntu live USB."
date: 2014-10-18
forum: New to Ubuntu
---

### Post by nick153 on 2014-10-18
So my laptop updated the other day and on restarting, it started to just reboot go black screen then blue screen saying restart problem or something along those lines. autorepair doesnt work, no way to get into safe-mode because win8 sucks. So i decided to look up linux on another computer. downloaded it to thumbdrive and running live from it. now i am trying to get into windows files from there but still looked out getting this error code when trying to click on my harddrive icon:

Error mounting /dev/sda4 at /media/ubuntu/TI10649600G: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda4" "/media/ubuntu/TI10649600G"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.


my question is how do i unmount it if i cant boot into it?

tried creating new disk with something close to sudo mkdisk media/*user name*/sda4
may not have been exactly that but i found it online and now cant find it

seen also i could fix ntfs but i need to get somethings off that hardrive if at all possible. Me being stupid didnt backup anything either.

anyhelp of anykind would be appreciatied. even if you want to give me search topix because i think what i am looking for is to specific to search or i'm not searching the right way

thanks to anyone who will help and if this isnt in the right section mods please move it to where it needs to be

---

### Post by coffeecat on 2014-10-18
As this is an Ubuntu question &#8211; trying to retrieve files from an unclean NTFS filesystem using the Ubuntu live session &#8211; I&#8217;ve moved it from Windows support to New to Ubuntu.

I&#8217;ve also renamed your thread. &#8220;New To Linux Hate Win8&#8221; might make you feel better, but it won&#8217;t attract those who can help you!

Good luck.

---

### Post by Vladlenin5000 on 2014-10-18
Windows 8.x by default hibernates instead of shutting down (fast boot). AFAIK you can't mount a partition in that state.
Booting from Windows installation media and reinstalling should keep your personal data.

---

### Post by nick153 on 2014-10-18
> **coffeecat said:**
> As this is an Ubuntu question &#8211; trying to retrieve files from an unclean NTFS filesystem using the Ubuntu live session &#8211; I&#8217;ve moved it from Windows support to New to Ubuntu.

I&#8217;ve also renamed your thread. &#8220;New To Linux Hate Win8&#8221; might make you feel better, but it won&#8217;t attract those who can help you!

Good luck.

Thanks

---

### Post by nick153 on 2014-10-18
> **Vladlenin5000 said:**
> Windows 8.x by default hibernates instead of shutting down (fast boot). AFAIK you can't mount a partition in that state.
Booting from Windows installation media and reinstalling should keep your personal data.

So i'll get some disc from the manufacturer since I was stupid and thought windows 8 had to be better than before and didnt think to create a recovery drive. Lesson learned

---

### Post by nick153 on 2014-10-18
Now sorry for being a little green I have not had to mess with anything like this since I was in high school 10 years ago. Life happened and things change if I go to use this recovery media is there anything I need to not do or watchout for so I dont lose my data?

---

### Post by Mark Phelps on 2014-10-18
> is there anything I need to not do or watchout for so I dont lose my data? 

Yes ... Recovery Media from the PC manufacture is almost certainly going to erase and reformat your entire drive!

You're going to have serious problems getting at your data on the Windows drive because it sounds like you had failed to disable FastStartup -- which would have then turned off the new hibernation, and then allowed you to mount the partitions.

If you can connect the drive to a working Windows PC, you might be able to use Windows data recovery apps to retrieve files and folders from that drive.  A free app of that kind is known as Recuva.  You should try that out.

---

### Post by nick153 on 2014-10-18
> **Mark Phelps said:**
> Yes ... Recovery Media from the PC manufacture is almost certainly going to erase and reformat your entire drive!

You're going to have serious problems getting at your data on the Windows drive because it sounds like you had failed to disable FastStartup -- which would have then turned off the new hibernation, and then allowed you to mount the partitions.

If you can connect the drive to a working Windows PC, you might be able to use Windows data recovery apps to retrieve files and folders from that drive.  A free app of that kind is known as Recuva.  You should try that out.

Thanks. Sounds like I need to do some digging then. Can I take the hard drive out of that laptop then put it in my desktop as a slave? Or is there something else I should do?

---

### Post by Mark Phelps on 2014-10-19
> Can I take the hard drive out of that laptop then put it in my desktop as a slave? 

If your desktop is a Windows PC, then yes -- that's the thing to do.

Also, if Recuva doesn't find what you need, consider using RecoverMyFiles.  It's free to install and try out, to at least see if it finds the files and folders you want, but you have to go online and buy a license to do the actual data recovery.

---

### Post by nick153 on 2014-11-03
Finnaly got drive into old desktop. Had to buy another ide cable. Computer will not detect drive. Tried using ubuntu and its so slow on this old thing it wont fully load. Any ideas?[SIZE=4][SIZE=4][/SIZE][/SIZE]

---

### Post by coldcritter64 on 2014-11-03
> Tried using ubuntu and its so slow on this old thing it wont fully load.
If the "old desktop" is too far gone to handle Ubuntu, try any lighter linux distro live cd. Lubuntu live cd for example may work (generally requires far less resources than Ubuntu, so may possibly work on the older hardware). **If** your old hardware supports booting from a usb stick, loading the image to a usb stick and booting from there may also improve access speeds on the live system (cd drive access to a live system can be painfully slow, particularly on older hardware). 

Download links for an Lubuntu image are on [[COLOR=#0000ff]--this page--[/COLOR]]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu")
Good luck.

---

