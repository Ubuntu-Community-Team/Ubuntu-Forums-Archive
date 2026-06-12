---
title: "[SOLVED] Wrong user when logging in?"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by Nevyn on 2008-08-07
The past couple of weeks I've had some issues with Ubuntu (8.04, 32 bit).
It started first when FF3 lost all bookmarks and settings for adblocker. Googled it and found other users having the same issue. temporarily resolved it by uninstalling and reinstalling FF. All worked fine for a week. 
Then the problem re-appeared. No biggie, I thought, an update wil come soon and in the meantime I can run [sudo firefox] in terminal and all is good. 

Then my desktop menues (I'm using standard theme) lost the extra shortcuts I've placed in the Places-menu. I can't delete files because I'm denied permission. My downloads that used to end up in /home/nev/downloads ended up in /home/nev instead, when starting FF I can't even use the forward- and back arrows (except when using sudo firefox) and all my adblock filters are lost. When I'm creating a document by right-clicking on the desktop it says I have no templates installed, where I used to be able to create for instance OpenOffice-docs directly that way. 
I don't get notified about Ubuntu updates anymore, but I have to run sudo apt-get update/upgrade. 

Also, when playing songs in Rythmbox, it plays a few songs (like 10-15) then it just kills itself and I have to start it again. Don't know if it's related to the other stuff.

I don't have a clue how to troubleshoot, it seems to me it got something to do with user management, but I only have one user configured (except the root-account of course). 
I'd really appreciate a pointer in the right direction.

---

### Post by Pro-reason on 2008-08-07
Those are several different issues.

For your Firefox settings, make a backup of your profile every now and again, so that you can restore your settings if something happens.  One way to do this is with the following command:

```
tar   -zvcf   ~/Desktop/Firefox_backup_`date +%F`.tgz   ~/.mozilla/firefox/
```

Running *sudo firefox* is a very bad idea.  Your settings could be mixed up due to running the app partly as a user and partly as root.  If your Firefox profile is corrupted for some strange reason, simply delete it and use a fresh one.  Extract your bookmarks etc from it first, or from your last backup.

---

### Post by Elfy on 2008-08-07
Run rhythmbox from a terminal and then see what error it gives when it crashes, you might have got yourself all caught up with

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> There are other times, though, when side effects can be as mild as Firefox extensions not sticking or as extreme as as not being able to log in any more because the permissions on your .ICEauthority changed. You can read a full discussion on the issue here.

---

### Post by mcduck on 2008-08-07
Sounds like possible permission problems with different setting files, possibly resulting from running apps with sudo..

Every time you start a program with sudo or gksudo, you start it as root, not as your own user. And if you use sudo (instead of gksudo) for graphical apps the programs are started as root, but root's environment isn't loaded correctly (as sudo is only for command line, gksudo would load root's environment for GUI apps) so youa re running the program as root user, but using your own users setting files..

_Never_ sun a GUI app with sudo. If you really need to run something with root permissions, use gksudo. But you never need to run apps like web browsers as root. They don't do the kind of tasks that would require full permissions to do whaever they want in your system.

Anyway, you could start by running "ls -la ~/" and checking that everything there is owned by your own user, and then doing the same for all the hidden directories inside your home.

---

### Post by Nevyn on 2008-08-07
Thanks for the quick responses.

Pro-reason: I'll be sure to start making backups as soon as FF functions as it should. Using sudo firefox has been the only way for me to use FF these past few weeks, since tha back- and forward arrows don't work otherwise. Guess I'll be using Seamonkey until I've solved it =)

forestpixie: thanks for the link, I'll read it thoroughly tonight. 

In the meantime, I'll post the error code I get when I try to update (either via Update manager or via sudo apt-get upgrade):
```
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-ubuntu-modules-2.6.24-19-rt (2.6.24-19.28) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-rt

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-rt
dpkg: error processing linux-ubuntu-modules-2.6.24-19-rt (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-rt:
 linux-image-rt depends on linux-ubuntu-modules-2.6.24-19-rt; however:
  Package linux-ubuntu-modules-2.6.24-19-rt is not configured yet.
dpkg: error processing linux-image-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-rt:
 linux-rt depends on linux-image-rt (= 2.6.24.19.21); however:
  Package linux-image-rt is not configured yet.
dpkg: error processing linux-rt (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-19-rt
 linux-image-rt
 linux-rt
E: Sub-process /usr/bin/dpkg returned an error code (1)
nev@nev-computer:~$ 
```
linux-rt, is that a part of the kernel? Not much helpful info in Synaptic anyway. The message that says "no  space left on device" (in the beginning of the message) is peculiar, since every partition except swap has at least 12 GB free.

Error codes in the Firefox Error Console
```
Error: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: file:///usr/lib/firefox-3.0.1/components/nsBrowserGlue.js :: bg__initPlaces :: line 386"  data: no]
Source File: file:///usr/lib/firefox-3.0.1/components/nsBrowserGlue.js
Line: 386
```
```
Error: uncaught exception: [Exception... "Component returned failure code: 0x8007000e (NS_ERROR_OUT_OF_MEMORY) [nsIDocShellHistory.useGlobalHistory]"  nsresult: "0x8007000e (NS_ERROR_OUT_OF_MEMORY)"  location: "JS frame :: chrome://browser/content/browser.js :: prepareForStartup :: line 763"  data: no]
```

There is a bug report on this error code at [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg880329.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg880329.html) but it's still active and it's been there a while. I'm only using Ext3 and not NFS. I have not been able to find out how to create a new user in only firefox. I'll try to create a new Ubuntu-user and see how apps behave for that user.

Btw, my /home folder is on a separate partition.

---

### Post by Elfy on 2008-08-07
CAn you open a terminal and run 

```
df -h
```then we can see what the sizes of partitions are - usually > gzip: stdout: No space left on devicewould suggets that the /boot is full

---

### Post by Nevyn on 2008-08-07
mcduck: I'll start checking this. So far I've seen a few that belong to root and about 90% belong to me. Haven't done it on every folder yet though.

forestpixie: I suppose here is where the problem lies:
/dev/sdb1              92M   89M     0 100% /boot
/dev/sdb3             210G  200G     0 100% /home

But 92 MB for /boot, looks really strange
Edit: Is it possible and recommended to change size of boot-partition with gparted?

---

### Post by bpowell2005 on 2008-08-07
Nevyn,

Yes, I think your disk-full error is the problem. I had the same strange stuff start happening to me on a virtual Ubuntu installation...it filled up quick (I only allocated 5 gig) and woah-boy did it start throwing some funny errors once it was full...lost my bookmarks, couldn't even start some programs, other programs would just shut-down...lost my "Applications" menu, etc...it was crazy. Just resizing the partition fixed me right up though.

---

### Post by Elfy on 2008-08-07
If you can actually do so I would uninstall some old kernels - but it might complain, try doing it in a root terminal in the recovery.

apt-get remove --purge linux-image-2.6.24-16-generic

for example - check which kernels you actually have installed, look on the menu.lst - it's likely that removing one will be sufficient to allow the new one to install.

But ther would nothing to stop you increasing the size of the partition with gparted  - but do it with the livecd if you can't boot.

---

### Post by Nevyn on 2008-08-07
Thanks again forestpixie.
I first tried to resize the boot-partition but realized that I probably would have to unallocate the space that comes directly after the boot-partition on the disk; space that is used by my /-partition. Don't want to do that ;)

Which kernels are safe to remove (doublechecking since I don't feel to comfortable with it)?
In /boot/grub/menu.lst there were kernels
2.6.24-17-generic (and recovery)
2.6.24-18-generic (and recovery)
2.6.24-19-generic (and recovery)
2.6.24-19-rt (and recovery)

I purged and autoremoved 16-generic and it freed a few megs, and that seemed to make things a little less buggy (for instance I can see all the shortcuts in the menus again).

And thanks bpowell2005!

---

### Post by Elfy on 2008-08-07
I always like to keep current and previous - then if there's a problem with one can boot the older one.

So at the moment if I was you I would lose -17

At the moment - I have -20, -19 and -18 - I'm keeping 3 as afaik -20 is still in propsed and it's 55Mb in total.

---

### Post by Nevyn on 2008-08-07
Thanks again, forestpixie. I now only have kernel 18 and 19, making the /boot only use 68MB.

However, a new major issue has occured. 
When I was about to use gparted to resize partitions on a second harddrive to be able to free up more space in /home, the whole system froze over. Not even ctrl+alt+backspace worked. 
After hard reboot, it says it cannot detect my primary master hard drive. a second reboot results in a blank screen right after the boot procedures (when GRUB is about to kick in).
I don't think it had anything to do with what I was doing in gparted since I hadn't clicked the "apply" button yet, therefore no operations should have been done to my partition table.

I am currently on a live CD and have no clue where to begin troubleshooting.

Edit: Solved it by disconnecting one of my three hard drives. Strange error. However, most of the errors I described in the first post are solved, including the firefox-error, by freeing space on /boot and /home-partitions.
Thanks for great and quick help!

---

