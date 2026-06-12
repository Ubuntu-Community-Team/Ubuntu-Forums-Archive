---
title: "Complete Failure"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by jyxxie on 2008-10-03
I have tried reinstalling Ubuntu to solve this, but nothing seems to work. And now I'm locked out of ubuntu; the only file access I have is PuppyLinux or Ubuntu LiveCD.

Here's my problem.. Whenever I install something new or watch a movie, I lose sound. Then I want to save text from my IM, but gedit won't start up. Firefox freezes. Terminal doesn't come up. I click the Power icon to shut down; nothing comes up, and the only way to shut down is pulling the battery out of the laptop or Alt+SysReq+reisub. Then I tried logging back into Ubuntu; the text is oversized and I can't read it all, something about saving and 644?

Any help would be appreciated.. thank you very much.

Specs: Ubuntu 8.04 LTS
Dual-Boot with Windows XP
Toshiba Satellite Laptop

---

### Post by jyxxie on 2008-10-04
I'm not sure if this is a hardware issue or if it's my laptop's age and history of constant spyware/viruses/malware/etc attacking it..

I'd like to check my hardware but I've no clue how. If all else fails I may have to go get another computer soon.

I haven't tested the main codec packages, like flashplugin-nonfree on my grandmother's ubuntu computer--a brand new Acer desktop, compared to my 3 or 4 year old laptop.

Could it be a hardware incompatibility even?
I'm lost.
Sorry. x_x;

---

### Post by Crafty Kisses on 2008-10-04
What are the laptops specs?

---

### Post by jyxxie on 2008-10-04
Call me pathetic.. but how do I check?
I'm stuck in WinXP right now. Google didn't tell me anything.

---

### Post by Paqman on 2008-10-04
> **jyxxie said:**
> something about saving and 644?


Is it talking about something called .dmrc?

Try throwing these commands into a terminal:

```

sudo chown -R  username:username /home/username
sudo chmod 755 /home/username
sudo chmod 644 /home/username/.dmrc

```

These commands will make sure that all the file ownership and permissions in your /home are correct.

---

### Post by jyxxie on 2008-10-04
Paqman:
For some reason, the font for the login page and whatever that message said, is at like, 72 pt and I don't know how to fix it--so I'm locked out of ubuntu for that reason; I can't hit enter to get past it, there's no scroll option and there's nothing to click..

Can I use a LiveCD to fix any of this?

---

### Post by Cato2 on 2008-10-04
> **jyxxie said:**
> Call me pathetic.. but how do I check?
I'm stuck in WinXP right now. Google didn't tell me anything.

In Windows, you can go into Control Panel, open the System icon, and it tells you some basic info such as CPU, memory and I think also disk size.   Key question is memory - if you have less than 512 MB, Ubuntu will run very slowly.  Are you sure it's really frozen, or is it simply doing a LOT of disk access.

Your problems are nothing to with spyware.  They might be failing hardware, or it might simply be lack of memory - but normally Ubuntu works even on old hardware, except some things are very slow or don't work (e.g. sound may not work, video may be slow, etc.)

Since the Ubuntu live CD works it seems your hardware is basically good, but perhaps your installation has been corrupted.

Within the live CD, it would be worth running the Hardware Test tool from the menus - it runs through all your hardware to see if it works.  To test memory, at the boot screen of live CD, choose the memory test and leave it running for a few hours, ideally overnight.

Testing the disk is a bit harder, but it would be good to run an 'fsck' - get into a Terminal in live CD, then do ```
sudo fsck /dev/sda1
```, then the same again with fsck /dev/sdb1.  Say yes to any fixes that it wants to make.

Check the /var/log/messages file using gedit, to see if there are any errors reported there, particularly around the times you've had the problems.  In fact, have a look through the files most recently modified in that directory (use Nautilus to sort by time) and see if there are any errors reported.


Try to configure a swap file - google for HOWTOs, it's quite easy - command is 'swapon'.  Use 'swapon -s' to see if you have one already.  You don't need a swap partition but if you are short of memory it really helps.  In Ubuntu 'top' from terminal tells you memory etc.

Final suggestion - once you've done the above to diagnose the problem a bit more, and know if any hardware is failing, I would simply do a re-install from the Live CD.  Back up any data you need to keep onto a USB stick or something, of course.


Good luck!

---

### Post by nowshining on 2008-10-04
if u have random errors constantly, things suddenly quit and disappear on u, esp. after a fresh install - it's more than likely that 98.9% of it is ur HD failing, backup whatever u can - and get a new Hard Drive...

edit: if ur wondering how i should know - well it's because i had similar probs when an ol' seagate HD was going out.. :/ it was while using windows tho...

---

### Post by jyxxie on 2008-10-04
I managed to get back into Ubuntu, and here's what I got in Terminal:

jyx@jyx-lappy:~$ sudo chown -R  jyx:jyx /home/jyx
chown: cannot access `/home/jyx/.gvfs': Permission denied
jyx@jyx-lappy:~$ sudo chmod 755 /home/jyx
jyx@jyx-lappy:~$ sudo chmod 644 /home/jyx/.dmrc
jyx@jyx-lappy:~$ sudo fsck /dev/sda1
fsck 1.40.8 (13-Mar-2008)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda1

jyx@jyx-lappy:~$ sudo fsck /dev/sdb1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: No such file or directory while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

jyx@jyx-lappy:~$ 


I still need to find out how to change the gigantic font of the menu/login screen to a smaller size..

---

### Post by Cato2 on 2008-10-08
> **jyxxie said:**
> I managed to get back into Ubuntu, and here's what I got in Terminal:
...
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda1
...
fsck.ext2: No such file or directory while trying to open /dev/sdb1

OK, this looks like NTFS (Windows filesystem) is on first partition of disk 1 (/dev/sda1) so your Ubuntu should be on /dev/sda2 or /dev/sda3 - try sudo fsck again on those.
> 
I still need to find out how to change the gigantic font of the menu/login screen to a smaller size..

Not sure how to fix that, but it's a relatively minor problem that can be fixed later.  

Running hardware tests, particularly memory test, would be a good idea too.  Memory test is a very easy thing to do.  Also, just try re-installing Ubuntu - if you get the same sort of problems, it's probably your hardware at fault.

Also my other suggestions are worth trying as well, particularly looking in the log file for errors - just post it here as an attachment if you can.

---

