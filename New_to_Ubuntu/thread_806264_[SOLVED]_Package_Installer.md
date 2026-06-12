---
title: "[SOLVED] Package Installer"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Miljet on 2008-05-24
I was trying to install a driver package for my Chicony webcam. Specifically sn9cxxx_2.13-gutsy-1ubuntu1_i386.deb

The package installer hung up and ran for several hours before I tried to stop it. It wouldn't close either window, no matter what I tried. I finally shut down the computer using the normal shutdown. The next day when I started the computer and attempted to install again, it gave me an error stating that I couldn't run more that one package managers at one time. I fixed that by running  sudo dpkg --configure -a  in the terminal.

Now if I double click on the package I get the message: Could not open 'sn9cxxx_2.13-gutsy-1ubuntu1_i386.deb'  The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.
I have downloaded the file at least four times and have changed the permissions to rwx for everyone. Makes no difference.

After checking other threads, I tried several other things. Here are the results of those attempts:

jack@jack-laptop:~$ sudo apt-get install util-linux
[sudo] password for jack:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package sn9cxxx needs to be reinstalled, but I can't find an archive for it.

jack@jack-laptop:~$ sudo apt-get dist-upgrade && sudo apt-get update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package sn9cxxx needs to be reinstalled, but I can't find an archive for it.

jack@jack-laptop:~$ sudo dpkg --configure -a
jack@jack-laptop:~$ 

I am running Gutsy 7.10 on a Toshiba P205 laptop

I have been fighting this problem for two days now and would really appreciate any help anyone could give.

---

### Post by HotShotDJ on 2008-05-24
> **Miljet said:**
> Now if I double click on the package I get the message: Could not open 'sn9cxxx_2.13-gutsy-1ubuntu1_i386.deb'  The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.Are you manually downloading this thng and then double-clicking on it to install or are you using System --> Administration --> Synaptic Package Manager to handle it for you? What is the source of this package?

You might try ```
sudo apt-get clean
``` and/or ```
sudo apt-get autoclean
``` and see if that gets things sorted for you.

---

### Post by Joeb454 on 2008-05-24
Did you check the permissions of the file? I know it sounds stupid.

Right click it and choose "Properties" Then click the permission tab.

Somewhere near the bottom will be a check box allowing you to execute the file as a program :)

---

### Post by HotShotDJ on 2008-05-24
> **Joeb454 said:**
> Somewhere near the bottom will be a check box allowing you to execute the file as a program :)ACK!  NO!  Don't do that with a .deb file.  Deb files are NOT executable.

---

### Post by Miljet on 2008-05-24
Yes, I downloaded the file to my desktop and double-clicked to install it. I couldn't find anything remotely similiar in Synaptic.

I tried the sudo apt-get clean and also sudo apt-get autoclean. I got no error messages but it didn't fix anything either.

I have already checked the permissions of the file and changed them to every configuration imaginable (including excutable.)

Oops, forgot to provide source: [http://www.linux-projects.org/modules/mydownloads/viewcat.php?op=&cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?op=&cid=7)

---

### Post by HotShotDJ on 2008-05-24
> **Miljet said:**
> Oops, forgot to provide source: [http://www.linux-projects.org/modules/mydownloads/viewcat.php?op=&cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?op=&cid=7)It is unlikely that this forum can help you.  This is a binary-only driver that is not supported by Ubuntu.  In fact, you are trying to install a "Time Limited" trial version.  I don't know how well it will work, if at all.  You need to pay for the full driver (see: [http://www.linux-projects.org/downloads/sn9cxxx-unlimited.html](http://www.linux-projects.org/downloads/sn9cxxx-unlimited.html) ).  You may need to file a bug with the creators of this package.

---

### Post by Miljet on 2008-05-24
Thanks HotShotD, I guess that explains why it won't install. I found the link following threads about getting webcam working. I need to start looking for other drivers.

Any ideas as how to undo whatever damage has been done? In other words, how do I get rid of the error messages "E: The package sn9cxxx needs to be reinstalled, but I can't find an archive for it."?

---

### Post by HotShotDJ on 2008-05-24
> **Miljet said:**
> Any ideas as how to undo whatever damage has been done? In other words, how do I get rid of the error messages "E: The package sn9cxxx needs to be reinstalled, but I can't find an archive for it."?Try removing it:```
sudo apt-get remove sn9cxxx
```Let me know if the error persists after doing this.

---

### Post by Miljet on 2008-05-24
That didn't get rid of it either. I ran locate and found a file called sn9cxxx.0.crash located in /var/crash. I deleted that file and it didn't make any difference either. Results:

jack@jack-laptop:~$ sudo apt-get remove sn9cxxx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package sn9cxxx needs to be reinstalled, but I can't find an archive for it.

---

### Post by HotShotDJ on 2008-05-24
> **Miljet said:**
> That didn't get rid of it either.Well, then... we'll just have to get ugly with that misbehaving package. :)```
sudo dpkg --remove --force-remove-reinstreq sn9cxxx
```

---

### Post by Miljet on 2008-05-24
Well, that changed the error message at least, but still getting a reference to the sn9cxxx package.

BTW, I really appreciate your taking the time for this.

---

### Post by HotShotDJ on 2008-05-24
> **Miljet said:**
> Well, that changed the error message at least, but still getting a reference to the sn9cxxx packageI need to know what the new error message is.

---

### Post by Miljet on 2008-05-24
I'm sorry, had another senior moment and forgot to include output from the terminal.

jack@jack-laptop:~$ sudo dpkg --remove --force-remove-reinstreq sn9cxxx
[sudo] password for jack:
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `sn9cxxx' missing, assuming package has no files currently installed.
94969 files and directories currently installed.)
Removing sn9cxxx ...
jack@jack-laptop:~$ sudo apt-get remove sn9cxxx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sn9cxxx is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jack@jack-laptop:~$

---

### Post by Miljet on 2008-05-24
I think that may have fixed the problem. I can run apt-get now without getting any reference to that package.

I am going to give it a rest for tonight. Thanks again for all the help.

---

