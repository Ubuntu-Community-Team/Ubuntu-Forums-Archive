---
title: "An error occured while mounting /boot/efi"
date: 2015-01-14
forum: New to Ubuntu
---

### Post by christopherbrown03 on 2015-01-14
I have been using ubuntu for about 2 years now.  The computer I am having issues with right now is about a year old lenova ideapad with ubuntu 14.04.1 installed as the sole operating system.  I have had 12.10 and 14.10 installed on this computer with 0 issues.  I installed an update last night and chose to have the computer restart later, I was working on a paper at the time.  When I finished I shut the computer down and walked away.  When I started it up this morning I got an error about not being able to mount my hard drive.  I shut the computer down and tried again, this time it made it to my login screen.   When I tried to login, hoever, I just landed on the default wallpaper with no unity interface to speak of.  The mouse cursor still worked, but right clicking did nothing.  I assumed it had something to do with the update, so I booted to a usb with a live version of 14,04.1 on it (I am in the live version right now).  I ran boot repair and restarted into my OS, this time it went through the normal ubuntu startup but then I recieved the error in the title.  I was given the option to skip or mount it manually, which I have no idea how to do, or if it would even work, so I went with skip to see what would happen.  It booted fine and let me log in normally this time.  However, the wireless no longer works, there isnt even an option for it in my networking screen.  I can restart and choose to skip the efi mount continuously now, so I have to assume that the issues are related (my wifi works fine in the live usb).  I did run ```
grep efi /etc/fstab
sudo blkid | grep fat
```

The UUID values were the same for both commands.  Trying to solve the problem with google, I ran into a post suggesting running ```
sudo dosfsck /dev/*my drive name*
```

I am not in the habit of running commands that I dont understand anymore (lesson learned on last computer).  Is this a safe and viable option for me to try?  If not, what else can I try?  Thanks to anyone who can help!

UPDATE:

I seem to have fixed the issue by entering the grub menu and selecting the last working version I had installed, being Ubuntu, with Linux 3.13.0-43-generic.  Computer booted up, mounted everything fine and wifi works as before.  I think the problem must be the update I installed (3.13.0-44-generic).  There may be something wrong with the update.  Not sure what to do from here, wait for the next one and hope for better results I guess.  Will mark as solved in a few hours if noone has anything.

---

### Post by grahammechanical on 2015-01-14
If you want to do a check of the file systems then there are couple of ways to do it.

At the Grub boot menu select Advanced Options and then select Recovery mode and at the Recovery menu select fsck - check all file systems.

The other way is with the Live session. At the first purple screen press Enter, then select the language (English default) and you will be at a text screen with option to Try Ubuntu, Install Ubuntu but also to Check disc for defects.

By the way, if the OS loads to the login screen or if set to automatic login, to the desktop wallpaper even without the launcher or the top panel, then the problem cannot be a boot problem. Can it? Boot Repair cannot fix OS loading problems only issues with the Grub boot menu.

When you get that message about the mounting of /boot/efi, what happens if you wait? All relevant Ubuntu partitions have to be mounted as part of the OS loading process. Sometimes, there is a delay in mounting a partition, and the situation resolves itself in a few seconds.

At that desktop with only the wallpaper try right clicking the desktop. If you get a menu, then select Change Desktop Background. That will get you to System Settings>Appearance but from there you can get to System Settings>Software and Updates>Additional Drivers tab. Try another video driver.

If that does not work and you can get to a terminal - Ctrl+Alt+T run

```
dconf reset -f /org/compiz
```

or 

```
setsid unity
```

The first command will reset Compiz the window compositor. The second command will restart Unity. If you cannot get to a terminal you might be able to get to a Linux console - Ctrl+Alt+F2. Run the commands from there and to get back to the desktop - Ctrl +Alt+F7.

Regards.

---

