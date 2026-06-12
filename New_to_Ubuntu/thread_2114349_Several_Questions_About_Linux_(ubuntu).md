---
title: "Several Questions About Linux (ubuntu)"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by gregoryshock on 2013-02-09
I have a couple of questions about ubuntu linux. 

Number 1 when one is using ubuntu and it alerts you that a newer version is available and you can update your existing version to it. Should you? 

Number 2 is linux fast? I realize that this question may seem dumb but when I was using 11.10 on my desktop I couldn't tell any difference in speed verses the windows vista I also had installed. The Vista was a 32 bit and the Linux was a 64 bit. According to what I read or think I read the Linux at 64 bit should be faster. 

Number 3 I know you can make a live CD and a Live USB drive for Linux but is it possible to install Linux on an external hard drive or flash drive? My reason is, I don't have enough experimental computers (old computers) laying around that I can experiment on. I think virtual machines are cool, even though I haven't tried one. I think duel booting is cool, though in my limited experience I found it annoying since I couldn't get the grub to switch the boot sequence around. (I tried the terminal command line someone online gave me, and it didn't work. I also tried to look for the program that How To Geek suggested in one of their articles and I couldn't find one for my version of Linux) I just thought that maybe I could install it on either an external hard drive or big flash drive, it would be good way for me to learn it without taking as big of a risk at messing things up on my good computers. I know what it is like to uninstall Linux, if you do it right it isn't so bad but you got to do it just right or you will end up doing a full format and reinstall of windows which is what I ran into last time, since I hadn't taken the time to look up a how to guide. I thought "I did this once successfully I should be able to remember how to do it again. Nope!"

---

### Post by CK000 on 2013-02-09
1) I would recommend you  stick with LTS versions.

2) Yes, ubuntu linux is generally fast.

3) I am sure it is possible to install on an external hard drive, but you will have to ask some-one else exactly how to do it as I have yet to try this...

---

### Post by GameX2 on 2013-02-09
> **gregoryshock said:**
> I have a couple of questions about ubuntu linux. Number 1 when one is using ubuntu and it alerts you that a newer version is available and you can update your existing version to it. Should you?

If you "update" your installation, you might end up with bugs.  It's always better doing a compleat, clean install instead on an upgrade.
Also, an LTS version (Like Ubuntu 12.04) is maintained for 5 years, while a normal release (Like Ubuntu 12.10) is supported for 18 months.

> Number 2 is linux fast? I realize that this question may seem dumb but  when I was using 11.10 on my desktop I couldn't tell any difference in  speed verses the windows vista I also had installed. The Vista was a 32  bit and the Linux was a 64 bit. According to what I read or think I read  the Linux at 64 bit should be faster.

Yes, Linux in my case is really fast.  32-bit version would not detect more than 4GB of RAM on your machine, while 64-Bit will.

> Number 3 I know you can make a  live CD and a Live USB drive for Linux but is it possible to install  Linux on an external hard drive or flash drive? My reason is, I don't  have enough experimental computers (old computers) laying around that I  can experiment on. I think virtual machines are cool, even though I  haven't tried one. I think duel booting is cool, though in my limited  experience I found it annoying since I couldn't get the grub to switch  the boot sequence around. (I tried the terminal command line someone  online gave me, and it didn't work. I also tried to look for the program  that How To Geek suggested in one of their articles and I couldn't find  one for my version of Linux) I just thought that maybe I could install  it on either an external hard drive or big flash drive, it would be good  way for me to learn it without taking as big of a risk at messing  things up on my good computers. I know what it is like to uninstall  Linux, if you do it right it isn't so bad but you got to do it just  right or you will end up doing a full format and reinstall of windows  which is what I ran into last time, since I hadn't taken the time to  look up a how to guide. I thought "I did this once successfully I should  be able to remember how to do it again. Nope!"

You can make a Live-USB, or use a Flash drive and apply persistance (Use a USB drive of 4GB or more).  That way, Linux will run from your flash drive, and when you'll reboot, you'll keep your changes.
I'm used to the software "Linux Live USB Creator" on Windows to do this.  Of course, there are plenty of others tools availible (I know, I use a Linux Live USB creator on Windows.. Why not on Linux. XD).

---

### Post by gregoryshock on 2013-02-09
> **GameX2 said:**
> If you "update" your installation, you might end up with bugs.  It's always better doing a compleat, clean install instead on an upgrade.
Also, an LTS version (Like Ubuntu 12.04) is maintained for 5 years, while a normal release (Like Ubuntu 12.10) is supported for 18 months.



Yes, Linux in my case is really fast.  32-bit version would not detect more than 4GB of RAM on your machine, while 64-Bit will.



