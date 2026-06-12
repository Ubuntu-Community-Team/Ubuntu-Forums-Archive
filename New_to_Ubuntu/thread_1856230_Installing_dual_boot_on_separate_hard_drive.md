---
title: "Installing dual boot on separate hard drive"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by zulubanshee on 2011-10-07
I have three hard drives, two of which are from an old computers and I'd like to install Ubuntu on one of them. I've burned the CD but it doesn't boot from the CD so I'll have to figure that out. 

When I do get it to boot, I'm not sure what I should do next. Will I be given the option to format the drive I want, which will be L: or D: I haven't decided which yet? 

Is there anything I should be looking for? I don't want to **** up my computer as it is. 

Can someone point me to some tutorials?

Added: Is there a way to do this without rebooting? Like with software that mounts CDs? Probably a long shot.

---

### Post by jtarin on 2011-10-07
You can unplug all drives but the one you want to install Ubuntu on, then install Ubuntu. The bigger question is what other operating systems do you want to run on the other drives? This will determine how you want to setup Grub boot loader at Ubuntu installation time.If your dual booting with Windows you might want to check the link in my signature on EasyBCD. It is not a boot manager nor does it overwrite you Win MBR. It is an editor for the Windows boot file. It will allow you to boot Windows and Ubuntu with Grub installed to the Ubuntu disk and not the Windows disk.

---

### Post by MontyMan on 2011-10-07
Here is how you make your computer boot the CD.  It's a method that works for most computers.  When you first turn the computer on, get your fingers over the <f2>, <f10>, and <del> keys.  At a certain point in the startup process, you need to press some key (probably one of these three) in order to go into BIOS.  The screen may quickly flash a message telling you which key, or you may have to experiment.  Once in BIOS settings, play around in the menu system until you find the boot options.  You need to make sure the CD comes before the hard disk in the boot sequence, in order to give it a chance.  Exit, saving changes, insert the Ubuntu CD, and try it again.
 
When Ubuntu CD boots, it will offer the option of "try Ubuntu" or "install Ubuntu."  Obviously you want to choose the install option.  It will not blow anything away and install itself without giving you the opportunity to choose which disk to use as a destination.
 
I hope you like Ubuntu.  I've been working in the Red Hat world so long that it is almost relaxing, because it is so easy to use, once you learn where things are.

---

### Post by wildmanne39 on 2011-10-07
Hi, jtarin gave you great advice.

When I installed ubuntu 11.10 it gave me the option of where to install grub and I chose the same hard drive that I installed ubuntu on that way if my other drive crashes I can still boot ubuntu.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

I have never used EasyBCD but when you install grub using ubuntu livecd to a 2nd drive and the other drives are disconnected you will need to boot ubuntu after you install it and run:
```
sudo update-grub
```unless you want to go into the boot menu when you boot up to choose which drive you want to boot from.

@jtarin is ```
sudo update-grub
``` needed with EasyBCD?
Thank you

---

### Post by jtarin on 2011-10-07
> **wildmanne39 said:**
> 
@jtarin is ```
sudo update-grub
``` needed with EasyBCD?
Thank youNo, as you install GRUB to the root of your Ubuntu partition then EasyBCD will find it when you point it to it.

---

### Post by wildmanne39 on 2011-10-07
Hi jtarin, thank you for letting us know, I figured that was the case since you did not mention it but I wanted to make sure so I could learn something if nothing else.

---

### Post by wackawacka on 2011-10-07
> **zulubanshee said:**
> I have three hard drives, two of which are from an old computers and I'd like to install Ubuntu on one of them. I've burned the CD but it doesn't boot from the CD so I'll have to figure that out. 

When I do get it to boot, I'm not sure what I should do next. Will I be given the option to format the drive I want, which will be L: or D: I haven't decided which yet? 

Is there anything I should be looking for? I don't want to **** up my computer as it is. 

