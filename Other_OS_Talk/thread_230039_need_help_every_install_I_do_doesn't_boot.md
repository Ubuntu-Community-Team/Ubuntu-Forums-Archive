---
title: "need help: every install I do doesn't boot"
date: 2006-08-05
forum: Other OS Talk
---

### Post by RAV TUX on 2006-08-05
Ok as you may know FreeBSD wiped my XPsp2...on my newer computer...

here is the problem with every install I do

Gentoo
Dreamlinux
Musix
PC-BSD
etc

The installs are fine but the boot loaders are not working and I am getting an error, I tried to boot from my Super Grub CD still no luck 

any help would be great...

(also I have been unable to load Ubuntu get a error with the Xserver or something of that nature?)

---

### Post by 23meg on 2006-08-05
> the boot loaders are not working and I am getting **an error**What error?

---

### Post by RAV TUX on 2006-08-05
> **23meg said:**
> What error?

I'll have to try it again, I didn't write down the error number:oops:

---

### Post by RAV TUX on 2006-08-05
error 21

---

### Post by K.Mandla on 2006-08-05
I don't remember if it's error 21 or error 15 I was getting when I had a missing grub configuration file. 

I had a dual boot and crapped out my Ubuntu partition, and so the file wasn't there to be read. Grub just gave me error ... I think it was 21, but I don't remember for sure.

If it were me, I would [Killdisk ]("http://www.killdisk.com")the entire drive and start over clean ... if that's an option. 

Good luck. ;)

---

### Post by RAV TUX on 2006-08-05
> **K.Mandla said:**
> I don't remember if it's error 21 or error 15 I was getting when I had a missing grub configuration file. 

I had a dual boot and crapped out my Ubuntu partition, and so the file wasn't there to be read. Grub just gave me error ... I think it was 21, but I don't remember for sure.

If it were me, I would [Killdisk ]("http://www.killdisk.com")the entire drive and start over clean ... if that's an option. 

Good luck. ;)

That could be a possibility as a last resort...

I was able to load only one Distro openSUSE 10....but I have to configure the DSL connection, printer and sound card.

I can't shut it down because the bootloaders don't work.

---

### Post by rattlerviper on 2006-08-06
> **yozef said:**
> Ok as you may know FreeBSD wiped my XPsp2...on my newer computer...

here is the problem with every install I do

Gentoo
Dreamlinux
Musix
PC-BSD
etc

The installs are fine but the boot loaders are not working and I am getting an error, I tried to boot from my Super Grub CD still no luck 

any help would be great...

(also I have been unable to load Ubuntu get a error with the Xserver or something of that nature?)


Just noticed this thread.  How weird is that?  Are these disks that have worked before?  Is this the pc that FreeBSD did in?  I don't uderstand what's going on there, you definantly have a list of first class software it just doesn't make much sense.  This is going to sound really harsh, but have you tried installing windows?  Whenever I get my hard drive to messed up, I start a windows xp install telling it to take over the whole hard drive.  Then I just install whatever distro I want right over the top of it.  Guess I got in the habit of using windows to fix it when I was a dual booter.  
Now that I think of it Windows XP does have a use for me LOL.

---

### Post by kabus on 2006-08-06
> 21 : Selected disk does not exist
This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.
.

---

### Post by RAV TUX on 2006-08-06
> **rattlerviper said:**
> Just noticed this thread.  How weird is that?  Are these disks that have worked before?  Is this the pc that FreeBSD did in?  I don't uderstand what's going on there, you definantly have a list of first class software it just doesn't make much sense.  This is going to sound really harsh, but have you tried installing windows?  Whenever I get my hard drive to messed up, I start a windows xp install telling it to take over the whole hard drive.  Then I just install whatever distro I want right over the top of it.  Guess I got in the habit of using windows to fix it when I was a dual booter.  
Now that I think of it Windows XP does have a use for me LOL.

I actually figured it out and the results are in this thread:

[http://www.ubuntuforums.org/showthread.php?t=230361](http://www.ubuntuforums.org/showthread.php?t=230361)


(by the way I did get desperate enough to reload windoze but since Dell set the Master Drive to my CD drive and NOT my DVD drive I couldn't reload windows which is on DVD!!!!

HAHA!!!! how ******* funny is that!!!!;))