You can make a Live-USB, or use a Flash drive and apply persistance (Use a USB drive of 4GB or more).  That way, Linux will run from your flash drive, and when you'll reboot, you'll keep your changes.
I'm used to the software "Linux Live USB Creator" on Windows to do this.  Of course, there are plenty of others tools availible (I know, I use a Linux Live USB creator on Windows.. Why not on Linux. XD).


A guy on howtogeek wrote me an instruction on how to install it to an external hard drive.  Everything went fine until I had to start editing partitions.  I couldn't tell where things were going to go.  I gave it two tries and gave up.  I think it is possible that his menu and my menu may not be the same.  Here is the post I made there:  [http://www.howtogeek.com/forum/topic/several-questions-about-linux-ubuntu?replies=5](http://www.howtogeek.com/forum/topic/several-questions-about-linux-ubuntu?replies=5)

---

### Post by GameX2 on 2013-02-09
> **gregoryshock said:**
> A guy on howtogeek wrote me an instruction on how to install it to an external hard drive.  Everything went fine until I had to start editing partitions.  I couldn't tell where things were going to go.  I gave it two tries and gave up.  I think it is possible that his menu and my menu may not be the same.  Here is the post I made there:  [http://www.howtogeek.com/forum/topic/several-questions-about-linux-ubuntu?replies=5](http://www.howtogeek.com/forum/topic/several-questions-about-linux-ubuntu?replies=5)

I never partitionned a flash drive to install Ubuntu on it, neither I installed it directly from the Ubuntu CD.  Check this out:

[http://www.linuxliveusb.com/en](http://www.linuxliveusb.com/en)

The procedure is super easy, no need to partition.  It's quick.  You might want to give it a try (Since it's the first time you do this, backing up your drive might be a good idea, although I never had a single problem with this software).

---

### Post by gregoryshock on 2013-02-09
> **GameX2 said:**
> I never partitionned a flash drive to install Ubuntu on it, neither I installed it directly from the Ubuntu CD.  Check this out:

[http://www.linuxliveusb.com/en](http://www.linuxliveusb.com/en)

The procedure is super easy, no need to partition.  It's quick.  You might want to give it a try (Since it's the first time you do this, backing up your drive might be a good idea, although I never had a single problem with this software).

I downloaded that.  I installed it.  It seems that I was able to get a file from it to download onto my external hard drive.  ubuntu-12.04.1-desktop-i386  However I don't know what to do with that.  There is one thing I don't like about Linux.  When someone is trying to learn something it is nice to have a "basic" to learn from.  It seems that every time I ask someone a question about "how to" with linux I get different answers.  Because there are different ways of doing the same thing.  I find myself frustrated with asking the "why" why so many different ways of doing the same thing?  For what purpose?  I decided that I need to make a full linux system on an external hard drive.  I think this program is only meant to make a live drive.

---

### Post by gregoryshock on 2013-02-09
A guy on Howtogeek just gave me this option.  I was wondering what any of you think of it?  [http://www.sevenforums.com/tutorials/276540-portable-os-carry-your-os-external-drive.html](http://www.sevenforums.com/tutorials/276540-portable-os-carry-your-os-external-drive.html)

---

### Post by Zill on 2013-02-10
> **gregoryshock said:**
> ...There is one thing I don't like about Linux.  When someone is trying to learn something it is nice to have a "basic" to learn from.  It seems that every time I ask someone a question about "how to" with linux I get different answers.  Because there are different ways of doing the same thing.  I find myself frustrated with asking the "why" why so many different ways of doing the same thing?  For what purpose?...
Because Linux is not developed by a single mega-corporation!  Linux is developed by thousands of *individuals* who simply want to produce software *primarily* for their own benefit.  As there are always many different ways of doing things there are, inevitably, many different answers to the question "how do I do xxx?"

Regarding your point that "it is nice to have a "basic" to learn from", you have answered your question yourself with the following statement:
> **gregoryshock said:**
> ...I decided that I need to make a full linux system on an external hard drive...
A "basic" installation of Ubuntu is made to the local hard-drive.  You *chose* to change this basic installation to an external drive!

Linux is all about choice and freedom.  Enjoy it. :-)

---

### Post by grahammechanical on 2013-02-10
My advice to you would be to download the Ubuntu ISO image and burn it to CD/DVD or install it on a USB stick and then run a live session. See, if the external hard drive is recognised.

Try to install. Choose the Do Something Else option and see if the partitioner lets you install on the external hard drive. Remember, to boot from that external hard drive you may have to change the BIOS settings. Likewise, to boot from DVD or USB.

