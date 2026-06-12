---
title: "First install experience"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by Roliocat on 2012-07-16
Hi Guys,

OK, so I came across Ubuntu 12.04 LTS on the net, downloaded the 32 bit version, burnt the CD, booted on my desktop and had look at it (preview from CD), decided I liked what I saw and want to install to my desktop computer (same as which I previewed on).  Needless to say I know/knew zilch about Ubuntu.

So I boot the machine, Ubuntu install goes through the motions, I say it can have the whole HD to itself, get past the Username and Password screen and the install continues for a few moments.  It jumps out of GUI mode into a black screen (like old DOS) and gives a string of scrolling messages, starting this, stopping that, failed etc. until the scrolling stops, machine freezes and thats it.  You have to restart the PC and same happens over and over.  So I change the HD thinking it might have a problem there, same thing.  Specs are:
Phoenix Award Bios
AMD Atlon XP 2800+ Processor
Nvidia GeForce2 MX/MX 400 graphics card
2GB Ram
320GB HD

So I give up on this install, and my Win XP OS is now screwed on it anyway, and take my notebook out.  It is an Acer emachine E725, stock standard.
I go through all the Ubuntu install motions, everything seems fine, it reboots and I get a black screen, that's it.  Power down (forced), restart, same thing.  So I get the missus's old Dell out (it's the only working PC in the household right now as I have just screwed another working Win OS) and go on the net to find a solution.  Presto, the Acers do have a graphics problem resulting in a black screen.  
Ok, according to the gurus you boot, go to 'Grub' and do several changes.  What is Grub and how do I get in there anyway with a black screen in front of me?

As a last attempt I decide that the Dell, being old (Dell Latitude D600) should be able to handle the Ubuntu install.  Boot with the CD and then before anything meaningful happens I get a black screen with the following
"This kernel requires the following features not available on this CPU - pae
Unable to boot - please use a kernel appropriate for your CPU'

Any suggestions, other than me having to buy a PC to suite the Ubuntu OS?

---

### Post by lukeiamyourfather on 2012-07-16
> **Roliocat said:**
> 
Nvidia GeForce2 MX/MX 400 graphics card


If I had to guess I'd say it has something to do with that. Given the age of the hardware I'd look at using an older distribution.

---

### Post by hypnot0ad on 2012-07-16
I came across a problem similar to this. 
For my machines it wasn't extracting everything it needed. At first I thought I had burned the disk wrong (nope.) Then I thought maybe the distro was bad (nope.)

If you have your Windows disks and are serious still about *buntu, but Windows back on, and maybe send away for a *buntu disk as they are cheap enough.

 "First install experience"
Hope this doesn't turn you away op.

---

### Post by verymadpip on 2012-07-16
To get around the PAE thing you could try installing 32 bit Lubuntu or Xubuntu.  Either of those would probably be a wise choice for ageing hardware.

---

### Post by Roliocat on 2012-07-16
Thanks for the responses thus far.  My preference would be to get *buntu running on any one one of the above machines in the same order in which I tried loading as per my initial post.
Any suggestions on which version of *buntu I should try on them with a prospect of success?

---

### Post by Lega11yblonde on 2012-07-16
This is my second install experience and it's a disaster. I had an old Compaq that I used to install a dual boot system and the wifi never worked. I got a brand new laptop, cheap but new, running Windows 7 Home Premium, used the disc that I loaded the other laptop with, and lo and behold absolutely nothing happens when I either restart or completely reboot my computer. It just goes straight to Windows. 
 
Sigh.

---

### Post by Rex Bouwense on 2012-07-16
Roliocat.  Lubuntu works well with older machines.  Granted it is extremely lightweight and is missing alot of the eyecandy that Ubunty can have, but if you are looking for an OS that you can do basic computing, it is your baby.  Now when you add newer more powerful computers into the mix, it also works well on those and those can be fluffed up a bit to whatever you care to do with it.  If that is too light there is also Xubuntu which is lighter than Ubuntu but not as light as Lubuntu.

Lega11yblonde please start your own thread as your problem may be different than the OP which may require different solutions.

---

### Post by verymadpip on 2012-07-17
Hey Roliocat.

I'd try for a Lubuntu install on the Dell Latitude at this point (that's just me though).
I feel your pain about being unable to put what you want where you want :(

GRUB is the bootloader for *buntu.  There are things one can change at boot (& afterwards) to make changes permanent, if they've worked for you.

This thread explains it better than I can:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Good luck & keep us posted.

---

### Post by d4m1r on 2012-07-17
1) Seems like you have several old machines in the house that are NOT ready for the latest technologies found in 12.04...Have you thought about buying a new PC and installing Ubuntu on there?

