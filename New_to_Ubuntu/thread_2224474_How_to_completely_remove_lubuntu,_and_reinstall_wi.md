---
title: "How to completely remove lubuntu, and reinstall windows 98?"
date: 2014-05-16
forum: New to Ubuntu
---

### Post by Bob_N on 2014-05-16
I tried lubuntu as an alternative for an old hp omnibook xe2, that was slow running windows XP.

But I've gotten stuck on the xorg 'no screens found' issue, and cant get past the dollar sign $ prompt - spent a LOT of time on this, and just want to get back to a usable windows (just want to use this as spare, for wifi internet surfing, to keep in my car trunk when needing info, will NOT be entering any personal details of any kind - windows 98 will work for that)

i tried creating a ms-dos 6 boot diskette, to reinstall windows, but it no longer recognizes my 'C:' drive

how do you competely remove lubuntu, and restore a computer to a state where windows can be reinstalled?

(this was not installed as a dual boot, I saw a lot of forums discussed that)

lubuntu 14.04

(want to go win 98 for 2 reasons: 1) was slow on xp, 2) has the win98 certificate on bottom of laptop, dont want to go digging into other computers to figure out what xp coa was on that laptop before)

---

### Post by sudodus on 2014-05-16
Try ***Knoppix***! It is a linux distro that is very good at recognizing and running old hardware.

---

### Post by papibe on 2014-05-16
Hi Bob_N. Welcome to the forum ):P

I'm not familiar with the MS-DOS installer, so this would be more like suggestions:

Try selecting an option to format the C drive before installing the OS.

If that option does not exist, try to get a DOS command prompt in the process of installing. Once you get 'A:\>' you can format your C: drive (read [here]("http://www.computerhope.com/formathl.htm")).

If none of that is possible, boot into the Lubuntu installation media, as you were to install Lubuntu, but select 'Try Lubunutu', so you can get to the desktop. Once there, open 'Gparted'. You'll see 2 disks available: the installation media, and the hard drive. The size's media should let you know what is what, but a good guess would be your hard disk will be /dev/sdb

Delete all partitions on that drive, and then format the drive using FAT16.

Just some thoughts. Let us know how it goes.
Regards.

---

### Post by stalkingwolf on 2014-05-16
if you are dead set on reinstalling 98 you will have to reformat the hard drive to fat32.  remember also that drivers may no longer be available.

You might also try puppy and/or dsl

---

### Post by HiImTye on 2014-05-16
from what I remember of the Win98 installer, it offers to format the drive for you, so just insert the CD or floppy drives and install away

---

### Post by Bob_N on 2014-05-16
thanks for the replies, a couple of answers

tried puppy linux - same 'no screens found' problem (puppy linux worked fine on another computer though)

in a bootable ms dos 6, i cant see the 'C' drive, so I couldnt format it. i was able to run a win 3.1 instal (used as a pre-req to win98 upgrade), and it said 'setup is unable to create the specified directory on the specified drive' (meaning, it cant see 'C' either)

win98 doesnt run from the cd, even when CD is given priority in the BIOS boot order

---

### Post by HiImTye on 2014-05-16
is it an upgrade CD? then you have to install a previous version of Windows, presumably Win95. it seems you already know this, however.

there's a million resources on the interwebs for Windows installs, and as many forums.

---

### Post by Bob_N on 2014-05-16
> **HiImTye said:**
> is it an upgrade CD? then you have to install a previous version of Windows, presumably Win95. it seems you already know this, however.

there's a million resources on the interwebs for Windows installs, and as many forums.

actually had 2 windows 98 disks, one 'complete', and the other 'upgrade' - i tried using the win 3.1 prerequisit, but then discovered i had a win98 certificate of authenticity stuck to the bottom of the laptop, the complete version disk would be usable

---

### Post by sudodus on 2014-05-16
> **Bob_N said:**
> thanks for the replies, a couple of answers

