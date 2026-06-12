---
title: "What happen to my ubuntu???"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by kjacobs on 2008-12-01
So much for Thanksgiving....

I have been running ubuntu 8.04 for the past 1 1/2 weeks. It's been working wonderful. I turned off the computer for the weekend holiday. Now I turn it back on only to have ubuntu spitting out lines of command prompt text and not booting.

Some of the lines are reading:

Buffer I/O error on device sda....blah, blah
Exception EMASK...blah, blah

What in the world happened? Does it mean I can't turn off the computer, otherwise it quits working?

This has happened other times as well when I have tried linux in the past, even with other computers. Works great until the next time I boot up....

---

### Post by SunnyRabbiera on 2008-12-01
odd, did you have any mission critical updates of late?
I know there was a kernel patch just recently and it could be the blame of your issue.

---

### Post by kjacobs on 2008-12-01
> **SunnyRabbiera said:**
> odd, did you have any mission critical updates of late?
I know there was a kernel patch just recently and it could be the blame of your issue.

I'm not sure....I know that when the update icon came on, I clicked to download updates, so I assume it is possible that an update could have caused it. The most recent update I think was the beginning or middle of last week.

---

### Post by Dj Melik on 2008-12-01
Can you at least boot the the recovery mode?

---

### Post by prshah on 2008-12-01
> **kjacobs said:**
> 
Buffer I/O error on device sda....blah, blah
Exception EMASK...blah, blah
What in the world happened? Does it mean I can't turn off the computer, otherwise it quits working?


This is sometimes due to logical filesystem damage (and rarely physical). I often get this error if the system is not shutdown properly. To resolve it, I boot off a live CD, and run fsck on the filesystem
```

sudo fsck -a /dev/sda1

```

Replace /dev/sda1 with the actual partition ID in your case. Repeat for every linux partition that you have (excluding swap). ENSURE that the filesystem(s) in question is UNMOUNTED (Hence the boot off live CD).

