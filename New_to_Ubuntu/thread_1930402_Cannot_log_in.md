---
title: "Cannot log in"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by acai2 on 2012-02-23
Hello!

I've run into a bit of a problem with my Ubuntu system recently. I was installing MATLAB on my Ubuntu partition (I dual boot Windows XP/Ubuntu on an old laptop) and upon rebooting I was not able to log in to my Ubuntu system. The login screen appears and I can enter my password, but upon doing so the screen flashes black, takes a few seconds, and reloads the initial login page. No change. There is also an error message in the upper right corner with the text: "Install problem! The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator." 

After googling around for a bit, it seems this may be the result of root being full. I'm not entirely sure what that means, but I followed the steps [here]("http://www.geekdevs.com/2010/04/solved-unable-to-boot-due-to-gnome-power-manager-error/") to try and solve the issue. None of the fixes on the site worked. As many posts with this issue ask, I'll post the results of df -h:

Filesystem Size Used Avail Use% Mounted on
/dev/sda3 11G 9.6G 0 100% /
none 493M 284k 493M 1% /dev
none 497M 0 497M 0% /dev/shm 
none 497M 192k 497M 1% /var/run
none 497M 0 497M 0% /var/lock
none 497M 0 497M 0% /lib/init/rw
/dev/sda2 140G 14G 119G 11% /home

Oh, and as you can guess, I'm able to access the terminal with ctrl+alt+F1.

Any ideas?

---

### Post by sffvba[e0rt on 2012-02-23
> After googling around for a bit, it seems this may be the result of root being full. I'm not entirely sure what that means...

Hi and welcome to the forum.

If you look at the output you posted; 
> Filesystem Size Used Avail Use% Mounted on
/dev/sda3 11G 9.6G 0 100% / 
... it shows your root partition ( / ) at 100%.  It seems you have allocated 9.6GB to it and it is full now.

The how-to you followed tried to tidy up typical places which hold files you won't need (temporary and cached etc.).  I think we should start looking for directories that are too big (which is of course subjective but with a little luck we will spot something funky).

Try the command *df* again but this time add *sudo* and *-a*: **df -a -h** and post the output here please.



Regards
404

---

### Post by acai2 on 2012-02-23
Here you go:

Filesystem Size Used Avail Use% Mounted on
/dev/sda3 11G 9.6G 0 100% /
proc 0 0 0 - /proc
none 0 0 0 - /sys
none 0 0 0 - /sys/fs/fuse/connections
none 0 0 0 - /sys/kernel/debug
none 0 0 0 - /sys/kernel/security
none 493M 284k 493M 1% /dev
none 0 0 0 - /dev/pts
none 497M 0 497M 0% /dev/shm 
none 497M 192k 497M 1% /var/run
none 497M 0 497M 0% /var/lock
none 497M 0 497M 0% /lib/init/rw
/dev/sda2 140G 14G 119G 11% /home
binfmt_misc 0 0 0 - /proc/sys/fs/binfmt_misc

---

### Post by sffvba[e0rt on 2012-02-23
Hi,

Thanks for the reply.  Seems df isn't the command we need :)

