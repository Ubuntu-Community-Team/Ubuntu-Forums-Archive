---
title: "Mini-Distro Required - Help sought"
date: 2007-02-23
forum: Programming Talk
---

### Post by AlanRogers on 2007-02-23
This is a shot-in-the-dark request for assistance - I know what I'm looking for and that somebody here could easily deliver it but I haven't the foggiest clue where to start. Here goes:

What I'd like to have is a Live CD which will boot and automatically do the following:[LIST=1]
[*]Detect and mount all physical hard drives in the computer
[*]Mount a network share after prompting for a (UNC) path, username and password - error checking critical
[*]backup/image each hard drive according to a naming convention which should include the computer name, hard drive identifier, file system and datestamp
[*]Verify the integrity of the backup
[*]Reboot and spit the CD out[/LIST]Any thoughts or takers ? :idea:
Mods: If I've posted to the wrong thread, please feel free to move it.

---

### Post by justin whitaker on 2007-02-23
Try Finnix:

[http://www.finnix.org/](http://www.finnix.org/)

---

### Post by SuperMike on 2007-02-23
> **AlanRogers said:**
> This is a shot-in-the-dark request for assistance - I know what I'm looking for and that somebody here could easily deliver it but I haven't the foggiest clue where to start. Here goes:

What I'd like to have is a Live CD which will boot and automatically do the following:[LIST=1]
[*]Detect and mount all physical hard drives in the computer
[*]Mount a network share after prompting for a (UNC) path, username and password - error checking critical
[*]backup/image each hard drive according to a naming convention which should include the computer name, hard drive identifier, file system and datestamp
[*]Verify the integrity of the backup
[*]Reboot and spit the CD out[/LIST]Any thoughts or takers ? :idea:
Mods: If I've posted to the wrong thread, please feel free to move it.

Install Ubuntu Server as a LiveCD -- there's got to be several docs on this somewhere, I would think. Then, have a bash command or script in that build so that you could run these things you want.

* Detect and mount all physical hard drives in the computer. I take it that this would be a Windows PC you'd use it on? If so, then you could probably run a command to find those drives and then use a mount -t ntfs or mount -t fat32 to mount those devices. Or, you could just guess and mount several and ignore the errors that come back.

* Mount a network share. A bash script could mount -t smbfs a network share. Do you know how to do this?

* backup - you could use 'cp' command and pass it the right parameters.

* verify integrity -- I think that's a switch on cp.

* reboot and spit cd out -- run 'eject' and a 'read' prompt 'hit enter to reboot', then do 'shutdown -r now' to reboot.

---

### Post by SuperMike on 2007-02-23
Here's another approach. If you're a LAN Administrator, and if you know for certain the local admin passwords on each Windows PC, and if you have a consistent PC naming convention, then you could write a Bash script on Ubuntu workstation to do all this from a centralized point without having to run around with a CD. It would use mount -t smbfs and try to attach to C$, D$, E$, F$, etc. on a PC remotely, generating an error report back to you for those it failed to reach. At that point you could just rerun your script again on a following day for the ones it missed. After that, you could take that error report and hit those PCs manually.

BTW, PC hibernation/power saving is the enemy of LAN Manager remote admin. Turn that off with a group policy rollout.

---

### Post by AlanRogers on 2007-02-23
> **SuperMike said:**
> * I take it that this would be a Windows PC you'd use it on?Correct, but multiple computers - it's intended as a tool that any user can use by following a crib sheet, not just admins with Linux experience.
> **SuperMike said:**
> * Do you know how to do this?No, sorry. I have less than a year's experience on Linux and still have much M$ to unlearn! :oops:
> **SuperMike said:**
>  * backup - you could use 'cp' command and pass it the right parameters.My bad, I should have made clear that I'm ideally looking to take an image of the mounted drives/partitions
> **SuperMike said:**
>  * verify integrity - I think that's a switch on cp.See above, but I'm guessing this answer is still relevent.
> **SuperMike said:**
>  * reboot and spit cd out - run 'eject' and a 'read' prompt 'hit enter to reboot', then do 'shutdown -r now' to reboot.This much I could do!:-D

---