If you get an error such as "Unexpected inconsistency - run fsck manually", then you have to run it without the "-a" switch. The status messages when running fsck will be interspread with messages similar to the one above; you can ignore them. When asked to fix anything, give "y" (in fact, I just pres Y+Enter 15 times and then leave the system to do it's thing). You can also try the "-y" flag (assume "Yes").

There is a very real possibility of data loss; so you do this at your own risk. In my own case, I have often lost package information, but luckily enough no data and/or critical files. YMMV.

Post back with your results. If the error persist even after fsck, you may have bad sectors. Post back for details on how to check this.

---

### Post by kjacobs on 2008-12-01
Thanks for the info...however, I just tried booting from the cd. At first it looked like it would boot up, then it went back to spitting out command line text like before, without booting up. So booting to cd was not successful.

---

### Post by alphacrucis2 on 2008-12-01
> **kjacobs said:**
> Thanks for the info...however, I just tried booting from the cd. At first it looked like it would boot up, then it went back to spitting out command line text like before, without booting up. So booting to cd was not successful.

If it booted ok from that cd in the past, sounds like you might have a hardware problem. Can you boot the memtest option from the cd?

---

### Post by dmizer on 2008-12-01
Are you sure your BIOS is set to boot to CD? It may simply be set to boot hard drive before CD.

If you are running 64 bit (this problem could also be present in 32bit), I believe your problem is with hard drive /dev location, more information here: [http://ubuntuforums.org/showthread.php?t=987612](http://ubuntuforums.org/showthread.php?t=987612)

---

### Post by prshah on 2008-12-01
> **kjacobs said:**
> Thanks for the info...however, I just tried booting from the cd. At first it looked like it would boot up, then it went back to spitting out command line text like before, without booting up. So booting to cd was not successful.

Try booting off any other linux live CD; puppy usually works fine for me. 

Or try to get a USB flash disk / thumb drive and setup linux to boot off it.

Or, if you can manage to get to a command prompt (for example, in recovery mode), give the command ```
sudo touch /forcefsck
``` and reboot.

---

### Post by levelup2 on 2008-12-01
I have the same problem and now it has been sorted!

---

### Post by redseventyseven on 2008-12-01
> **levelup2 said:**
> I have the same problem and now it has been sorted! It would be very helpful if you could share how you solved it!

---

### Post by kjacobs on 2008-12-01
Thanks everyone for all the input. I tried booting to puppy 4.1.1 cd and the machine booted fine. I ran: fsck -y /dev/sda1 from a terminal in puppy and it supposedly fixed a couple errors. So I rebooted back to the hard drive again. Still no go, lots of text stuff. I tried rebooting to the ubuntu cd, same problem.

How do you get to recovery mode from the live cd? I tried a couple different options from the live cd (safe graphic, etc.) but there is no "recovery mode"....

---

### Post by dmizer on 2008-12-01
It would be really helpful if you could post some of what the text is saying. Repetative messages, any kind of errors you can catch would be extremely useful. I understand that you can't catch everything, but even a small thing can be helpful. Otherwise, we're just shooting in the dark.

---

### Post by kjacobs on 2008-12-01
Usually when I start the computer, the ubuntu logo and status bar show up. After the status bar bounces back and forth for a while, the screen goes black. Here is what the text starts reading once the screen goes black...

ata1.00: exception Emask 0x0 Sact 0x0 SErr 0x0 action 0x2 frozen
ata1.00: cmd c8/00:01:00:5f:64/00:00:00:00:00 ez tag 0 dma 512 in
Buffer I/O error on device sda1, logical block 40132352
ata1.00: status: {dDRDY}

The exception Emask line repeats quite a bit. The cmd line repeats with a different dma #. The buffer i/o error repeats with a different logical block #.

It still doesn't make sense that it was working wonderul when it was turned off, then started doing this after the weekend....

---

### Post by xikarrousx on 2008-12-01
When you turn on your computer, it will say "Loading Grub menu" and something about pressing escape to load it or whatever. In this grub menu, you should see a list of a few different versions of ubuntu and whatever other operating systems you might have. 

simply, try loading the next oldest ubuntu version and see if that changes anything.

---

### Post by phidia on 2008-12-01
If you google > ata1.00: exception Emask 0x0 Sact 0x0 SErr 0x0 action 0x2 frozen you will find several bugs-most of them have expired but you could [report this]("https://help.ubuntu.com/community/ReportingBugs") at launchpad.

---

### Post by kjacobs on 2008-12-01
> **xikarrousx said:**
> When you turn on your computer, it will say "Loading Grub menu" and something about pressing escape to load it or whatever. In this grub menu, you should see a list of a few different versions of ubuntu and whatever other operating systems you might have. 

simply, try loading the next oldest ubuntu version and see if that changes anything.

AHA!!! Yes!!!! Thank you!!! I rebooted the machine and hit ESC. First i tried the 2.6.24.21 recovery mode. However, that again brought up my never ending screen of text. The primary hangup seemed to be "Unable to turn cooling device on". Then I restarted again and tried 2.6.24.19 normal and the machine booted up just great. In fact, I'm using it for this message.

Now, will the machine boot normally from now on or do I need to do something???

---

### Post by phidia on 2008-12-01
As long as you choose the working (older) kernel you should be ok. You may want to comment out the kernel that's causing problems in /boot/grub/menu.lst.

---

### Post by kjacobs on 2008-12-01
Thanks again...one more thing, though. I opened the menu.lst in the file manager to comment out the two bummer kernels, but it will not let me save the file....no permission. How do I get it to let me save?

---

### Post by maheshjr2000 on 2008-12-01
I recommend you double check what dmizer said. Make sure you are REALLY booting from the CD.

---

### Post by kjacobs on 2008-12-01
Actually, the machine is booting okay again from the hard drive with a slightly older kernel from the grub menu. I just need to know how to get permission to save the menu.lst changes from the file manager....

---

### Post by lswb on 2008-12-01
You can change your grub menu to use the 2.6.24.19 kernel by default, the comments in /boot/grub/menu.lst explain how. (It must be edited as root; use sudo vi, sudo nano, or gksudo gedit)

Is it possible that power was interrupted while the update to the .21 kernel was in progress? Might be worth while reinstalling the newer kernel & rechecking if so.

Reporting the bug per the link phidia posted will help the developers get it fixed for the next update.

---

### Post by kansasnoob on 2008-12-01
> **kjacobs said:**
> Actually, the machine is booting okay again from the hard drive with a slightly older kernel from the grub menu. I just need to know how to get permission to save the menu.lst changes from the file manager....

```
sudo gedit /boot/grub/menu.lst
```

But be careful! Or install startupmanager from synaptic.

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

---

### Post by dmizer on 2008-12-01
Please open a terminal, run the following commands, and post the output here.
```
sudo blkid
df -Th
cat /etc/fstab
```

---

### Post by kjacobs on 2008-12-02
Here are the results...

kenneth@kenneth-linux:~$ sudo blkid
[sudo] password for kenneth: 
/dev/sda1: UUID="f29be360-b1bf-4c70-9c28-724c5adffc76" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="db41a368-a18b-43ec-b51a-71c99e03838a" 
kenneth@kenneth-linux:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3     19G  3.0G   15G  18% /
varrun       tmpfs    506M  104K  506M   1% /var/run
varlock      tmpfs    506M     0  506M   0% /var/lock
udev         tmpfs    506M   64K  506M   1% /dev
devshm       tmpfs    506M   12K  506M   1% /dev/shm
lrm          tmpfs    506M   39M  467M   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon     19G  3.0G   15G  18% /home/kenneth/.gvfs
kenneth@kenneth-linux:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f29be360-b1bf-4c70-9c28-724c5adffc76 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=db41a368-a18b-43ec-b51a-71c99e03838a none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
kenneth@kenneth-linux:~$

---

### Post by maheshjr2000 on 2008-12-02
> **maheshjr2000 said:**
> I recommend you double check what dmizer said. Make sure you are REALLY booting from the CD.

wow theres a case of not reading then entire thread XD my bad.

---

### Post by kjacobs on 2008-12-02
Here's an update...the most recent update (2.6.24-22) was downloaded today and, after rebooting, still seems to work fine. So I guess something about 2.6.24-21 didn't like my machine. Thanks again to all who helped. Eventually I will become as familiar with ubuntu as I am with "the other one".

---

