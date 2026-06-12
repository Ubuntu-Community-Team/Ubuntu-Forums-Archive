---
title: "Ubuntu 11.04 natty - Cannot login after running Live CD"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by painguin on 2011-09-26
Hi guys, 

This is my first official post in the forums here.  I have long been a "reader" of the questions and answers here and have found them to be more than helpful.  With that said, I have a problem which I cannot seem to find an answer to.  

I have an Ubuntu 11.04 (x64) installation on my system.  I is a wubi install and just the other day I ran a script I found on the forums here to expand the virtual disk to 32gigs.  It worked well!!!

However, last night, I popped in the LiveCD to use Gparted to examine my partitions as I planned to go ahead and try to migrate my wubi install to a larger partition (with swap) in the coming days. 

I know where I screwed up, after inserting the disc I moved forward with the installation process (non-wubi) and I believe this has ruined my wubilldr and wubildr.mbr files.  The reason I believe this is because I restored my root.disk last night using a shadow copy throgh windows.  This should have taken my virtual drive back to the status it was before my problem arose.  However, I found out that it did not.

This is what I get (and I searched the forums for a solution beforehand but was unable to find a viable solution for myself).

Upon choosing which kernel to boot into via GRUB, the login prompt comes up as usual.  However now I notice this error in the top right corner of the screen stating something to the nature of "The Gnome Power Manager has not been configured correctly.  Please contact your systems administrator."

On top of that, when I try to login, it acts like it is going to log me in but just loops back to the logon prompt.  I tried choosing the recovery option in GRUB and reinstalled the power manager but nothing changed.  I updated GRUB, I checked for broken dependencies, etc. 

I can still access all of my files from the shell prompt but my desktop environment is gone.  I also tried "sudo apt-get install ubuntu-desktop".  The readout was "You already have the latest desktop installed."

So, I found a thread on here last night for backing up all of my programs and data from Ubuntu so that I could recover them in a fresh install.  However, as I was running the backup (basically compressing everything into a tarball) I noticed that it was copying the files in the /host directory.  Most notably /host/program files/, I don not want to copy these files as they are obviously only used in my Windows 7 installation. 

So, in order...

1.)  Can I "rescue" my wubi installation and login again?
2.)  When backing up my data I used this comand in my root directory.  How can I use this to backup my system in say, my C:\?  
3.)  how can I stop this from backing up program files and all of that stuff non-Linux related?  Should I change that last switch from "/" to "/host/UbuntuBackup/?  And should I add "--exclude=/host" so that it does not copy the contents of my C:\"? 
4.) And finally, how do I type underneath the line of code that I just pasted?  LOL!  :D  
FYI - I took this line from  [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+system](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+system)

Thanks in advance!!!

PAinguIN
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/dev --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

---

### Post by painguin on 2011-09-26
> **painguin said:**
> Hi guys, 

This is my first official post in the forums here.  I have long been a "reader" of the questions and answers here and have found them to be more than helpful.  With that said, I have a problem which I cannot seem to find an answer to.  

I have an Ubuntu 11.04 (x64) installation on my system.  I is a wubi install and just the other day I ran a script I found on the forums here to expand the virtual disk to 32gigs.  It worked well!!!

However, last night, I popped in the LiveCD to use Gparted to examine my partitions as I planned to go ahead and try to migrate my wubi install to a larger partition (with swap) in the coming days. 

I know where I screwed up, after inserting the disc I moved forward with the installation process (non-wubi) and I believe this has ruined my wubilldr and wubildr.mbr files.  The reason I believe this is because I restored my root.disk last night using a shadow copy throgh windows.  This should have taken my virtual drive back to the status it was before my problem arose.  However, I found out that it did not.

This is what I get (and I searched the forums for a solution beforehand but was unable to find a viable solution for myself).

Upon choosing which kernel to boot into via GRUB, the login prompt comes up as usual.  However now I notice this error in the top right corner of the screen stating something to the nature of "The Gnome Power Manager has not been configured correctly.  Please contact your systems administrator."

On top of that, when I try to login, it acts like it is going to log me in but just loops back to the logon prompt.  I tried choosing the recovery option in GRUB and reinstalled the power manager but nothing changed.  I updated GRUB, I checked for broken dependencies, etc. 

I can still access all of my files from the shell prompt but my desktop environment is gone.  I also tried "sudo apt-get install ubuntu-desktop".  The readout was "You already have the latest desktop installed."

So, I found a thread on here last night for backing up all of my programs and data from Ubuntu so that I could recover them in a fresh install.  However, as I was running the backup (basically compressing everything into a tarball) I noticed that it was copying the files in the /host directory.  Most notably /host/program files/, I don not want to copy these files as they are obviously only used in my Windows 7 installation. 

So, in order...

1.)  Can I "rescue" my wubi installation and login again?
2.)  When backing up my data I used this comand in my root directory.  How can I use this to backup my system in say, my C:\?  
3.)  how can I stop this from backing up program files and all of that stuff non-Linux related?  Should I change that last switch from "/" to "/host/UbuntuBackup/?  And should I add "--exclude=/host" so that it does not copy the contents of my C:\"? 
4.) And finally, how do I type underneath the line of code that I just pasted?  LOL!  :D  
FYI - I took this line from  [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+system](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+system)

Thanks in advance!!!

PAinguIN
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/dev --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /


So, I'm still at a loss here.  Does anyone have any idea as to what I can do?  I have installed pyrit on my Ubuntu setup.  The databases I have created are HUGE and if I have to get rid of this installation and start over I'm looking at literally one week of work to get it all back.  Please, someone help!

I don't need a "fix all" solution, I just need to backup everything so that I can restore it in a new Ubuntu install...  You guys are the best, that's why I'm asking you.  All suggestions are welcome.

Thanks!

PAinguIN

---

