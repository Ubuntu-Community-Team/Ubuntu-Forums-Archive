---
title: "Windows starting up... error"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by madmanmick on 2008-05-02
Hi,
I am new to Ubuntu (evidently). This is my second foray into Linux, as the first proved to completely hopeless (could not get a Kubuntu install to work properly).

I am currently using my Ubuntu operating system, but the problem lies in that i cannot dual boot windows.

Here is my HDD boot sequence:

1) Channel 0 SAMSUNG 80gb (Linux drive, includes GRUB)
2) Channel 1 MAXTOR 250gb (Windows install and MBR on this drive)
3) Channel 0 MAXTOR 250gb (Storage drive)

Here is my GRUB config for Ubuntu, which works fine.
Root (hd0,0)

*At time of writing, I just tried to run gksudo gedit boot/grub/menu.lst to get the exact GRUB parameters, but for some reason my menu.lst is totally blank! WHAT HAS HAPPENED*

Either way, Ubuntu still boots fine even though my menu.lst seems to be blank... aside from this, my Windows is set to boot from:
Root (hd1,0) - As this is the hard drive number
Savedefault
Makeactive
Chainloader+1

This boots up the "starting up..." message, and then sits there with a blinking cursor.

I tried adding the commands:
Map (hd0) (hd1)
Map (hd1) (hd0)

But that caused me to receive a GRUB error.

Also, I then tried to have it set to: Root (Hd2,0), and that gave me the same "starting up..." hang.

Could it be that this particular HDD is set to Channel 1 instead of Channel 0? Does that denote the drive is a slave?
No amount of fiddling with the parameters has gotten it to work yet.
Please help!
Thanks.

EDIT: After posting, my menu.lst now seems to be showing up.
These are the parameters for the Ubuntu boot sequence:
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=228caacb-b637-49c1-b3b3-690536963eb7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

And these are the parameters for WINDOWS XP:
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
chainloader	+1

... Any ideas?

---

### Post by madmanmick on 2008-05-02
Anyone?

---

### Post by zvacet on 2008-05-02
You can try few options but they all have to be below this line 

### END DEBIAN AUTOMAGIC KERNELS LIST


1. rootnoverify (hd1,0)
   makeactive
   map (hd0) (hd1)
  map (hd1) (hd0)  
  chainloader +1

or 

root (hd1,0)
makeactive
chainloader +1

I hope it will work for you.

---

### Post by madmanmick on 2008-05-02
I tried using the map commands, only caused it to give me errors instead of just lingering at the starting up... bit. Can anyone else offer an opinion?

---

### Post by zvacet on 2008-05-02
Did you tried second option?

---

### Post by madmanmick on 2008-05-02
The second options is the standard entry in my GRUB... that's what doesn't work in the first place. Are there no tech heads who patrol the beginner forums?

---

### Post by halitech on 2008-05-02
when you installed, did you install grub to the MBR or on the first partition of the linux drive only?

---

### Post by madmanmick on 2008-05-03
I installed GRUB to the samsung hdd, which only has linux on there. i kept grub off my windows partition, last time i tried that it caused me nothing but grief...

---

### Post by madmanmick on 2008-05-04
If no one can help me in this forum, is it possible to have this thread moved to General Help or another forum where more people would be able to help me? Right now I have to resort to using Windows, until its happy to dual boot... (I have to change the boot order of the hard drives every time i want to change OS, what a joke!)

---

### Post by madmanmick on 2008-05-04
After fiddling with the boot sequence, I determined two orders, one that would allow each system to boot. I tried to switch the cables on the motherboard to their correct slots (I tried to move the linux drive to SATA2 port 1 and have it set as first hard drive to boot) but no amount of fiddling yielded a good result.

As it stands now something has gone wrong with the ubuntu drive and I am receiving error 17 at GRUB loading stage 1.5. I am certain now that it is something to do with the channel of the hard drive, my linux drive being Ch 0 and Slave, Windows drive being Ch 1 Master, and spare drive being Ch 0 Master.

When i moved them around the motherboard ports to try and make each a master and channel 1, it made no difference. After pulling the plug on both my NTFS drives (windows and spare), it seems that the NTLDR is on one of them and the actual operating system is on the other! Im guessing here, because when i unplugged one (using the guaranteed boot order that loads windows xp) it gave me the missing NTLDR error, and when I unplugged the other drive (re-plugging the previous one) I had an error saying 'missing file hal32.dll'... To my understanding this denotes that the actual WINDOWS OS is on one hdd (containing all the files) and the other drive contains the MBR, that refers back to WINDOWS install on the other drive.

I dont know how this could have happened because when I installed Windows it was solely on the one hard drive - unless again this relates back to the Channel and master problem i stated before.

I tried unsucessfully to unplug the drive that i thought had the MBR on it, and ran a fixboot and fixmbr on the drive I thought had the XP OS installed. This didn't work at all, it just made me have to switch the boot order of the two drives in the BIOS to load Windows.

I am totally perplexed - surely there is someone here who can help? I have tried many other suggestions from other posts pertaining to similar issues, yet nothing works (and yes that includes the fabled Map (hd0) (hd1) crap...).

I am still convinced it is something to do with the channel and master properties of the hard drives. Is there anyway to account for the channel settings of a hard drive in GRUB booting?

Thanks guys.

---

### Post by madmanmick on 2008-05-04
Bump?

---

### Post by madmanmick on 2008-05-06
Is no one able to help me?

---