Let us try - **sudo du -sh /**

I am suspecting there will be a lot of output (can't do this myself at the moment, not in front of an Ubuntu machine) but in theory it should list all the directories and their sub-directories plus the sizes. Maybe this way we can identify an area that looks unusually large.


404

---

### Post by acai2 on 2012-02-23
Here it is:

du: cannot access '/proc/5126/task/5126/fd/4': No such file or directory
du: cannot access '/proc/5126/task/5126/fdinfo/4': No such file or directory
du: cannot access '/proc/5126/fd/4': No such file or directory
du: cannot access '/proc/5126/fdinfo/4': No such file or directory
23G     /

---

### Post by sffvba[e0rt on 2012-02-23
Hi,

Thanks for your patience thus far (the ways of Linux is very much a learning ground for me too).

Let us modify the last command by adding -x to get past this error; **sudo du -shx /**



404

---

### Post by acai2 on 2012-02-23
Here's the output:

9.5G /

---

### Post by sffvba[e0rt on 2012-02-23
> **acai2 said:**
> Here's the output:

9.5G /

Oh wow... was expecting some more information from that :|

Going to have to wait for some of the guru's to wake up and rescue us both it seems.

Free BUMP then from me.



Good luck
404

PS - As time allows I will continue to try and figure this out myself too...

---

### Post by SuaSwe on 2012-02-23
I'm afraid I'm no guru but thought I'd contribute my two pence! What about the find command?

```

sudo find / -size +10000000 -type d -ls | awk '{print $7,$11}' | sort -n

```

... which I'm hoping will generate a list of directories sorted by size (largest last). Tests OK on my machine at any rate! Note of course, the size may need to be adjusted up or down depending on what sort of files you've got knocking about. :)

---

### Post by matt_symes on 2012-02-23
Hi 

For what it's worth, here's another to give the largest 20.

```
sudo du -h /* | sort -nr | head -n20
```

Change the value of head -n20 as required.

Kind regards

---

### Post by acai2 on 2012-02-23
SuaSwe's output:

find '/proc/1616/task/1616/fd/5': No such file or directory
find '/proc/1616/task/1616/fdinfo/5': No such file or directory
find '/proc/1616/fd/5': No such file or directory
find '/proc/1616/fdinfo/5': No such file or directory

matt_symes output: 

du: cannot access '/proc/1917/task/1917/fd/4': No such file or directory
du: cannot access '/proc/1917/task/1917/fdinfo/4': No such file or directory
du: cannot access '/proc/1917/fd/4': No such file or directory
du: cannot access '/proc/1917/fdinfo/4': No such file or directory
1020K /usr/share/branding/gnome-games-common/cards
1020K /usr/local/MATLAB/R2011b/rtw/c/tlc/lib
1020K /usr/lib/python2.6/lib-tk
1016K /usr/share/xml/iso-codes
1016K /usr/share/gnome/help/empathy
1016K /usr/local/MATLAB/R2011b/toolbox/shared/controllib/general
1016K /usr/local/MATLAB/R2011b/toolbox/control/ctrlutil
1016K /usr/local/MATLAB/R2011b/toolbox/control/control
1016K /usr/lib/totem
1012K /usr/src/linux-headers-2.6.32-33/arch/arm/include
1012K /usr/src/linux-headers-2.6.32-25/arch/arm/include
1012K /usr/src/linux-headers-2.6.31-22/drivers/media/dvb
1012K /usr/share/gdm/themes/HumanList
1012K /usr/doc/libsnmp15
1012K /usr/local/MATLAB/R2011b/toolbox/dsp/dspdemos/demosearch
1012K /usr/local/MATLAB/R2011b/java/jarext/glnxa64
1012K /usr/local/MATLAB/R2011b/java/jarext/glnx86
1012K /usr/lib/python2.6/dist-packages/twisted/python
1012K /usr/lib/perl/5.10.1/auto/Encode/TW
1012K /usr/lib/gtk-2.0/2.10.0/engines



So it seems Matlab is taking up some space here? Also, is there an easy way to copy the terminal output from another pc? Typing that up was painful and I get a permission denied when using 'cmd > output.txt'.

---

### Post by SuaSwe on 2012-02-23
As stated with my command, you may need to adjust that figure - if you get no results based on +10000000 or whatever I type, reduce it until you do. :)

And hmm, that's a point - you should be able to get rid of some of those old headers. There's plenty of stuff about this on the net - perhaps try [this one]("http://ubuntugenius.wordpress.com/2011/01/08/ubuntu-cleanup-how-to-remove-all-unused-linux-kernel-headers-images-and-modules/") or [this]("http://www.foogazi.com/2008/07/02/quickzi-how-to-remove-older-kernels-from-ubuntu/") as a start? :) Just **beware**: you must be very careful not to remove the current version as that will definitely cause some issues!

You probably can't save stuff because you're in a directory mounted on root, which is full - try to output to /home/yourusername/Desktop (I noticed your /home is mounted on another partition so this should work, hopefully!).

---

### Post by acai2 on 2012-02-23
Your first link managed two bring root to 79% usage and get me logged back in! Thanks! Is there a way to add more room to the root filesystem or maybe move those matlab folders? If it's space sensitive enough to keep me from logging in I'd rather not deal with the issue once it's full again.

---

### Post by SuaSwe on 2012-02-23
I'm not really sure how MATLAB is laid out, however you could experimentally move the directories to /home and see if the application still works exactly as you expect - if not, you can always move them back, and if yes, you could delete them. :) The same applies to the other application data in there too (anything not integral to the functioning of the system, of course - always be careful when messing about in /!).

It is possible to resize the partition (using GParted from a LiveCD or USB would be one method) though there's always risk of loss of data doing this. 11GB is an OK size for root I would say; could be that you still have some files in there that could be got rid of. How about /root/.local/share/Trash, for example? You can also follow more general [clean-up strategies]("http://ubuntuforums.org/showthread.php?t=140920") that should help - will be easier now you have a GUI!

---

### Post by sffvba[e0rt on 2012-02-24
Awesome, good to see some progress :)


404

---