2) As for the CPU/PAE related message, 12.04 ships with PAE required stuff on the stock disk so try to find the non-PAE 12.04 installer on the net if you can, OR install 11.10 which can also be downloaded off of ubuntu.com

---

### Post by Roliocat on 2012-07-18
Just some feedback (more to come) - I  attempted to install Xubuntu and then Lubuntu (both 12.04 Desktop) on my desktop machine (first one in my intial post), both failed during install -ok, so I have decided to give up on that machine - back to Win 7 I go on this one.
 
Tonight I want to attempt an install on the Acer simply because Ubuntu 12.04 did install on my initial attempt, just the backlight just being an issue.  There are however several posts with solutions for this so I would want to attempt an install with Ubuntu12.04  again.
These posts however all point to making changes from within Grub.
How would I get a terminal session to be able to use Grub?  ie. bearing in mind that the install culminates in a dark screen so I will not be able to see what i am doing?
At what stage during the install, should I do what, to get a visible terminal session, before getting to a black screen?

---

### Post by mastablasta on 2012-07-18
> **d4m1r said:**
> 1) Seems like you have several old machines in the house that are NOT ready for the latest technologies found in 12.04...Have you thought about buying a new PC and installing Ubuntu on there?

 
That's BS. If the system worked in live session (try it) then it should work on install as well. even more so if the previous sytsem on computer was windows 7.

---

### Post by mastablasta on 2012-07-18
> **Roliocat said:**
> Just some feedback (more to come) - I attempted to install Xubuntu and then Lubuntu (both 12.04 Desktop) on my desktop machine (first one in my intial post), both failed during install -ok, so I have decided to give up on that machine - back to Win 7 I go on this one.

 
Did you check the md5sum of the downloaded file? [https://help.ubuntu.com/community/HowToMD5SUM/](https://help.ubuntu.com/community/HowToMD5SUM/)
Did you check that the disk burned propperly (burn at lowest speed, verify after burn)?
Did you try alternateCD (with text based installer)? [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)
 
if the live OS works then install should work as well.
Also a much safer option than CD/DVD is to use USB key (you can "burn" the image on it using unetbootin).
 
aside form alternate CD install there is also a mini.iso install option which is a non-pae kernel (see more here: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)).
 
>  
Tonight I want to attempt an install on the Acer simply because Ubuntu 12.04 did install on my initial attempt, just the backlight just being an issue. There are however several posts with solutions for this so I would want to attempt an install with Ubuntu12.04 again.
These posts however all point to making changes from within Grub.
How would I get a terminal session to be able to use Grub? ie. bearing in mind that the install culminates in a dark screen so I will not be able to see what i am doing?
At what stage during the install, should I do what, to get a visible terminal session, before getting to a black screen?
 
Grub is boto loader. it loads just after BIOS and just before the OS loads. to get to it you need to hold shift key after BIOS boots. you can then try various boot options within it. see here: [https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)
 
grub is usually edited by editing a file (grub.cfg) and then updating grub. you can editi it using live CD is live CD boots/works.
 
additonay you should always test (option "try it") before doing a full install. as mentioned if liveOS works then the install should work as well providing the install media and downloaded image are OK. if you used CD for install another option is a faulty CD drive.
 
another option that offers safe troubleshooting & testing is wubi install. it installs in a virtual disk. if the install get's corrupted you can remove it just like any other windows programmes.

---

### Post by verymadpip on 2012-07-18
Lubuntu 12.04 ships with a non-PAE kernel by default.

I suggested Lubuntu for the machine that is not PAE capable (Dell Latitude IIRC).

I still think this thread is helpful for modifying the boot parameters:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

It seems to be a coherent "tutorial".

---

