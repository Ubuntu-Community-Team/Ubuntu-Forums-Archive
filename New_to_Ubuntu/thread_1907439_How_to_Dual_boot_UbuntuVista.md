---
title: "How to: Dual boot Ubuntu/Vista"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by justmott on 2012-01-11
I have done a search of the forum and was unable to locate a thread that addressed my specific issue.  I installed Ubuntu 11.10 about a month ago.  I need to figure out how to create a partition for Vista and install it so I can run my machine as a dual boot.  I don't intend to use Vista often but I will need it occasionally for school, therefore I am hoping I won't need a huge partition for vista.  Any help would be greatly appreciated.

---

### Post by mlentink on 2012-01-11
Have you looked [here]("https://help.ubuntu.com/community/WindowsDualBoot") at all?

---

### Post by Double.J on 2012-01-11
> **mlentink said:**
> Have you looked [here]("https://help.ubuntu.com/community/WindowsDualBoot") at all?

+1 in terms of dual booting anything that applies to vista, applies to 7 ;)

as the link says, please back up - consider it not an optional extra 

As a rough guide windows need about 40GB+data 

All the best!

---

### Post by Mark Phelps on 2012-01-11
Sorry ... wrong material...  

You need to boot from an Ubuntu CD or a GParted LiveCD and shrink down your partition(s) to leave room for Windows.

Don't create a new partition, just leave the space empty.

Then, when you boot from the Vista install DVD, just select the empty space and allow the installer to do the formatting.

---

### Post by anewguy on 2012-01-11
If i read your post correctly, you currently only have ubuntu installed but now also want to ADD vista as dual boot.  If you have no free space left on you drive you will need to do several steps to dual boot, so i would suggest instead to just install virtualbox and the extension pack from oracle's site as it would be much easier. First we  should  be sure your hardware will support it.  So, please answer these questions:

What are the specs of your PC?

Is your vista 32 or 64 bit

Are you running 32 or 64 bit ubuntu


That should give us enough to go on to help you.  A virtual machine is much easier than adding windows for dual boot on an existing ubuntu installation.

Dave ;)

---

### Post by QIII on 2012-01-11
+1 for virtualization.  If you only need it occasionally, don't go through a great deal of pain.  Everything you probably want for general school work will be just fine.

---

### Post by buckyaustin on 2012-01-11
Ok these guys do seem to be giving good advice when it comes to virtualbox, but what is your school work?

I'm learning java and c# plus many others.... but i hate c# since it means i need to use windows to test out my programs... I spend alot of time on windows this way, and if I virtualise windows I will create alot of problems for myself.For one, the speed of the virtualised OS is terrible as i have to run the bulky visual studio... So for my school work i have to dual-boot.... 

so basicly wat im saying is what is your school work.... cause we can't give advice without knowing your situation....

---

### Post by justmott on 2012-01-11
Ok so here are my specs:

Sony VAIO vgn-nr220e
Intel® Pentium® Dual Core processor T2330 (1.6GHz1 )
160GB2 hard drive and 1GB RAM

I am running Ubuntu 11.10 32-bit and the Vista backup I have is also 32-bit.

I am in my second year of a Information Systems degree, just getting into the hands on stuff this coming semester.  I know I will need to access Windows for many of my courses.  I may rehab a pavilion desktop that has a fried motherboard and make it a dedicated windows machine for school if dual booting this machine becomes a problem.  Thanks for the comments.

---

### Post by anewguy on 2012-01-12
Should work fine for virtualization.  When you set up the virtual machine, give it about 1/2 your memory (512mb) or a little more if possible.  I'm not sure what the minimal memory requirements are for Vista.

I also have something that might help you that you can have for free - a 1gb ddr2-533 (pc2-4200) sodimm for your laptop.  I noticed the specs said 1 gig, 2 gig max.  So, with your 1 gig, depending on the configuration, you could end up doubling your memory.  This would also help so that you could dedicate a lot more memory to the virtual machine - and that will definitely help.  If you're interested, PM me with your name/address so I can send it to you.

Dave ;)

---

### Post by lolpenguin on 2012-01-12
Dual-booting Windows and any other OS with the other installed first is a pain, because Windows always assumes it is the only OS on the computer and overwrites the boot sector, so you can't boot into Ubuntu unless you reinstall your bootloader.

Windows is VERY memory heavy. 1GiB for 32-bit, 2GiB for 64-bit (although Windows Developer Preview works with 256MiB...).

---

### Post by Mark Phelps on 2012-01-12
lolpenguin is right about the Windows memory demands.  You'll have a hard enough time getting Vista to run decently with ALL of the 1GB of memory available.  If you install a VM and allocate only half of that to Vista, it's likely to be so slow as to be unusable.

I had an XP laptop that I upgraded to Vista, and it had only 512MB (which worked fine with XP), and it was so slow, it was painful.  When I upgraded that to 1GB, it finally became usable.  When I later upgraded that to 2GB, it became pleasant.

Also, you DO understand that you have to install from scratch with a VM, right?  So, if you're installing afresh anyway, might as well just do it to a true dual-boot and be able to use ALL the memory when you're running Vista.

---

### Post by QIII on 2012-01-12
Now that you have said what you will be studying, I withdraw my virtualization suggestion, regardless of the specs of your machine.  You will probably be best served by a hardware instllation of windows because you can't count on virtual hardware to genuinely test a bona fide Windows installation.  I multiboot for just that reason.  I need to test that things work in a physical environment.

---

### Post by anewguy on 2012-01-12
I was just trying to skip over the inevitable question of "I installed Vista for dual boot and now I don't see Ubuntu at all".  I didn't know Vista was such a memory hog, so, unless you want to take me up on my memory offer, install for dual boot since at least then Vista will have the full 1gb to work with.

Obviously you'll need to do things like shrink your existing installation, install Vista, come back and have someone tell you how to run update-grub from the livce, etc., or you could make you life easier and back up everything you need from Ubuntu, blow it away with a full Vista install, then shrink the Vista partition (Mark Phelps posted instructions for that already), install Ubuntu and restore your backup.  

Either way around, be sure to backup EVERYTHING you need before you start.  I'm not sure about actually shrinking the size of an existing Ubuntu partition, but I'm sure it's going to involve the livecd, so I'd have that handy before I start as well.

I'll leave you in Mark Phelps' more than capable hands - he's a very knowledgable user!

Dave ;)

---

### Post by buckyaustin on 2012-01-17
If you have lost grub, you need to use a live cd again and install grub, thats it.... 
when i say grub, i mean the option to boot ubuntu

this happens when u install windows after a linux OS.... windows changes the MBR to only suit itself.... Linux trys to suit everyone....

---

### Post by anewguy on 2012-01-17
Hence my previous post........

---

### Post by buckyaustin on 2012-10-18
There are many solutions to this on Ubuntu forums, there is also many ways to solve this. I haven't been on this for a long time so sorry for posting now. Hope you found the solution. You also should mark this as solved after adding a link to one of the solutions of getting grub to work again.

---

