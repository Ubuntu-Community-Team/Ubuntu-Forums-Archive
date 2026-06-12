---
title: "Noob question. 12.04 alongside Xp Ok?"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by NotSure23 on 2012-09-27
Hey guys,

Well i got an older HP laptop(1.60Ghz single core, 512mb ram) w/ a fresh  install of xp on it. As far as i can tell it only has a single  partition. Under my computer it only lists 1 drive, C: w/ 16.4GB used  out of 80gb.

I already have the ISO burn to a disk and it works fine w/ the "try ubuntu" feature.

When i dual boot on this i would select "Install alongside XP" correct? (confused w/ the something else selection) 

Is there anything else i need to do prior to install?

Thank you

[[IMG]http://imageshack.us/a/img3/5862/partitionw.jpg[/IMG]]("http://imageshack.us/photo/my-images/3/partitionw.jpg/")

---

### Post by Epodx64 on 2012-09-27
Yeah you would click "install alongside xp" then you have to decided how much space it'd recommend a minimum of 10gb but 25-30gb would probably be optimal

---

### Post by jerrrys on 2012-09-27
> **Epodx64 said:**
> Yeah you would click "install alongside xp" then you have to decided how much space it'd recommend a minimum of 10gb but 25-30gb would probably be optimal

Yep, that works.  If you find ubuntu a little too heavy for that machine, give xubuntu a try.

---

### Post by papibe on 2012-09-27
Hi NotSure23.

Unlike Windows Vista and Windows 7, XP does not have partition tools (installed by default). If you are committed to change the partitions on Windows, you would have to use a 3rd party tool like Norton Partition Magic.

On the other hand, you can do it using 'gparted' available on the Ubuntu Live CD.

In that case, please take this precaution steps before attempting it (in XP):
[LIST]
[*]Backup your files.
[*]Do a system clean (remove temps files)
[*]Defrag your disk at least a couple of times.
[/LIST]Hope that helps, and let us know how it goes.
Regards.

---

### Post by newb85 on 2012-09-27
Yes, the option to automatically install alongside Windows should work fine.  The "Something Else" option would give you some more advanced options, like setting up extra partitions for certain parts of your Ubuntu system, but for what you want, none of that is really necessary.

And as jerrys pointed out, the specs you gave are rock-bottom for Ubuntu.  If I were you, I'd create a Live CD of Xubuntu and test it out, as well, before installing one or the other.

Lubuntu is even more lightweight than Xubuntu, but you probably won't need to go that far (although for the price of a CD and a little time, you could test it out, too).

Both Xubuntu and Lubuntu are official derivitaves of Ubuntu.  They're the same base (under-the-hood) system with different Desktop Environments and default Applications installed.  In any one of them, the DEs and Applications of the others can be installed and used.

---

### Post by NotSure23 on 2012-09-27
Ok great. I plan on upgrading the ram since it supports up to 2gb. This laptop is just for fun and isn't my main comp, i just want to learn Ubuntu.

---

### Post by newb85 on 2012-09-27
> **NotSure23 said:**
> Ok great. I plan on upgrading the ram since it supports up to 2gb. This laptop is just for fun and isn't my main comp, i just want to learn Ubuntu.

Great!  Have fun.  The ram should help.  I'm not sure that single-core will be up to snuff, but if you're doing this for fun, what do you have to lose?

---

### Post by NotSure23 on 2012-09-27
Ok, well you were right its too old i guess. I restarted and the message came up saying "unable to boot use kernel that will work w/ CPU"

So I also have a my fiance old HP vista laptop AMD dual core w/ 3gb of ram, (she a OSX user now) that was the original comp that i tested 12.04 on to make sure i burnt it correctly. I was just going to try Ubuntu on the oldest laptop first.

This one does have two partitions HP recovery 9.99gb (D) and (C) 222.9 total w/ 100gb used.

Would all of the above still apply? 

Put disk in and click "Install alongside Vista" and then just use the slider to give Ubuntu 30gb?

---

### Post by jerrrys on 2012-09-27
With "Vista" I suggest that you create a partition with a windows partitioner.  Vista has been known to get screwed up when using gparted (the linux partitioner).

---

### Post by NotSure23 on 2012-09-27
ok so follow this, i would shrink the C drive and where it says "enter amount of space to shrink" i would enter 30000 for roughly 30gb.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

Now i would have a separate partition for Ubuntu correct?

---

### Post by oldfred on 2012-09-27
Just do not create partitions with Windows. Windows cannot create Linux partitions and may convert to dynamic partitions which is proprietary to Windows and does not work with Linux.

Use gparted to partition in advance or use the installer which works like gparted. If installing to free space and you want just the default of / (root) and swap you can just install the unallocated free space.

---

### Post by pyrokinetic on 2012-09-27
> **NotSure23 said:**
> ok so follow this, i would shrink the C drive and where it says "enter amount of space to shrink" i would enter 30000 for roughly 30gb.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

Now i would have a separate partition for Ubuntu correct?

Yup. :) Should pop up as 'unallocated space' 

But I'd also back up any important data you have.

EDIT - oldfred is right, definitely be careful because it can be changed to dynamic disk and you could be facing some issues.

---

### Post by NotSure23 on 2012-09-28
I figured it might be a pain w/ vista, like i was saying its just for fun and i mainly use a laptop during the summer so its not a huge deal i just want to play w/ linux. I'll probably look into Xbuntu like suggested and report back tomorrow. Thanks for the help

---

### Post by NotSure23 on 2012-09-28
Ok so i downloaded Xubuntu 32bit and used InfaRecorder to burn the ISO. After its done i restarted the Vista laptop and it boots from DVD no problem and "try Xubuntu" works great. 

