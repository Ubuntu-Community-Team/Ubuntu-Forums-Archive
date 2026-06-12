---
title: "Old computer, can't get Ubuntu to boot"
date: 2012-09-13
forum: New to Ubuntu
---

### Post by PB268 on 2012-09-13
Hi guys,

Have installed Ubuntu 12.4 on an old PC. But when it comes to boot it gives up looking for root device and dumps me into BusyBox <initramfs>.

Have already looked on here and think I need to edit "menu.lst" to increase the delay, but can't edit anything from the command line I'm on.

Think I have to hold down [shift] boot time to get Grub to load, then press [e] to edit -- but tried that a number of times, and can't get anything to load :O/

Any help with where I'm going wrong?

Many thanks.

Bob :D

---

### Post by snowpine on 2012-09-13
Welcome to the forums!

Let's back up a step. What are the hardware specs of your old computer? Did you test drive the Live CD prior to install, and if so, what was the result?

---

### Post by PB268 on 2012-09-13
Hi, thanks for the welcome.

Bought PC off ebay a couple of days ago, came with no OS. Has 40gb HD 512MB memory, ASUS A7VT. Bought as something to mess around with Ubuntu to see what it's like.

Didn't test drive CD, but it seemed to install ok. Didn't bother to setup any kind of partitions on HD.

---

### Post by snowpine on 2012-09-13
I just googled your system and to be honest I am completely unfamiliar with this hardware, hopefully another user will be along to assist. (Or you can use the Search box at the top right of the screen.)

In the meantime you might want to test-drive the Live CD and also to read up on partitioning.

---

### Post by cracker89 on 2012-09-13
see if pressing the key f4 during the boot screen brings up anything?

---

### Post by PB268 on 2012-09-13
Thanks for your time... I'll see what I can find :)

---

### Post by PB268 on 2012-09-13
[F4] during boot = blank screen with flashing cursor top-left, but can't type anything, and then it returns to BusyBox.

---

### Post by cracker89 on 2012-09-13
type "exit" after initramfs?

---

### Post by cracker89 on 2012-09-13
I think typing exit should get you onto your log-on screen. if it does, this has been an issue with some ppl in the past with past versions of ubuntu. but 12.4 was supposed to have fixed it. but im sure if its a problem with the bootloader (grub2) or partitioning, it can be worked around.

once on busybox, type the following and post the output please?
```
fsck -y /dev/sda1
/sbin/fsck -y /dev/sda
```

---

### Post by PB268 on 2012-09-13
"exit" just causes the error text "Giving up waiting for root device" to reappear and I'm back in <initramfs>

Forgot to add, there is some text which reads:-

cat /proc/cmdline

check rootdelay
check root

But will take photo of screen and post tomorrow. Will call it a day for now.

Thanks.

---

### Post by snowpine on 2012-09-13
I'll repeat my advice to test-drive the Live CD.

If the Live CD works but the install doesn't, then that is a completely different scenario vs. neither works.

---

