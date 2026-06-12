---
title: "UGH just upgraded to Hardy and having an issue!"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by andyho on 2008-05-21
I've waited quite some time before upgrading to Hardy.. heck, I barely had Gutsy running good after finally getting Feisty all worked out! But now I've got...

"init rc-default main process (5731) killed be SEGV signal"

after upgrading! I'm assuming it might have something to do with my nvidia drivers? I always seem to have problems with them. But just in case it's not the drivers, any other ideas? Thanks!!

---

### Post by cmnorton on 2008-05-21
What is your hardware configuration?

---

### Post by stchman on 2008-05-21
> **andyho said:**
> I've waited quite some time before upgrading to Hardy.. heck, I barely had Gutsy running good after finally getting Feisty all worked out! But now I've got...

"init rc-default main process (5731) killed be SEGV signal"

after upgrading! I'm assuming it might have something to do with my nvidia drivers? I always seem to have problems with them. But just in case it's not the drivers, any other ideas? Thanks!!

Did you go the upgrade route or did you do a clean install?  I recommend a clean install as it is faster and less likely to give errors.

---

### Post by andyho on 2008-05-22
> **stchman said:**
> Did you go the upgrade route or did you do a clean install?  I recommend a clean install as it is faster and less likely to give errors.

No, of course I went the upgrade route.. UGH! My own dumbness there...

---

### Post by andyho on 2008-05-26
Ok.. so here's EXACTLY what I get at bootup..

*Setting the system clock
Segmentation fault
*Loading kernel modules... [OK]
*Loading manual drivers... [OK]
*Setting kernel variables...
*Activating swap...
...done.
mount: you must specify the filesystem type
[COLOR="Red"]*[/COLOR]Cannot check root file system because it is not mounted read-only
Segmentation fault
*Starting early crypto disks... [OK]
*Starting remaining crypto disks... [OK]
*Checking file systems...
1207
fsck 1.40.8 (13-Mar-2008)
                              [OK]
Segmentation fault
Segmentation faultfilesystems...
[OK]
*Activating swapfile swap... [OK}
*Checking minimum space in /tmp... [OK]
*Skipping firewall: ufw(not enabled)... [OK]
*Configuring Network interfaces... [OK]
init:rc-default main process (5254) killed by SEGV signal


So is it that I have a bad mount point?? 

CMNORTON: How can I get my hardware configuration to all show? I tried lshw, but I could only see part of it. 

If I kill X-server I can log in.. so I'm hoping it's something that's still fixable!! :)

---

### Post by andyho on 2008-05-26
Even more info... I've tried booting into other kernel's but no such luck there. However, I did just get this to show up..

*Checking root file system...
1207
...fail!
[COLOR="DarkRed"]*[/COLOR]An automatic file system check (fsck) of the root filesystem failed. A manual fsck must be perfomed, then the system restarted.
The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
[COLOR="DarkOrange"]*[/COLOR]The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance. press ctrl+d to terminate the maintenance shell and restart the system.
bash: no job control in the shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found

HTH some more... still trying to figure what's causing this...

---

### Post by philinux on 2008-05-26
when you hit the cli type

fsck -v

the -v switch is for verbose.

---

### Post by andyho on 2008-05-26
> **philinux said:**
> when you hit the cli type

fsck -v

the -v switch is for verbose.

Ok when I do that I get..

/dev/sda1 is mounted.

WARNING!!! Running e2fsk on a mounted filesystem may cause SEVERE filesystem damage.

Do you really want to continue(y/n)?

Do I?!? LOL!

---

### Post by andyho on 2008-05-26
Hmm I just noticed something weird.. one minute it had me as root for some reason, that's when it gave me what I last posted.. This time though it says...

andyho@andyho-ubuntu:~$ fsck -v
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=bfcf5100-02eb-4274-b599-72545d15005'

?!?!

---

### Post by andyho on 2008-05-27
anyone?!?

---

### Post by cmnorton on 2008-05-28
> **andyho said:**
> 
CMNORTON: How can I get my hardware configuration to all show? I tried lshw, but I could only see part of it. 



/proc/devices has some more information.

---

### Post by andyho on 2008-05-31
Ok well I had posted, but for some reason it didn't go thru.. UGH! More lost time.. anyways... 

