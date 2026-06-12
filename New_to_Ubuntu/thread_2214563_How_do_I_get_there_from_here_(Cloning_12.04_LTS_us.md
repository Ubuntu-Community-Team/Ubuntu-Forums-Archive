---
title: "How do I get there from here? (Cloning 12.04 LTS using external HDD)"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by flyfishingphil on 2014-04-02
I have used Ubuntu for a few years now and have usually installed then gone thru the complete copy, paste routine to transfer files from one version/computer to the next. I've spent some time now looking thru the files but don't seem to be having much luck on finding the info I am after.

Here's what I have:
1 Maxtor 160 GB external drive
1 Seagate 1TB external drive (3 partitions)

I want to save my entire system from my Toshiba L305 laptop so I can transfer that into a desktop. (Trading with my son the lap for the desk)

In the first partition I think I have the entire Win7 file (don't like it but will use it) Seriously considering dropping all Windo$ again and just using Ubuntu but there are some places that Win is needed to operate properly. Transferring the entire Ubuntu file to a second partition on the Seagate is what I really need but would accept help with both. I'll gladly format everything that is on the Seagate and start over at step one if that is the better way to go.

I have seen several discussions but none of them start where I need it to start. Little things like "Turn the computer on" help a lot! Not looking at copying everything to DVD's then doing a total re-install if not needed.

Does anybody have any suggestions where I can find a "for newbies" step-by-step set of instructions for doing a clone of the entire system so I don't have to do the full install of the 12.04, all of its update, then start copying and installing file after file? Looked at Clonezilla but didn't see one that identified as being the workable version for the 32 bit 12.04LTS. Is there something better, easier to use? Where do I find it or what version is best of Clonezilla for my system?

BTW, another question: Since I already purchased a smaller laptop that is 64 bit capable and the desktop is 64 bit capable, would I be better off to just go the old fashioned way and do a full upgrade/install to 64 bit? Does it make that much difference?

Thanks for any assist.

---

### Post by Double.J on 2014-04-02
Hi there! 

I would say first thing is to back up everything - your whole laptop hdd and desktop onto the external hard drives. Before attempting to clone anything, make sure absolutely everything is on the other hard drives. Also make sure those external drives are not connected in any way to a computer when you do get down to cloning. 

With this kind of thing it's best to start at the back. The actual disk cloning comes last. Back up first and then see what the hardware situation is.

now there's another element here - disk cloning means just that; two identical disks. Ubuntu is pretty darn good at being pulled from one intel/amd computer and being shoved into another. Windows is not quite so resilient. Does your laptop have a nice little removable panel on the back? If so I would recommend removing the laptop hard drive from the laptop, plugging it into the desktop and double checking that it will boot as is on the desktop.

there is no point waiting hours to days to clone a hard drive block by block, just to find out you'll have to reinstall windows anyway? Also if the laptop hard drive is connected to the pc, it is easier and faster to clone the disks.

IMPORTANT
when opening up computers practice electrical safety - make sure you are grounded, not wearing things like nylon, and then disconnect from the mains power supply, disconntect the laptop battery, then pres the power button several times to dissipate charge. It is very very unlikey that you would cause yourself any harm, it's mostly to protect your computer from you.

---

### Post by Double.J on 2014-04-02
Just one quick gotcha:

when backing up all your data onto hose external's, make sure it is a drag and drop backup. You should always have at least one drag and drop backup. If you use an imaging backup such as windows disk backup there is always a minimal chance of corruption or if you use disk imaging like clonezilla there's that slight chance you accidentally get it backwards and wrote the blank drive over the full one.

sorry if it sounds like scare mongering, It's a mixture of personal experience (10 years of using linux and just a month ago i accidentally installed a test os over another one; mistakes happen) and having seen so many people on the support pages who have made those catastrophic slips using clonezilla and dd

jj

---

### Post by flyfishingphil on 2014-04-03
Thanks for the info and, now that I'm operational, I'll save it so it's there next time I do this. Turned out I didn't need it for what I wanted to do. The old laptop is a 32 bit and the new one is 64 bit. Started out at ground zero and put everything together in the 64 bit zone.

Thanks again.

---

