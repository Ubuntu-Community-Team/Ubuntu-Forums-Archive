---
title: "Is it possible to use a flash drive as a hard drive to install ubuntu?"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by trolol on 2012-02-01
What title says. 

I have a netbook lying around with a corrupt hard drive, fixing it costs way too much and Im not gonna pay for it. I also have a 4gb flash stick, so i was wondering is it possible to install any version of ubuntu but use the flash stick as my hdd?

if so, how, and which version is small enough? 

i know that im gonna have like no memory but idc coz ill just be on the web the whole time, anything else i will go on my computer.

any help would be great ty

---

### Post by Rodney9 on 2012-02-01
HOW TO Install Lubuntu on USB Drive

[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

Rodney

---

### Post by Paqman on 2012-02-01
Any USB stick 4GB and up will do (>8GB would be better), just make sure you install Grub onto the stick instead of your hard drive. Just boot Ubuntu off a USB stick, run the installer like normal and choose your fresh USB stick as the drive to install to.

---

### Post by trolol on 2012-02-01
> **Rodney9 said:**
> HOW TO Install Lubuntu on USB Drive

[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

Rodney

It says I need to use the live CD too... my netbook doesnt support CD's is there any way to do it without it?

Or did I not understand it correctly?

---

### Post by Paqman on 2012-02-01
> **trolol said:**
> It says I need to use the live CD too... my netbook doesnt support CD's is there any way to do it without it?

Or did I not understand it correctly?

You can put the ISO you download onto a USB stick instead of a CD. Go to:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
...and click on the instructions for "I would like to create a > USB stick" for your current operating system. You can either use this stick to run a live system, or you can use it install Ubuntu onto a second stick.

---

### Post by trolol on 2012-02-01
> **Paqman said:**
> You can put the ISO you download onto a USB stick instead of a CD. Go to:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
...and click on the instructions for "I would like to create a > USB stick" for your current operating system. You can either use this stick to run a live system, or you can use it install Ubuntu onto a second stick.

Ohh two sticks! Of course! Thanks

Also just another question how much memory will I have remaining if i do this?

---

### Post by Dennis N on 2012-02-01
> **trolol said:**
> Ohh two sticks! Of course! Thanks

Also just another question how much memory will I have remaining if i do this?

An example: Lubuntu 11.10 installed on an 8 gb flash drive, after installing additional software and some music: 3.5 gb used out of 6.5 gb available. I think after install it was around 2 gb used, maybe a bit less.

Don't expect speed. Runs slow. Lots of waiting. Don't expect a lot of portability. It's configured for the machine it was installed on. For that, you need a live USB with persistence.

---

### Post by lkraemer on 2012-02-01
You can also try Lupu-528.ISO, Puppy Linux, Slitaz 3.0, or Tiny Core 4.2
as they are much smaller and require less Memory.

UNetbootin will allow you to take any ISO and create a Bootable USB Drive.

REF's:
[http://distrowatch.com](http://distrowatch.com)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

lk

---

### Post by Dennis N on 2012-02-01
Give it a try. Consider it an experiment, and you may be happy with the result. You never know unless you try it out. 

I also found that installing to an external USB hard drive gives much better performance, not too much different than the internal hard drive. 

Good Luck!

---

### Post by Kixtosh on 2012-02-01
If you do use Puppy, you'll experience almost normal performance. Since Puppy loads entirely into RAM, and is designed to run normally from RAM (it is not designed to be installed on a normal hard drive, ever, although it can be done). It's more or less as fast running from a CD or USB flash drive as any normal distro that would be running directly from a hard drive for normal use. Some would claim faster, but I haven't really noticed that to be the case. The only things that I have found to be considerably slower are boot times and shut down (particularly shut down, since it has to save everything from the session to a small save file on the USB drive every time).

Puppy is fully portable, so you can take your whole operating system with you to any other machine. Puppy starts right after BIOS, so it won't interfere with any "host" machine in any way. The hard drive won't be mounted, in fact, unless you intentionally do so. One thing to be aware if you intend to use it as a portable system, however, is that sometimes you may run into nasty wireless cards that don't want to work "out of the box" so you may want to consider purchasing a USB wireless adapter to circumvent that (but only if you intend to use it as a fully portable O.S., with your saved documents in a small compressed file).

Puppy should be very happy on a 4 GB drive. I installed Puppy 5.3.1 on an 8 GB flash drive recently, and it used 1.1 GB. Other installations will be a lot less happy, since I think that you are going to require almost 3 GB just to get the O.S. on the flash drive in the first place (my minimal hard drive installation took up that much space), and you still need room for Swap. 5 GB seems like an absolute minimum for that to be possible, even if you're only leaving 1 GB to take care of cache for browsing and downloads. If swap is too small, you may experience strange behavior (I did, I'll admit it!).

---

### Post by underquark on 2012-02-01
I'd vote for Puppy, too. Currently running Puppy Lupu 5.2.8 installed onto a 1GB SSD and with 1GB RAM in a HP T5730 (ex "thin client"). Have added Firefox, Flash, VLC, Filezilla and a couple other small programs and still have about 50MB left on the "disk". I have this machine plugged into my TV to surf, e-mail, stream video from network.

For portability, Puppy also gets my vote. Even on a 1GB stick it'll work but best get a larger capacity one if you want to store anything.

I did manage to get a home-rolled version of ubuntu with LDXE desktop environment onto a 2GB SSD on another HP machine using a 4GB USB stick for some of the directories but Puppy is just way easier to use out of the box.

---

### Post by Weirdy on 2012-02-01
I'd definitely recommend puppy linux (or something with the run from ram feature) as flash memory only has a fixed number of reads and writes; its normally a big number but if you don't keep track of how often the OS writes to the drive (especially when swapping) you may start to find the drive's life starts to shorten :/

---