If I try to access /proc/devices I can see it for a brief moment and then usually the system crashes. Is there something specific I should be looking for in there? Is there anything else I can try to get my system back to working?? I know it has to be something pretty dumb... Another thing I notice at bootup is something about a swap fail.. did I already put that previously in my post? I think there may be a secondary partition or something that was created at upgrade and that's where things are getting messy.. I really hope I can get this working by tomorrow.. WHERE did the irc chat go?!?! I can't access it at all!?!

---

### Post by andyho on 2008-05-31
Here is what I get in /proc/devices..

Character devices:
1 mem
2 pty
3 ttyp
4 /dev/vc/0
4 tty
4 ttys
5 /dev/tty
5 /dev/console
5 /dev/ptmx
6 lp
7 vcs
10 misc
13 input
14 sound
21 sg
29 fb
116 alsa
128 ptm
136 pts
171 ieee1394
180 usb
189 usb_device
254 usb_endpoint

Block devices:
1 ramdisk
2 fd
8 sd
11 sr
65 sd
66 sd
67 sd
68 sd
69 sd
70 sd
71 sd
128 sd
129 sd
130 sd
131 sd
132 sd
133 sd
134 sd
135 sd
254 device-mapper

HTH!! :)

---

### Post by cariboo on 2008-05-31
Sounds like you are suffering from a hard drive failure. If you've got another computer go to your hdd manufactures web site and download the diagnostic tools and check your hard drive.

JIm

---

### Post by andyho on 2008-05-31
Nope.. hard drive is fine. :)

---

### Post by andyho on 2008-05-31
cheeeese whiz.... my god if this isn't confusing the h=ll outta me!! Ok so just booted up again and got the whole manual fsck needs performed.. so I go ahead and fsck once again.. and get...

fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1: clean; 383934/18972672 files, 18907091/37939497 blocks


any ideas now?? for some reason though I can't get into /dev/sda now and I KNOW sda5 was giving me issues because before it was showing the UUID for it and now it's showing sda1?!?!? For a brief second I had something pop up about restarting normal, fixing blocks or fixing x and then it crashed... :/

---

### Post by andyho on 2008-06-02
guess I'm not the only one perplexed?!? :lolflag:

---

### Post by andyho on 2008-06-04
Ok.. so I was miraculously able to get into my home folder last night and everything is still there!! YEA!! So I think I will probably just move everything and start with a fresh install. Quick ? though... with my syatem jacked up as is, will I be able to plug in my external usb hd and will it recognize it?!?!? THANKS!!!!

---

### Post by bobpur on 2008-06-04
OK, I don't know a lot about your earlier issues on this thread; but, speaking from experience, you could be re-installing all of your problems again. What I mean is that you might have a corrupted burn on the USB drive (flashdrive?). Burn a cd with a good ISO burner at a slow speed (4X or so) and try a fresh install from that using your computers cd drive. Assuming that it does have a cd drive. Specs?? :)

Good Luck!

---

### Post by andyho on 2008-06-04
Bob: Right now I don't have anything installed on usb. All I'm wondering now is if I plug in my external usb hd, will the system be able to recognize it so that I can move all the stuff off my primary so that I can just start with a fresh install? I've tried rescue with an install disk, but no such luck there. At least I'm able to get into irc now so maybe someone will be on there! :)

---

### Post by starcannon on 2008-06-04
you will need to run 
```
sudo blkid
```

then your going to need to fix your /etc/fstab file with the appropriate uuid's that blkid spits out.

You may also need to update your /boot/grub/menu.lst file with correct uuid's not for certain though, anyway that should get you pointed in the right direction. 

If you have /home on its own partition and this gets to whacky you could just do a fresh install in 45 minutes. If /home and / and /boot are all sharing the same partition though, well then its a bit more work.

---

### Post by andyho on 2008-06-04
yeah unfortunately they're on the same partition :(

but thanks for the info.. off to see if I can get things workin :)

---

### Post by andyho on 2008-06-05
nope.. still no luck.. though I did switch over from my nvidia card to my onboard and I'm not having as many lockups! And I plugged in my usb external and it shows up, so now I'm just trying to figure out the command for copying over to it so I can save what I need to and start fresh!!

---