Can someone point me to some tutorials?

Added: Is there a way to do this without rebooting? Like with software that mounts CDs? Probably a long shot.

ubuntu live can install on top of windows.  wasn't that one of your questions?  

it didn't feel right for me when i installed it in windows.

you want to partition (make space) your hard drive and give yourself at least 30GB to get a really good, "let me do what i do," experience.  grub is great with keeping up with current installations of windows.  if you screw up and have to revert to constant re-installs of ubuntu until you understand how to fix linux, you can safely do it because you allotted space to fool around with, like a workshop bench.  just make sure grub (which stays in your master boot record (mbr) even when you remove ubuntu) chooses windows as a default system so you have your other life on standby.  partition magic is a good software for windows.  

you won't see "L:" or "D:" in ubuntu installations, it's gonna speak to you in /dev/hda1 or /dev/sda1 or any hard drive device in the /dev folder.  this is easy.  just pay attention to the sizes of L and D and look for those sizes (in bytes, not MB) in a list provided to you and choose your size pertaining to the letter you chose and it'll look for space and install.  

tutorials are tricky to find.  this forum is awesome for my level because i can find what i'm looking for and move on quickly.  but i remember when i first started (this is a new account, forgot old) and this forum was too much information at one time.  it's like a harvard professor visiting an oakland elementary school and explaining math to the students.  haha

you want to google something like:

ubuntu howto
ubuntu install howto
ubuntu dual boot

do you get the idea?  be simple in your questions and google does a good job of providing suggestions.  but the trick is looking for websites that layout steps.  that's how you learn.  you can maybe post a thread for step by step instructions but the well versed will force the policy of independent achievement by telling you to look for the answer and while that policy is a great policy, as an economics major, i'm concerned with the dead weight loss that can be recouped by providing information catalysts like step by step instructions.  nothing says efficient learning like having a guide.  you don't do remodeling without a guide to follow.  

i'll shut up now.  haha

---

### Post by oldfred on 2011-10-07
If  you want lots of detail Herman's site has that, some beginners may think it is too much but it is useful:

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?

If you have multiple hard drives you should not need EasyBCD unless you  like it for some reason. You just install grub2's boot loader to the MBR of the drive you have installed Ubuntu into. Unless you have an old BIOS you can select that drive to boot from and grub will let you boot Ubuntu or Windows.

---

### Post by verymadpip on 2011-10-08
Hi zulubanshee.

I did the 2 OSs on 2 HDDs thing a while back.

Here's the thread just in case you need it.  I'm sure the info suggested already will be good enough.

[http://ubuntuforums.org/showthread.php?t=1706223](http://ubuntuforums.org/showthread.php?t=1706223)

Good luck & have fun :)

---

### Post by zulubanshee on 2011-10-15
OK I changed the boot sequence so the DVD boots first. Then I get the ubuntu screen and I think everything's good, and then it goes to a plain prompt. After that I get a looping message that says

udevd[152]: timeout: killing '/sbin/modprobe -bv pci<random looking string>[191]

---

### Post by zulubanshee on 2011-10-15
Adding: I tried already to install by wubi, but while I was able to install, when i rebooted to finish install I got another timeout error (I didn't write it down)

---

### Post by oldfred on 2011-10-16
When it does not boot from CD that is a concern.

Was ISO correctly downloaded. 
Was CD burned at slowest speed your CD writer allows.

Perhaps your system needs additional parameters. Often video needs nomodeset with nVidia but some need other settings also.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---

### Post by zulubanshee on 2011-10-16
It was indeed burned at the lowest speed. I have the 64 bit version, which matches my machine. But the machine is no longer booting from the CD anyway, even though I have set it to do so. I think I'll have to deal with that first.

---

### Post by oldfred on 2011-10-16
Sometimes CD gets lost if system has not been totally powered down or cold boot. I would try that first. Then check connnectors, sometimes they just come loose.

---

