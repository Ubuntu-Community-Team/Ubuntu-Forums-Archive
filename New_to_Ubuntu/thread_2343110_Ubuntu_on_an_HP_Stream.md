---
title: "Ubuntu on an HP Stream"
date: 2016-11-13
forum: New to Ubuntu
---

### Post by wfriedwaldgmail.c on 2016-11-13
I have an 2014 HP stream - a very minimal machine, mostly a "netbook" - very little memory or capacity etc.
(My main computer / desktop is a Mac...)

I have always wanted to switch it over to Ubuntu - and now may be the right time.

I was attempting to reset the machine, to wipe everything clean and install a new Windows OS ... anyhow, it crapped out in the middle of the reset.  Now there's no OS - when I turn it on, it flashes the HP logo for a few seconds, then a blank screen, then HP logo for a few seconds again, then a blank screen again, and so on, over and over.

I would like to try installing Ubuntu (I tried once before and couldn't get that going) - 

I would probably need to use a USB stick.  So, the issue would be making a USB stick on my Mac and then hoping the HP will boot from it.

I do currently have a 4GB USB stick formatted in traditional MS-DOS that I can use - that should work.  I hope!  Yes!

w

---

### Post by howefield on 2016-11-13
Have a browse here, probably will answer you question.

[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)

Scroll down to the section entitled "*Easy ways to switch to Ubuntu - From Mac OS X*"

---

### Post by wfriedwaldgmail.c on 2016-11-13
thanks very much!

All right-  now I have the ISO file on my Mac desktop.

and I have the MS-DOS USB drive in the port.

so: am trying to figure out what the next step is - do I just copy the ISO file to the flash drive?

Then, obviously, I'll stick in the HP laptop and try to boot... will see what happens.

thanks, I would love for this to work!

w

UPDATE: I am trying UNetbootin - the trick now is trying to figure out which of my USB devices gets which code name, ie, "/dev/disk14s2" - there has to be some way to see that.  right now UNetbootin is finding four "dev" drives.  thanks!

---

### Post by howefield on 2016-11-13
Did you read the link ?

You need to use an application to create the live USB, the link mentions Unetbootin but there are many others. I do not know which are suitable for using on a Mac though, apart from what is mentioned in the link.

---

### Post by wfriedwaldgmail.c on 2016-11-13
thanks, yes, what's confusing is that I am download on a Mac, but need to install onto a windows machine, so am not sure what set of rules applies.

thanks again, yes.

w

---

### Post by howefield on 2016-11-13
> **wfriedwaldgmail.c said:**
> ...So, the issue would be making a USB stick on my Mac and then hoping the HP will boot from it.

> **wfriedwaldgmail.c said:**
> ..but need to install onto a windows machine, so am not sure what set of rules applies.

So, which is it then ?

If you are creating a live USB on a Mac follow the directions for the MAC, if creating it on a Windows machine, then follow the directions for that platform. Doesn't matter how it was downloaded.

---

### Post by &amp;KyT$0P# on 2016-11-13
Just use the method #4 from [here]("http://www.webupd8.org/2009/04/4-ways-to-create-bootable-live-usb.html").

---

### Post by wfriedwaldgmail.c on 2016-11-13
Nuts!  Rats!

I believe I successful created a USB boot drive, but the HP does not recognize it, or, does not boot from it.  I tried push the F12 button, which didn't seem to do anything.

I actually created two different USB boot drives, to see if one would work any better than the other, but no dice, neither of them worked.

Any suggestions for a possible next step?

w

---

### Post by Bucky Ball on 2016-11-13
How did you end up creating the USB? When you select it from the boot order, if you can, what exactly happens? You get booted into Windows?

You need to hit F12 pretty much straight after boot. Hit F12 like you were hitting whatever the key is to get to the BIOS.

---

### Post by Autodave on 2016-11-14
I have one old netbook that will not boot from a USB stick. I use an external DVD drive and it will boot from that. You will have to burn the Ubuntu install file as an ISO to the disk. 

If this is a basic netbook, I would be using Xubuntu since it is a much lighter install.

I have an Asus EEEPC running Xubuntu 16.04. 900Mhz, single core, 1 gig RAM: and it runs just fine.

---

### Post by Geoffrey_Arndt on 2016-11-14
Sometimes there are difficulties using certain programs to create a bootable image on your usb flash-stick.

I've had the best success with a relatively new program called "Etcher" . . . it's simpler and very reliable.   It works in Windows, Linux and MacOS.

Also, it is Open Source and the code is available via GitHub.   

check it out:    [URL="https://etcher.io/"]https://etcher.io/


[/URL]

---

### Post by tea for one on 2016-11-14
> **wfriedwaldgmail.c said:**
> Nuts!  Rats!

I believe I successful created a USB boot drive, but the HP does not recognize it, or, does not boot from it.  I tried push the F12 button, which didn't seem to do anything.

w

I have an HP Stream 11 (purchased in 2016) and the configuration in the HP Boot Manager is to use F9 to boot USB drives.

Any good?

Also, have you turned off Secure Boot in the set up utility?

---

### Post by wfriedwaldgmail.c on 2016-11-15
Okay!  Here is the latest:

1. to make sure that the USB drive(s) were working, I tried one on another laptop I have - a much older Dell Inspiron "netbook."  and yes, it worked just fine here.  the Dell found the drives and installed Ubuntu on itself without a problem.

2. then I put that same USB stick in the HP.  It still doesn't find it by itself.  But when I go into the BIOS / "boot manager" / "file explorer," yes, it does seem to see the USB drive ("cruzer2") however, I don't know how to select that, in the sense that I tell it to boot from the Cruzer2.  When I select it, just goes into the file directory, and shows me what's there.

so, my question would be, since the HP is actually seeing (in some sense of the term) the CRUZER2 USB drive, how do I tell it to actually boot from that drive?

(Like I say, that happened instantly on the dell... worked just fine.)

w

here are some shots of the stuff I'm seeing in BIOS, boot options, file explorer etc 

thanks again for any help!

w

[ATTACH=CONFIG]272138[/ATTACH][ATTACH=CONFIG]272139[/ATTACH][ATTACH=CONFIG]272140[/ATTACH]

---

### Post by Bucky Ball on 2016-11-15
How about this:

> 3. With bootable USB restart machine and press escapte key continuously
4. Press f9 to boot from USB

... [from here]("https://ubuntuforums.org/showthread.php?t=2297546"). You may have already tried it. Does F9 take you to the boot manager page you have in your third screenshot? I have a HP Stream 11 and don't remember that or having these troubles. I did have some troubles and wish I did remember how I solved them cos it might help you now. ;| ;)

[This may also work for you]("http://bernaerts.dyndns.org/linux/74-ubuntu/343-ubuntu-install-hp-stream-13"). It is for the 13 but shouldn't make any diff. Shouldn't ... ;)