anyway that is another problem I have to fix....I opened the box up and those tape looking wires scared the hell out me....no I will save that for another day that I actually get some sleep!:(

---

### Post by rattlerviper on 2006-08-06
> **yozef said:**
> I actually figured it out and the results are in this thread:

[http://www.ubuntuforums.org/showthread.php?t=230361](http://www.ubuntuforums.org/showthread.php?t=230361)


(by the way I did get desperate enough to reload windoze but since Dell set the Master Drive to my CD drive and NOT my DVD drive I couldn't reload windows which is on DVD!!!!

HAHA!!!! how ******* funny is that!!!!;))

anyway that is another problem I have to fix....I opened the box up and those tape looking wires scared the hell out me....no I will save that for another day that I actually get some sleep!:(


It was the bios setting?  That would really frustrate me to spend all the time trying to figure it out and have it be the bios.  At least it is solved and it sounds like you've got a REALLY NICE OS on there now.  DreamLinux is sweet!

---

### Post by RAV TUX on 2006-08-06
> **rattlerviper said:**
> It was the bios setting?  That would really frustrate me to spend all the time trying to figure it out and have it be the bios.  At least it is solved and it sounds like you've got a REALLY NICE OS on there now.  DreamLinux is sweet!

I don't know how I did it this morning but I accidently deleted my 'Home' folder and 'Computer' folder but when I did a re-install I got the infamous GRUB error 17 this time....so I installed Knoppix rather quickly but I have to say I will probably re-install Dreamlinux when I get home.

I am thinking I may do a quad boot for a while....


1. Dreamlinux
2. Sabayon Linux
3. PC-BSd
4. Knoppix

perhaps or just a triple boot....

1. Dreamlinux
2. Sabayon Linux
3. PC-BSD


I like Dreamlinux and Sabayon the best but I would like to be able to run PC-BSD at a whim if I so choose.

---

### Post by rattlerviper on 2006-08-06
Once you check out PCLinuxOS it might be a 5 os boot!

---

### Post by richbarna on 2006-08-06
> **rattlerviper said:**
> Once you check out PCLinuxOS it might be a 5 os boot!

Make that a 2 OS boot, PClinuxOS and Ubuntu :mrgreen:

---

### Post by peabody on 2006-08-07
I responded to your other thread with something similar to the effect of, ya'know, running all of these OS's via virtualization in something like VMware sounds like less of a headache.

---

### Post by RAV TUX on 2006-08-07
nice suggestion but honestly not interested,....the primary problem I had was with my boot loader and thus my RAID software incompatibility  with Linux.

but thanks for the advice.

---

### Post by rattlerviper on 2006-08-07
Running a OS under VMware...Wouldn't that make testing it a moot point?  Wouldn't all your hardware work all the time? Don't know much about VMware, but it seems I heard that somewhere on the forums.

---

### Post by RAV TUX on 2006-08-07
> **rattlerviper said:**
> Running a OS under VMware...Wouldn't that make testing it a moot point? Wouldn't all your hardware work all the time? Don't know much about VMware, but it seems I heard that somewhere on the forums.

exactely...how can you test an install with VMware?

---

### Post by peabody on 2006-08-07
It seems I may have misunderstood what you were after in installing all of these Linux distributions...

I was under the impression that you were trying out all of these linux distros to see what they were like out of the box, not to test their hardware compatibility.  If it was to test the hardware compatibility of the distros out of the box it seems like it might have been more fruitful to install one at a time.

You do go through the installation process as part of setting up the virtual machine.  If you're just testing hardware, if it works in the host Linux distro it theoretically can be made to work in any another.

If you were after something else, my apologies.

---

### Post by RAV TUX on 2006-08-07
> **peabody said:**
> It seems I may have misunderstood what you were after in installing all of these Linux distributions...

I was under the impression that you were trying out all of these linux distros to see what they were like out of the box, not to test their hardware compatibility. If it was to test the hardware compatibility of the distros out of the box it seems like it might have been more fruitful to install one at a time.

You do go through the installation process as part of setting up the virtual machine. If you're just testing hardware, if it works in the host Linux distro it theoretically can be made to work in any another.

If you were after something else, my apologies.

No problem Peabody and Thanks again for the advice and input it is greatly appreciated.;)

---