Switch over and put it in the HP DV1000 XP laptop and it seem like its trying to boot from the DVD but then after 30 second it switches and boot from HDD. 

I checked the Bios in the XP laptop and it optical drive boots before harddrive.

Any Advice?

---

### Post by oldfred on 2012-09-28
Possibilities:
CD drive may not work, can you read files from CD/DVD on system. Some older system just do not read from CDs written by another. Did you try CD not DVD? That also could be an issue.

How old is computer? New versions use PAE but Lubuntu and Xubuntu will ship with non-pae so it should work even if very old.

What video card/chip does it have? Do you get initial screen with little icons at bottom. If so press any key, then f6 and choose nomodeset.

---

### Post by mips on 2012-09-28
Try creating the image on a usb stick and booting of that, in windows you can use Unetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by NotSure23 on 2012-09-29
Yea i burnt it on a DVD and it has a DVD-RW drive. I can try a CD and see if that works if not ill try the USB drive. 

It has an 1.60ghz Intel Pentium M, 512mb of ram, Graphics are intel 855 GME

Its like this one probably 1 step down
[http://www.notebookreview.com/default.asp?newsID=2546](http://www.notebookreview.com/default.asp?newsID=2546)

---

### Post by NotSure23 on 2012-09-29
when i booted w/ the vista laptop i got the two icons at the bottom and then shortly after the Xubuntu screen appeared. With the XP laptop it will just show a black screen w/ the white blinking cursor at the top left. I can hear the DVD drive spinning up but it never booted.

---

### Post by oldfred on 2012-09-29
Depending on how old computer is, you may have chip without PAE extensions. All new versions of Ubuntu use PAE as standard for the 32bit version. 

[http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae

How To Install Ubuntu 12.04 On Non-PAE Capable Hardware.
[http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html#more](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html#more)

---

### Post by NotSure23 on 2012-09-29
Well burnt it to a cd and it booted fine. Played around w/ the Try Xubuntu for a while then went to install it. Half way through the install it got an error which stopped the install.

I was able to shut down and restart into windows, i might of screwed it up but it left the partition on the drive so i right clicked it and deleted it. 

Now im left w/ this. Should i Reinstall XP before i try this again?

[[IMG]http://imageshack.us/a/img35/2765/1111om.jpg[/IMG]]("http://imageshack.us/photo/my-images/35/1111om.jpg/")

---

### Post by Guilden_NL on 2012-09-29
> **NotSure23 said:**
> Ok, well you were right its too old i guess. I restarted and the message came up saying "unable to boot use kernel that will work w/ CPU"

That doesn't make sense.  I am running 12.04 on a 2004 Toshiba laptop/Intel Pentium M 725 / 1.6 GHz and a 2006 Dell laptop/Intel Pentium M 755 / 1.73 GHz.  And am posting this on the old Dell.

---

### Post by NotSure23 on 2012-09-29
Seemed to work better w/ CD's rather then DVD.

---

### Post by NotSure23 on 2012-09-29
Ok so I'm up and running on Xubuntu.

I tried Ubuntu again but burnt it to a CD this time rather then a DVD. It started to boot and the two icons at the bottom came up. I made the F6 menu come up and selected "nomodeset" but i still got the "use kernal that works w/ CPU." 

So i burnt Xubuntu again using Infra recorder, but i turned down the write speed from maximum to 16x. Then installed by selecting "erase disk and install ubuntu" and now its running good.

Thanks for the help

---

### Post by Hakunka-Matata on 2012-09-29
That's great.  Thanks for detailing what you did to make things work.  Enjoy Ubuntu, it's a killer OS.

---

### Post by mips on 2012-09-30
> **NotSure23 said:**
> I made the F6 menu come up and selected "nomodeset" but i still got the **"use kernal that works w/ CPU."** 


What's the full name of the image file you do downloaded? 
You might have downloaded the 64-bit version by mistake.

Secondly you might have an older "Banias" based Pentium M cpu that does not have PAE support. Only Lubuntu & Xubuntu comes with non-PAE kernels to support older hardware.

Copy&paste the following two commands to a terminal and post the output here,

```
lscpu
```

&

```
grep --color=always -i PAE /proc/cpuinfo
```

---

### Post by NotSure23 on 2012-10-02
Yea it was definitely the 32-bit version that i downloaded for Xubuntu and Ubuntu. The CPU is 1600mhz not 600mhz from what its stating below.

Second code didnt work

HP-Pavilion-dv1000-PR425UA-ABA:~$ lscpu
Architecture:          i686
CPU op-mode(s):        32-bit
Byte Order:            Little Endian
CPU(s):                1
On-line CPU(s) list:   0
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 13
Stepping:              6
CPU MHz:               600.000
BogoMIPS:              1196.89

---

### Post by mips on 2012-10-02
And the second command?

Anyway that's a Dothan based CPU and from the bit I've google the ones with a 400MHz FSB don't support PAE. 

If you don't get any output in the above command in red saying pae then your cpu does not have pae support and you won't be able to use the Ubuntu LiveCD.

 Only way to install it is to 1) Use the minimal/netinstall cd or 2) Use a ubuntu sping like lubuntu or xubuntu which comes with none pae kernels and install that and afterwards add the ubuntu-desktop or whatever it's called package.

---

### Post by NotSure23 on 2012-10-02
Yea the second command didn't work. 

Xubuntu's live cd along w/ the full install worked perfect, i just got errors the first time from the cd being burnt at too high of a write speed. This was when i was attempting the dual boot and these messages popped up during install.

After that i just burnt xubuntu again at 16x write speed and did a full install. Its been working great since.

---