tried puppy linux - same 'no screens found' problem (puppy linux worked fine on another computer though)

in a bootable ms dos 6, i cant see the 'C' drive, so I couldnt format it. i was able to run a win 3.1 instal (used as a pre-req to win98 upgrade), and it said 'setup is unable to create the specified directory on the specified drive' (meaning, it cant see 'C' either)

win98 doesnt run from the cd, even when CD is given priority in the BIOS boot order

You still have the option to explore ***DSL*** and ***Knoppix***.

What about the hp omnibook xe2 specs?

- CPU (there seems to be more than one alternative)

- RAM size
. if only 32 MB - maybe difficult with linux,
. if 64 MB, DSL works, then it is 'maybe only' a question about graphics
. if 128 MB or more, Knoppix should work.

---

### Post by Bob_N on 2014-05-16
550mhz celeron
256 mg memory

---

### Post by sudodus on 2014-05-16
> **Bob_N said:**
> 550mhz celeron
256 mg memory

This is far above the minimum for hp omnibook xe2, and chances are good for Knoppix and DSL to work :-)

---

### Post by buzzingrobot on 2014-05-16
Any chance a drive needs to be partitioned with DOS' fdisk before it will recognize it as "C:"?

---

### Post by LastDino on 2014-05-16
Your best bet is to do what sudodus is suggesting IMO. Even if you managed to install W98, it wont be usable. From what I remember; you do need to format with DOSfdisk to make your C: to be bootable, you will need bootable floppy or disk to do that.

---

### Post by Bob_N on 2014-05-16
ubuntu is the 'Hotel California' of OS

---

### Post by Mark Phelps on 2014-05-16
From what you said, you can get to a command prompt in Lubuntu.  That being the case, run the following command: (sudo fdisk -lu" (lowercase L, not a one) -- that will list out the filesystems and partitions on your drives.  IF XP was running REALLY SLOW, that could be an indication of a failing drive.

---

### Post by Bob_N on 2014-05-17
well, I did get D small linux to boot up, but am having trouble getting it to connect (was easy with puppy linux on another computer, but the computer in question gets 'no screens found' xorg error w/puppy)

it looks like it doesnt have a site survey (you have to know the name you are connecting to), and it only takes a WEP key (the one I am connecting to needs WPA - which works fine with puppy linux on another computer)

looked at knoppix, but it's almost 4 gig

---

### Post by sudodus on 2014-05-17
DSL is old, so I can understand that it might not connect via wifi - too bad. And too bad Puppy does not work for you. By the way, there are several versions of Puppy, did you try ***Puppy Wary***?

[http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm](http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm)

The next distro to try might be ***Tiny Core Linux*** or rather **[CorePlus]("http://distro.ibiblio.org/tinycorelinux/5.x/x86/release/CorePlus-current.iso")** for wifi
[URL="http://distro.ibiblio.org/tinycorelinux/downloads.html"]
http://distro.ibiblio.org/tinycorelinux/downloads.html[/URL]

---

### Post by Bob_N on 2014-05-17
> **sudodus said:**
> DSL is old, so I can understand that it might not connect via wifi - too bad. And too bad Puppy does not work for you. By the way, there are several versions of Puppy, did you try ***Puppy Wary***?

[http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm](http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm)

The next distro to try might be ***Tiny Core Linux*** or rather **[CorePlus]("http://distro.ibiblio.org/tinycorelinux/5.x/x86/release/CorePlus-current.iso")** for wifi
[URL="http://distro.ibiblio.org/tinycorelinux/downloads.html"]
http://distro.ibiblio.org/tinycorelinux/downloads.html[/URL]

wary puppy WORKS!!!!

connected right off the bat

THANKS TO ALL WHO HELPED!!!!!

---

### Post by sudodus on 2014-05-17
Congratulations :KS

If your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by Bob_N on 2014-05-17
> **sudodus said:**
> Congratulations :KS

If your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

done, and thanks again

---