---

### Post by oldfred on 2016-11-15
Is this a Atom Bay Trail Intel chip which has had issues.
Or a 32 bit UEFI boot even if 64 bit chip. Vendors did that as then Linux did not have 32 bit UEFI boot to make it Windows only. But Ubuntu does have a 32 bit UEFI boot, but not particularly easy to configure. Better now as pre-compilied and you can down load the bootia32.efi.

If 32 bit may be similar?
 Instructions to install Ubuntu 16.04 on ASUS EeeBook X205TA - Atom Bay Trail 32 bit UEFI
[https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md)

---

### Post by wfriedwaldgmail.c on 2016-11-15
Okay! Thanks.

Am going to attach another picture of what I'm getting.

In the SYSTEM CONFIGURATION option: 
I played around with the function keys until I had the USB DISKETTE ON KEY/USB HARD DISK - 
now it's highlighted in white and at the top of the list.
However, the "OS BOOT MANAGER" still has the indicator thingie next to it.
so, does this mean that when hit F10 to "save and exit," that it will then boot through the USB DISKETTE ON KEY/USB HARD DISK

I tried that ... it doesn't seem to have made any difference, but knowing me I am probably doing something wrong.

I will keep trying, sooner or later I will lick this! I hope!

w
[ATTACH=CONFIG]272145[/ATTACH]

---

### Post by tea for one on 2016-11-15
When I wanted to boot an installation USB drive (loaded with Xubuntu Core) on my HP Stream 11, I had to enable Legacy Support which automatically disables Secure Boot.

Press F10 to enter Set up utility
Arrow right to **System Configuration**
Arrow down to **Boot Options**
Arrow down to **Legacy Support**
Change Disabled to **Enabled**

Save and exit

Restart and press F9 to select USB drive

---

### Post by wfriedwaldgmail.c on 2016-11-15
whoa!  yes! that seems to have done the trick!

so far so good!  I shall give you a fuller report later on!

thank you!

w

---

### Post by wfriedwaldgmail.c on 2016-11-15
Yes!  seems to have installed and updated successfully.

thank you very much.

I may start a new thread ... regarding an app that I'm now looking for.

thanks again!

w

---

### Post by tea for one on 2016-11-15
> **wfriedwaldgmail.c said:**
> Yes!  seems to have installed and updated successfully.

thank you very much.

I may start a new thread ... regarding an app that I'm now looking for.

thanks again!

w

Splendid - It would help other users if you could mark the thread as solved

Kind regards

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Bucky Ball on 2016-11-15
Good news and got there in the end. Yes, start a new thread for any new issues and

> **tea for one said:**
> ... It would help other users if you could mark the thread as solved

+1. 

If Ubuntu is running ok on that, Xubuntu will fly. I wouldn't bother using Ubuntu on mine, but then, I'm not interested in the bells and whistles and only use it for basics; maps when travelling, surfing, music. I have Xubuntu-core on mine. 

Good luck. ;)

---