### Post by cracker89 on 2012-09-13
also, right before the busybox prompt (the line that says "BusyBox vX.XX.
X (Ubuntu blah blah) built-in shell 
Enter 'help' for a list of built-in commands."), there should be a few lines of text. could you also post those here? they will help us in determining why the boot failed. 

Thanks. and Dont Panic!

---

### Post by PB268 on 2012-09-13
Getting the following

/bin/sh: fsck: not found

---

### Post by PB268 on 2012-09-13
Not feeling 100% at the moment, and PC with Ubuntu is in other room. Off for a quick lie down.

Thanks.

---

### Post by cracker89 on 2012-09-13
i'm off for now too bud. but ill c u tomm to try n help sort this out. meanwhile, heres some reading:
[http://ubuntuforums.org/showthread.php?t=1027432&page=2](http://ubuntuforums.org/showthread.php?t=1027432&page=2)
[http://ubuntuforums.org/showthread.php?t=1962175](http://ubuntuforums.org/showthread.php?t=1962175)
[http://ubuntuforums.org/showthread.php?t=1653682](http://ubuntuforums.org/showthread.php?t=1653682)
[http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)
[http://stackoverflow.com/questions/9492174/how-to-fix-boot-error-after-fresh-installing-ubuntu-10-04-lts](http://stackoverflow.com/questions/9492174/how-to-fix-boot-error-after-fresh-installing-ubuntu-10-04-lts)
[http://www.elfnet.org/2010/07/20/ubuntu-10-04-grub-boot-error/](http://www.elfnet.org/2010/07/20/ubuntu-10-04-grub-boot-error/)

---

### Post by BrianBlaze on 2012-09-13
I would try a live cd or USB and see what happens... because I know for some of my buddies older computers I would try to install off a live USB and it would say they didn't have enough memory to install... Check it out :) I would try an older version! I havent been able to install new Ubuntu or Fedora on older machines sadly...

---

### Post by arpanaut on 2012-09-13
With the specs. of that rig you are going to have better (if any) results trying Lubuntu.
The supported cpu's are way out of date.
The memory is low. (well, medium low)
The onboard SIS graphics chipset is barely supported these days.
And if you have an additional pci graphics card installed it is only AGP x4.

So, sorry to say, you are going to find it difficult to run full blown Ubuntu 12.04
Try Lubuntu and see if you have better luck.

Not trying to be harsh,  just stating facts.
Good Luck!

---

### Post by cracker89 on 2012-09-13
I'd go with arpanaut. he makes sense.

---

### Post by Gone fishing on 2012-09-13
You installed? and now its booting to busy box. Or this is a live CD? If its a Live CD burn a new one this one has a problem. If you installed then it means that the boot loader cant find the Linux. Why I don't know but I'd repartition and reinstall this will be easier than fixing.

 That box will stuggle with Ubuntu - I'd try a lighter version of Linux.

---

### Post by mörgæs on 2012-09-13
Yes, X/Lubuntu is your best choice. Ubuntu will be a pain.

If the standard ISO does not boot you could try the alternate one.

---

### Post by PB268 on 2012-09-13
Having a look at cracker89's links... but think a lighter version might be the way to go :)

Thinking about it, I don't actually HAVE to run Ubuntu. Main computer died a few weeks ago so using backup PC which runs XP. But now need a new backup, so ordered ASUS off ebay. As long as I can get the ASUS online, I'm happy :)

Thanks for all the help.

---

### Post by mips on 2012-09-14
> **PB268 said:**
> ... but think a lighter version might be the way to go :

[http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-alternate-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-alternate-i386.iso)

---

### Post by PB268 on 2012-09-14
Thanks for the link, downloading now. Lubuntu feels like the way to go for backup PC.

On another issue, installed Puppy as a second OS on main PC... looks like a handy thing to have, but only one slight snag, I can't get Flash to work with either Chrome or FF. But I'll sniff around at it later ;)

---

### Post by mips on 2012-09-14
> **PB268 said:**
> Thanks for the link, downloading now. Lubuntu feels like the way to go for backup PC.

On another issue, installed Puppy as a second OS on main PC... looks like a handy thing to have, but only one slight snag, I can't get Flash to work with either Chrome or FF. But I'll sniff around at it later ;)

Flash works on Macpup 529 for me.

---

### Post by PB268 on 2012-09-14
DONE IT!

Well... got a £15 PC, off ebay, online for no extra money (luckily had spare monitor, keyboard and mouse) ;)

Lubuntu had exactly the same problem as Ubuntu, but running Slacko (Puppy) and so far so good... posting this from backup PC "Hello World!" ):P

---

### Post by Epodx64 on 2012-09-14
Could it be the CPU doesn't support the PAE extension?

---

### Post by cracker89 on 2012-09-14
> **PB268 said:**
> DONE IT!

Well... got a £15 PC, off ebay, online for no extra money (luckily had spare monitor, keyboard and mouse) ;)

Lubuntu had exactly the same problem as Ubuntu, but running Slacko (Puppy) and so far so good... posting this from backup PC "Hello World!" ):P

well done mate. it was obviously lack of hardware then. mark the post as [SOLVED] if u satisfied.

cheers.

---

### Post by vexorian on 2012-09-14
> **Epodx64 said:**
> Could it be the CPU doesn't support the PAE extension?
I wanted to ask this very much.

---

### Post by PB268 on 2012-09-14
**Have marked as solved!**

(still have problems seeing flash content even with flash installed... but will save that for another day)

Thanks again, you are a very helpful bunch, if "bunch" is the correct collective name for techies ;)

---

### Post by mörgæs on 2012-09-14
> **Epodx64 said:**
> Could it be the CPU doesn't support the PAE extension?

You are probably confusing PAE and CMOV.

Lubuntu 12.04 supports non-PAE hardware, but 10.04 was the last supporting non-CMOV. 

This motherboard is from around 1999/2000, and it is likely that the missing CMOV is the explanation (sorry for not being alert when I posted first and recommended Lubuntu). 

If original poster wants to know please post the CPU details or the output from **lshw**.

---

### Post by Epodx64 on 2012-09-14
> **mörgæs said:**
> You are probably confusing PAE and CMOV.

Lubuntu 12.04 supports non-PAE hardware, but 10.04 was the last supporting non-CMOV. 

This motherboard is from around 1999/2000, and it is likely that the missing CMOV is the explanation (sorry for not being alert when I posted first and recommended Lubuntu). 

If original poster wants to know please post the CPU details or the output from **lshw**.

you're right. Lubuntu and Xubuntu both support the none PAE kernel.

---

### Post by mips on 2012-09-18
> **mörgæs said:**
> You are probably confusing PAE and CMOV.

Lubuntu 12.04 supports non-PAE hardware, but 10.04 was the last supporting non-CMOV. 

This motherboard is from around 1999/2000, and it is likely that the missing CMOV is the explanation (sorry for not being alert when I posted first and recommended Lubuntu). 


I learned something new today wrt CMOV.

I actually remember the command from assembly days.

---