[http://www.ubuntu.com/download/help/install-desktop-long-term-support]("http://www.ubuntu.com/download/help/install-desktop-long-term-support")

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")

[http://www.ubuntu.com/download/help/burn-a-dvd-on-windows]("http://www.ubuntu.com/download/help/burn-a-dvd-on-windows")

As for speed, as Einstein said, it is all relative. How fast is your CPU? How fast is your GPU? How much video memory does it have? How fast is your hard drive? How fast can move the mouse and press keys? There is no such thing as an instantly loading application. 

Regards.

---

### Post by gregoryshock on 2013-02-16
I am sorry that I haven't been around lately to read the other suggestions.  For I sure there is more then one way to do this.  Here is an Update on what I actually did.  It worked But...

Today I Used my old Desktop computer to install Ubuntu to the External Hard Drive.  The way I did this, I opened up the case and disconnected the internal hard drive.  Booted from The Ubuntu DVD and Installed it to the External.  

The installation was successful.  I wasn't able to boot up from the  External on the Desktop.  I didn't try very hard, but it doesn't appear  to have a usb boot option in the bios.  I connected the external hard  drive to my Laptop.  Set the Bios accordingly, and booted.  I was in  Ubuntu 11.10 in no time.  The point of putting it on the External hard  drive is for learning and experimental purposes.  Linux notified me of  updates that are available to it.  One was to upgrade it to 12.04.  I  decided to go ahead and try...  The result is a crashed External Hard  Drive.  I'm not sure how to recover this.  It seems to me that my  options are A)  to re attach it to the Desktop and try a Reinstall.  Or  B)  Try and down load 12.04.  Either way I think I will need to re  attach the External to the Desktop Computer.  I don't know what caused  the actual Crash.  At first it was downloading stuff, next it was ready  to install stuff.  It was installing when the progress bar disappeared  and next all the icons plus the shut down button (Top Right) vanished.  I  waited a while, and since nothing was happening I didn't know what to  do.  I held down the PC power button until the system stopped.  I  thought maybe when I tried to reboot I would have some options.  The  first try did nothing more then freeze up.  The second try gave me the  option of booting in safe mode.  Since I have yet to learn any Linux  commands, I am currently sunk. :(

---

### Post by Zill on 2013-02-16
> **gregoryshock said:**
> ...One was to upgrade it to 12.04.  I  decided to go ahead and try...  The result is a crashed External Hard  Drive...(
Upgrading from one release to another has "uncertain" reliability at the best of times!  To try to do this on a hard drive with a release that was originally configured on a totally different machine is really asking for trouble. ;-)  I have been using Linux for around ten years now and I wouldn't even attempt this one!

As a "newbie", I do suggest you will get better results if you just do a standard installation of your chosen release direct to the internal hard drive.  This should "just work" out of the box.  When you wish to upgrade to a later release, the most reliable method is simply to do another fresh install, rather than an upgrade.  This is far quicker and generally gives better results.

One top tip is to ensure that you have a separate /home partition on your hard drive.  This *should not be formatted* when you reinstall meaning that all the your settings and files in /home/myuser are retained.

Having said that, *always* keep regular backups of your data, *especially* before doing any major surgery such as a re-install.

---

### Post by gregoryshock on 2013-02-16
> **Zill said:**
> Upgrading from one release to another has "uncertain" reliability at the best of times!  To try to do this on a hard drive with a release that was originally configured on a totally different machine is really asking for trouble. ;-)  I have been using Linux for around ten years now and I wouldn't even attempt this one!

As a "newbie", I do suggest you will get better results if you just do a standard installation of your chosen release direct to the internal hard drive.  This should "just work" out of the box.  When you wish to upgrade to a later release, the most reliable method is simply to do another fresh install, rather than an upgrade.  This is far quicker and generally gives better results.

One top tip is to ensure that you have a separate /home partition on your hard drive.  This *should not be formatted* when you reinstall meaning that all the your settings and files in /home/myuser are retained.

Having said that, *always* keep regular backups of your data, *especially* before doing any major surgery such as a re-install.

Call me a dare devil if you like...  But I can't afford to buy a new computer for just testing stuff...  I will avoid the "update".

---

### Post by gregoryshock on 2013-02-16
I used the Ubuntu 12.04 DVD with my old Desktop and installed it to the  External Hard Drive.  After I carefully looked over the Bios, I noticed  that I could indeed boot from USB.  It just wasn't in the list of boot  devices as the DVD, Hard Drive etc.  I did a test boot and it booted.   Next I plugged the External Into my Laptop.  I am currently using Ubuntu  12.04 from an External Hard Disk.  It seemed to take on the updates ok.

---

