---
title: "How do I boot Ubuntu 12.10 using an external HDD and no internal HDD?"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by Writt on 2012-12-07
things to know:
I'm running ubuntu on a 10G HDD and a 500G external
I  don't have money to go out and change the 10G problem.(my windows lappy  was stolen, my brother made me this pc to help me get through school)

At  first I was excited to learn linux, I use to build components, I  understand how computers work, and basic programming. Yet I lacked the  experience linux required and totally down to learn.

The Issue:
Everything  I install, installs into the C drive. All my downloads and programs  check there for space, and I can't get anything to run or finish  installing because the OS drive is too small, although i have a big 500G  external to use. Wine and Crossover are on the C drive. I can't get  anything to go on the E drive manually. I tried the REGEDIT  and just switched C for E for program files, pictures, temp,  (couldn't find Downloads).... Tried running the starcraft to install exe  on crossover, but now it's saying can't find directories. (it was semi  installed at this point because it ran out of space, and now i don't  know how to start from scratch). I don't have an issue mapping back to C  since everything that has an E flags the needed changes, no biggie.

What Do I do?
I just want to have  the OS on the 10G, and EVERYHTHING ELSE on the 500G.
Sigh.
common solution that aren't an option:
Destroying my external case and converting it into a internal=(
Buying a new internal. =(

Moving forward after one post of advice:
[quote="just brew it!"]What you need to do is create and format a partition on your external, copy the contents of your .wine directory to it, then mount that partition over your .wine directory. A symlink might work instead of a hard mount, that would actually be easier (if wine is OK with it).

Or take apart the external and swap the drive into your system as the system drive. :wink:[/quote]

My steps to solving this ended with:

Alright, what I've done so far is get ubuntu 12.10 on a boot cd,  disconnected my IDE cable from the internal, boot the cd from the dvd  drive with the external off(for some reason it doesn't get bast booting  with it on, even when using the internal). I turn on the external after  i'm in the trial, install ubuntu on the external, and then booted with  only the external connected. 

What I end up with is a 
"extent error"
GRUB:

and that is my current wall. 

researched  GRUB, came across BURG. I would delve into it more if I felt there was  support for external drives. it seems to be catered for internal drives.  Utilizing GRUB/BURG at boot may also be the giant variable here  determining my success..... the manual boot part, not the dualboot  aspect of it. 

I checked out the symlink command on the ubuntu  forum, and a few videos. It seems like this is a route I must take if I  can't figure out how to use the 500G with a fresh instal. It shows that  its really easy to do on older versions of ubuntu. 7.something where i  would go into the system settings and just uncheck some simple drive  checkboxes from the live cd part of the install, then install from there  and voila. I'm scared going backwards in versions will only just  increase my compatability issues with new games and software support.

My quetion now with this symlink (very handy by the way, glad you posted about it) is:

 Will it create and store data in both locations doubling the space used?
Can  I create the link on the C drive where the os wouldnaturally put  information, and have that data actaully stored in the E dive?

If so then this might be the solution.

Or  flat out, and this is my last resort, break the external case and slot  it internally through sata. thankfully sata cables are 3 bucks. lol 

That's obviously the easy way out, but it's also the way I don't learn and remain a linux noob =(

Helpppp

---

### Post by danelwillis on 2012-12-07
you need to enable the use of usb in your cmos/bios we the computer is in the bios when its turned on generally press F12 is for me anyway the multiboot and use arrow keys to move to usb, basically that means when u boot it will boot from usb. that's step one, then use your live media device to install on the page were it ask for partition or the hard-drive theirs a small arrow next to writeing "sdb/dev/* and click that it should see your hard-drive then partition that and it will install off the HDD

---

### Post by Writt on 2012-12-07
Alright, so I went into the Disk on the desktop and theres a boot partition(most of the drive, a swap partition(around 4gigs) and a extended partition. if its the swap, its sdv5, if its the large one, then sdv1.

Anyway, I hit F8 to choose boot device (not delete for bios options that change priority) and chose USB. it then gave me a dos screen that said 
Invalid Extent:
Grub Rescue>

I then entered  "ls" and it gave me a list of hd's. 
Example (hd0) (hd0,msdos1) (hd1,msdos1) i think there was a (hd1,msdos5)

After trial and error I found that the one with vmluniz was  (hd1,msdos1). I didn't continue after that.

I achieved this by entering: ls (hd1msdos1)/boot 

I then entered set root=(hd1,msdos1)/boot
it just gave me another line of simply: grub rescue>
I entered insmod linux

Thats the the wall i'm at now. after some research in grub rescue tonight, i think i'm supposed to enter linux (hd1,msdos1)/boot/vmluniz-5.6.something
then a similar one for intrid, but after i enter insmod linux i get a directory error and then i enter the vmlunix line and i get a linux command does not exist. 

I'm either on the right track, or I went down the wrong track after I first landed on this screen period.

I'm a little fuzzy on understanding the whole choose HD from a live media source.

---

### Post by C.S.Cameron on 2012-12-07
Can you set your USB drive as first HDD in grub?
Some computers just will not boot USB.
If this is the case, try Plop boot manager.

---

### Post by Writt on 2012-12-07
Alright, After more work on the issue, I got a bit further towards success. I feel like this might be the last wall I have to break down before it works.

1. I reinstalled 12.10 on the external.

2. from the live CD, I opened the Terminal and installed GRUB2 and updated it.

3. From the Terminal, I installed Boot-repair with a Sudo get apt command. I ran the program launched from Terminal, but it never got to the screen where I could repair the recommended. It would Scan for over 10 minutes. So I just killed it. 

After this, I rebooted, hit F8, Chose USB to boot, and then finally had the black screen where I could choose Ubuntu, advanced Ubuntu boot where I could run safe mode, and other options. 

I tried both safe mode and normal boot, and I end up with the screen pictured in the attachment with this post. 

 It Is mentioning a root error concerning a kernel.

I entered :
root=(hd0,6)
prefix=(hd0,6)/boot/grub
insmod normal
normal

This did not work.
Maybe because the hd with ubuntu with nothing else in the computer is (hd0,msds1)? should I just put (hd0,1)?
I think I have to start messing with code that uses a loop command..


going to try something like set prefix=(hd0,1)/<path to modules> 

Any comments or advice would be awesome =)

---

### Post by elhancho on 2012-12-07
I'm sorry if I don't understand you correctly, but I think you may have the same question I did. If so, you can check out the thread that I started at the link below, but please excuse me if I misunderstood your question.

[http://ubuntuforums.org/showthread.php?t=2091124&highlight=seperate+hard+drive](http://ubuntuforums.org/showthread.php?t=2091124&highlight=seperate+hard+drive)

---

### Post by Writt on 2012-12-07
The difference between what you wanted to do and what I want to do is really that you had no problem doing it.

It should be as simple as install OS on external (countless videos and threads about this) with internal disconnected, you can reconnect the internal after completion( I left it unhooked after a bunch of strife), reboot, prompt the OS loader, select ubuntu, and that's it. 

For me though, everything that could go wrong, went wrong. Well, lets hope more doesn't happen. 

I'm having GRUB RESCUE prompts, kernels not rooted, and a hell of a time entering the file directories with the grub rescue. 

For instance, I'm locating the proper hd, double checked that the files were on there through the 10G OS, and reaching file not found once I'm a few folders in. 

I'm almost certain I am a step away  with rooting/looping the proper kernel and file paths for that, for successful boot. I just need to figure out how to properly implement a few lines of code. =(

Thanks though! =)

---

### Post by C.S.Cameron on 2012-12-07
Sometimes problems can be the result of a corrupt download.
Have you checked the iso's MD5SUM?

---

### Post by verymadpip on 2012-12-08
I often find USB drives are listed in the hard disks section of the boot whatsit in the BIOS.

Just something to try really, this all seems far too technical for me :)

---

