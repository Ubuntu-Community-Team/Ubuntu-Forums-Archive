---
title: "Ubuntu on USB Flash"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Ginoxy on 2008-07-23
Okay i just bought a 4G flash USB to install linux ubuntu but for some reason something happened and the 4G drops to 65MB !!! how to get the 4G back ? is there anyway ?

---

### Post by LowSky on 2008-07-23
what brand flash drive?

did you format the drive yet?

[http://lifehacker.com/software/ubuntu/how-to-install-ubuntu-linux-on-a-flash-drive-245087.php](http://lifehacker.com/software/ubuntu/how-to-install-ubuntu-linux-on-a-flash-drive-245087.php)

---

### Post by Ginoxy on 2008-07-23
ts imation and i did not format it ! how to format it ?

---

### Post by WRDN on 2008-07-23
In Windows, right click on the drive and click Format.
In Ubuntu, I would recommend using GParted (its in the repositories) to format it. The easiest way is to delete the partition already there, create a new one that fills the entire space, then finally, right click on the drive and select "Check" to check the filesystem (I had to do this, otherwise it wouldn't recognise the drive).

---

### Post by Ginoxy on 2008-07-23
i downloaded gparted but i can not find it ?!

---

### Post by Ginoxy on 2008-07-23
[ATTACH]78706[/ATTACH]

ok here is my flash usb what to do now ? how to get the full space now ?

---

### Post by Ginoxy on 2008-07-23
I tried to delete everything and i got 3.7g unallocated ! 
is that right ?

---

### Post by Ginoxy on 2008-07-23
Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         487     3911796    b  W95 FAT32


this is what i got now !!! 

why the end is 487 ?

---

### Post by LowSky on 2008-07-23
> **Ginoxy said:**
> I tried to delete everything and i got 3.7g unallocated ! 
is that right ?

Yes that is correct. Memory companies are horrible about actual memory sizes. For some reason they like to think that in 1000's when the measurement should be 1024. Also drives are approximate and will have descrepences between drives.

Can you post a picture of what gparted is showing you now

---

### Post by Ginoxy on 2008-07-23
here is the picture 

[ATTACH]78718[/ATTACH]

---

### Post by Ginoxy on 2008-07-23
Hello, 

still getting the same message ! 

////

Device Boot Start End Blocks Id System
/dev/sdc1 1 487 3911796 b W95 FAT32

////

---

### Post by Ginoxy on 2008-07-24
anyone can help?

---

### Post by rossmoore on 2008-07-24
I'm not sure I understand the problem - you now seem to have a formatted 4Gb USB stick, formatted in FAT32. You plug it in and see 3.7Gb of space, as expected, and I presume you can now read and write to it. Of course, because it's formatted as FAT32 you'll be limited to no files greater than 2Gb, but apart from that you're sorted, no?

---

### Post by Ginoxy on 2008-07-24
Well in very simple way i wanted to install ubuntu to my usb flash drive as this site shows 

[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/)

now the problem is when i go to this step 

# type n to make a new partition

to make a new partition i need to choose like 2GB+ as recomennded but for some reason i got this 

Partition number (1-4): 1
First cylinder (1-487, default 1): 

see this is the problem i can not choose greater than 487 !!

---

### Post by muteXe on 2008-07-24
I don't think the 487 is *directly* related to your 2Gb+ request...

---

### Post by Ginoxy on 2008-07-24
What do you mean ?

---

### Post by Ginoxy on 2008-07-24
Guys any help !!

---

### Post by Ginoxy on 2008-07-24
i have been looking for help throughout many channels but nobody knows about this ! anyway thanks a lot.

---

### Post by Ginoxy on 2008-07-25
i just formated the whole usb on windows xp and i got the whole usb memory 4GB but in FAT is that right ? 

now i switch to ubuntu again and i got the same problem and error as below

---

### Post by duckfeet on 2008-07-25
I also booted mine from a 2 gig USB Flash, but I  downloaded 'netbootin' app, , and it worked fine, (w/2gigs), just following the instructions on here...I just picked up a 2gig flash at Radio Shack, downloaded the first 8.04 .iso file I found on the install site link here, and have put 8.04 on two computers without incident...most USB's are formatted correctly w/fat16 to begin with...maybe if you refrased your question, one of the tech savvy guys could help you...I know how frustrating it can be: I download and copied *three* cd's and just about gave up, and then did the USB trick, and it worked...I'm re-reading yer post now, see if it's anything I know...

O.K. I re-read, and 1st, I would have said not to reformat, as most usb flashes are already formated correctly fat16 fine for this...but anyway, I'd go ahead and download yer isofile, and then download whatever bootloader u choose to use, and give it a shot: worked fine for me...

Best wishes...

---

### Post by Ginoxy on 2008-07-25
duckfeet thanks for replying, but my problem is with the formatting issue i got the same error i can not copy all ubuntu files into the usb ! i dont know why ?

---

### Post by duckfeet on 2008-07-25
Look on the bright side: at least I'm keeping your thread alive until somebody who really *does* know what they're doing, comes along...

Anway, I reread your post, and went to the site you are using, and that is why I recommended what I used, which is netbootin, because with this little ap, I didn't *need* to punch in all the command line stuff: all I had to do was put in where it was going, basically, to the USB drive, and it did the rest, and worked fine, and if that site isn't working, "netbootin" is a little app, that works just fine...that's why I suggested it...

---

### Post by Ginoxy on 2008-07-25
okay so you suggested to download netbootin and the .iso file to the usb and thats all ?

---

### Post by duckfeet on 2008-07-25
It worked really good: I didn't expect it to, either, as I'd had bad luck w/cd's...but anyway, I followed the ubuntu mirror guy's instructions, which was to first download an .ISO file to my HD--Ubuntu 8.04-- then I downloaded 'netbootin' to my USB, then opened it, and it has a little menu, w/USB on the bottom, and I needed to type in what drive and file I was using, and it did the rest,u know, transferring Ubuntu over to USB, and then I rebooted, just like it said, and I got that amazingly *happy* feeling, people like me get, to *finally*--around 4 in the morning--see the Ubuntu logo pop up, rather than one more grub menu....

Anyway, I just went to the site, and it worked...see what u think: the site seemed to encourage the mirror unbuntu, but I didn't like it, and I'm glad I stuck to the normal UB...

> **Ginoxy said:**
> okay so you suggested to download netbootin and the .iso file to the usb and thats all ?

---

### Post by Ginoxy on 2008-07-25
Well, now i need to know from where i need to download netbootin ? and do i have to be on windows or i can work from ubuntu ?

---

### Post by kpkeerthi on 2008-07-25
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by duckfeet on 2008-07-25
> **Ginoxy said:**
> Well, now i need to know from where i need to download netbootin ? and do i have to be on windows or i can work from ubuntu ?


Good question: I'm trying to remember: it was real late, and I was going between one XP box, and a Ubuntu setup, to install this on a third...I think I got it on Windows, yep, but I use Opera browser on all of them, so I'm guessing it would work: I'm not sure tho, u might have to check: here is the site that I think I started from, when I was in the same boat, on here yesterday night, trying to find out what to do:

*whoops!!!* guy beat me to it hahaha...good job!

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by muteXe on 2008-07-25
> **Ginoxy said:**
> Well in very simple way i wanted to install ubuntu to my usb flash drive as this site shows 

[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/)

now the problem is when i go to this step 

# type n to make a new partition

to make a new partition i need to choose like 2GB+ as recomennded but for some reason i got this 

Partition number (1-4): 1
First cylinder (1-487, default 1): 

see this is the problem i can not choose greater than 487 !!


Have you tried allocating 2Gb+ at this stage?  Just to see what happens?  If that "487" value is something to do with cylinders then I dont think it has anything to do with memory.

[http://www.storagereview.com/guide2000/ref/hdd/geom/tracksDifference.html](http://www.storagereview.com/guide2000/ref/hdd/geom/tracksDifference.html)

---

### Post by duckfeet on 2008-07-25
Another thing: don't get bogged down in all the stuff that is for earlier editions of netbootin: here is their webpage, and I used it, and the above, and I didn't neet to write in anything: the unetbootin app did it all: all I had to do was type in where it was going, making sure I put the previously downloaded file, from the desktop of my HD, to my USB drive, as the little GUI did all the rest...I read the stuff about the *manual* installation, and didn't realize I didn't need to do all that: that is what the unetbootin app does...hopefully by now u have already figured all this out...


[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Ginoxy on 2008-07-25
guys 


ITS WORKING 

THANKS A LOT :)

:guitar:

---

### Post by dark_harmonics on 2008-07-25
Hard to believe there is a 3 page thread on this. If you have a large enough drive you just point the installer at the USB drive and it works. I have it running on the USB stick in my pocket with this method.

---

### Post by duckfeet on 2008-07-26
My take on it, was that the instructions complicated the hell out of it, and made it seem like there were all sorts of stuff to figure out: I'm not the first guy to realize--kind of by accident--that once I loaded netbootin, NBdid all the rest...and I wander around w/my usb stick loaded w/8.04 around my neck too, which I'm always trying to stick in innocent windows ports

---

### Post by bluesalt on 2008-11-30
Hi, very useful information here for me :) Glad I found this thread. I've followed different instructions to install Ubuntu 8.10 onto my USB stick. I tried pendrivelinux's method of using the script to download the files but to no success for the past 2 days.
Then I tried unetbootin and got everything downloaded into my USB stick. However, I am stuck at the startup.

My PC (vista OS) starts up immediately with through the USB stick but I get the Unetbootin grey screen telling me that the system will start in 10secs. The message just keeps going on and on. What's happening?

Can I also get this same USB stick to start in Vista as well? Or have a choice in selecting the OS when the notebook boots up? I'm a beginner's beginner in Linux.

Thank you very much for any help.

---

