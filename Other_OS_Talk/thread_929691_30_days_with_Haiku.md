---
title: "30 days with Haiku"
date: 2008-09-25
forum: Other OS Talk
---

### Post by Sealbhach on 2008-09-25
An intriguing look at Haiku, which is a resurrected form of BeOS.

[http://www.techradar.com/news/software/operating-systems/beos-reborn-30-days-with-haiku-465275](http://www.techradar.com/news/software/operating-systems/beos-reborn-30-days-with-haiku-465275)

I got the disk with Linux Format magazine so might give it a spin on a virtual machine.


.

---

### Post by Sorivenul on 2008-09-25
Great link!  I've tried it in VMs many times and love it.  I have never had a successful HD install, despite my best efforts.  It may be time to try again, soon.

---

### Post by cardinals_fan on 2008-09-25
I love Haiku, but hardware support is definitely not there yet.

---

### Post by pelle.k on 2008-09-26
I just compiled and installed the new revision, but unlike the previous revision i tested, this wouldn't succesfully boot up on my notebook. :(
I guess i will try again in a week or so...

---

### Post by Thelasko on 2008-09-26
I tried Haiku about 6 months ago.  At that time there were some VMs on the BeBits site that included Firefox and other pieces of software.  It was much easier than starting off with no browser and having to navigate the command line to get one.

The major problem was that those VMs were extremely large, and they didn't have enough extra space on the drive to do anything useful.

---

### Post by pelle.k on 2008-11-16
Hey guys. Lookie here. (attached screenie).
Mind you, this is a santa rosa laptop, sata hd controller, intel hd sound, gigabit network, a geforce 8600M GS, and 1680x1050 lcd.
I had to install the OSS sound port from haikuware, but as you can see from the screenshot, i got it working. And, i had to do nothing else than install it. No tinkering.

---

### Post by cardinals_fan on 2008-11-16
> **pelle.k said:**
> Hey guys. Lookie here. (attached screenie).
Mind you, this is a santa rosa laptop, sata hd controller, intel hd sound, gigabit network, a geforce 8600M GS, and 1680x1050 lcd.
I had to install the OSS sound port from haikuware, but as you can see from the screenshot, i got it working. And, i had to do nothing else than install it. No tinkering.
Very impressive.

---

### Post by pelle.k on 2008-11-16
Even though i'm probably lucky to have everything working this good, to me, it still is a good indication of the quality of this project.
Need i tell you this thing boots in like 5-10 seconds?
Either way, they still have much to do. Like add tons of hardware support, release R1, and plan *new* features for R2 (since R1 was pretty much aimed at binary compability with BEOS R5, and not to add new features).
And yeah, it's not even multiuser as of yet (well, there might be support for it, but it's not visible from what i can see). heh. But, on the bright side, that has the advantage of starting with a clean slate, and implement a modern solution instead.

---

### Post by handy on 2008-11-17
Another milestone in my book.

I too look forward to being able to run Haiku, & being able to use the reimplementation of the Be File System (BFS), which from a google video I saw once looks to be remarkable:

***_[http://video.google.com/videoplay?docid=236331448076587879](http://video.google.com/videoplay?docid=236331448076587879)_***

---

### Post by Sorivenul on 2008-11-17
Sucked it up.  Spent some time on it today after reading the new post, got it working on a testing box.  Works fine, and works just as well in QEMU on my main box.

---

### Post by zmjjmz on 2008-11-17
Would anyone give this OS a minimum hardware requirement spec? I'm seriously considering running it on some old computers, because I guess support for them might be there by now.

---

### Post by Sorivenul on 2008-11-17
> **zmjjmz said:**
> Would anyone give this OS a minimum hardware requirement spec? I'm seriously considering running it on some old computers, because I guess support for them might be there by now.

Estimated 64MB RAM (my QEMU Haiku crashes with less than 64MB), estimated 100MB HD space.  Not too bad.

---

### Post by zmjjmz on 2008-11-17
> **Sorivenul said:**
> Estimated 64MB RAM (my QEMU Haiku crashes with less than 64MB), estimated 100MB HD space.  Not too bad.

Too bad for me actually. Oh well.

---

### Post by Sorivenul on 2008-11-17
> **zmjjmz said:**
> Too bad for me actually. Oh well.

If that's too much, I believe Syllable only requires 32MB RAM to run, and AROS only requires 24MB.  Remember both of these are also in development, but from my tests I never had them fry my HD.

---

### Post by zmjjmz on 2008-11-17
I've tried Syllable, and 32MB definitely is a bit little.
I haven't tried AROS though. Maybe I might, if there's a large amount of software available.

---

### Post by Sorivenul on 2008-11-17
> **zmjjmz said:**
> I've tried Syllable, and 32MB definitely is a bit little.
I haven't tried AROS though. Maybe I might, if there's a large amount of software available.

AROS is binary compatible with Amiga software if it is installed on an Amiga, and is source-level compatible when installed outside an Amiga.  There is a good ammount of software already available on AROS, and if you have an Amiga or a way to get one it should be able to run almost anything you can find for it.  May be worth a try anyway.

Just out of curiosity, what type of machines are you planning/trying to install on?

---

### Post by zmjjmz on 2008-11-17
> **Sorivenul said:**
> AROS is binary compatible with Amiga software if it is installed on an Amiga, and is source-level compatible when installed outside an Amiga.  There is a good ammount of software already available on AROS, and if you have an Amiga or a way to get one it should be able to run almost anything you can find for it.  May be worth a try anyway.

Just out of curiosity, what type of machines are you planning/trying to install on?

Old x86 machines, namely one Pentium II (Packard Bell) and one generic 586.
I'll be glad to compile all the software, but unfortunately a lot of the cool Amiga software is proprietary.

EDIT: No web browser? :( 
That might be a deal breaker, but then again the computers I'm looking to use it with don't exactly have any form of ethernet (not that I can't just put a card in though. If I like AROS enough I might just to do IRC or something)

EDIT2: I found [AWeb](http://aweb.sunsite.dk). Anyone know anything about it?

---

### Post by MethodOne on 2008-11-23
Here's my experience so far with Haiku:

I installed a daily Haiku raw image on real hardware (Intel D845PT motherboard)  by following the instructions at [http://www.haikuware.com/components/com_mambowiki/index.php/Install_Haiku_Beside_Windows](http://www.haikuware.com/components/com_mambowiki/index.php/Install_Haiku_Beside_Windows) (I am dual-booting Haiku with Windows XP on a drive on a mobile rack), but I had to boot into safe graphics mode because my GeForce FX5200 card caused the screen to blank out.  Before that I had to download and burn a BeOS Max CD to install the bootloader with the makebootable command on my mounted Haiku partition, but I had to disable my onboard sound because the BeOS CD would crash if it were enabled.  I also had to increase the mouse speed in the options.  I tried building a Haiku live CD from source (on my Ubuntu Hardy installation on a different drive) so I don't have to deal with BeOS if I install Haiku on newer hardware than mine, but [the system reboots immediately after booting the CD I made]("http://dev.haiku-os.org/ticket/2491").  I also tried a distribution of Haiku called Senryu, found on [http://www.haikuware.com](http://www.haikuware.com), which contains more drivers and applications.  That one worked much better.

---

### Post by pelle.k on 2008-11-23
Oh, I always build haiku from this guide;
[http://www.haiku-os.org/documents/dev/building_haiku_on_ubuntu_linux_step_by_step](http://www.haiku-os.org/documents/dev/building_haiku_on_ubuntu_linux_step_by_step)

Then i follow a few steps from this guide to have it install directly to a partition instead of an image file. Easy as pie!
[http://www.haiku-os.org/community/forum/installing_haiku_to_a_partition_from_linux](http://www.haiku-os.org/community/forum/installing_haiku_to_a_partition_from_linux)

---

### Post by MethodOne on 2008-11-23
I would love to build it on GNU/Linux, but my hard drive with Ubuntu Hardy is only 15GB.

Edit:  I can just reinstall Ubuntu and make a 2GB partition dedicated to Haiku.  I don't plan on using Haiku as my main OS anytime soon because it's still in development.

---

### Post by pelle.k on 2008-11-23
Don't reinstall ubuntu, resize a partition instead. I have a 1 gigabyte partition for haiku, but even that is overkill if you're just trying it out. The image is just a few hundred megabytes.

---

### Post by MethodOne on 2008-11-23
I just reinstalled because I wanted to dedicate the drive to testing Haiku.

---

### Post by free10 on 2008-12-06
I am wanting Haiku so bad I can taste it. I built my first computer 1998 coming off Webtv. I loaded 5 different versions of Linux and the all seem to destroy my BeOS 5.0 Pro I had bought and vice versa. So I could only get one to work on my new computer since I did not know how to get dual boot and BeOS won that choice hands down.

I used BeOS until about 3 years ago when I installed Ubuntu on a second drive in 2005 to get my new Nikon D70 and its raw files to work right right. Firefox flash movies didn't work with BeOS but it did for Ubuntu. My Jabber messenger in BeOS I used was dying out as the  Jabber servers changed to new Java software.

I liked Ubuntu but it is way slower even then, but looks nice and not that hard to use and has better in some ways software apps, and newer software. Overall experience pretty cool.

Around March of 2008 I order new guts for my computer updating from a one gig celeron to a quad Intel CPU, plus 4 gigs of memory and new Samsung terabyte drive. I knew BeOS would not boot anymore with this hardware change but it was time to make a big leap in hardware and I had the spare cash. I also thought it would give Ubuntu a speed boost especially with graphics software and it did, but I also was keeping BeOS/Haiku in mind and knowing it soon should be out and it should be able to run on my newer hardware as a bootable R1 and then off to the moon on abilities quickly with pure speed.

I have resisted building or using Haiku so far as I wait for R1 to come out and it should be soon I think. I for one can not wait hardly and feel like a kid in the candy store just waiting for it. It will have chat, and it will be able to deal with my camera and its large files and its raw ones, if not off the bat on raw I am sure someone will quickly port over UFRAW and DCRAW, and I think the flash movie problem is partially fixed using VLC now. 

Hey Intel has 8 core cpus coming:wink::wink::biggrin:--Dwight

---

