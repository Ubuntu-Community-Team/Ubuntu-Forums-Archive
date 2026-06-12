---
title: "hi i need to install window xp pro"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by blake7 on 2008-11-25
can some one as hopeless as me do it with out to may problems and will it take long 
yea i like to give 10 gb of space just so that if i cant sovle a software problem then i can just have a sound back plan 

i hope you can help 

thank you

---

### Post by BDNiner on 2008-11-25
You should probably ask this question in the 'other OS' thread on this board. But from my experience. XP is pretty straight forward to install so long as you have a valid XP key. You just need to follow the prompts. The only confusing issue could be setting up the partitioning, but that can be confusing with any operating system. 

It can take under an hour from starting the install to having a usable system without any windows updates and no addition software, depending on your hardware. windows updates and the addition software will add at least an hour.

---

### Post by Paqman on 2008-11-25
Ok, we'll need a bit more info from you:

[LIST]
[*]Have you got Ubuntu installed already?
[*]Is your hard drive partitioned?
[*]Do you already have a copy of Windows installed?
[*]Do you have a bootable XP Pro install disk and a valid licence key?
[*]Do you want to set up a dual-boot system with Ubuntu, or to replace Ubuntu with Windows?
[*]Do you know how to restore Grub after installing Windows?
[*]Do you have all the disks of hardware drivers for your machine (eg: motherboard, graphics card, etc)
[/LIST]

---

### Post by Skripka on 2008-11-25
> **BDNiner said:**
> You should probably ask this question in the 'other OS' thread on this board. But from my experience. XP is pretty straight forward to install so long as you have a valid XP key. You just need to follow the prompts. The only confusing issue could be setting up the partitioning, but that can be confusing with any operating system. 

It can take under an hour from starting the install to having a usable system without any windows updates and no addition software, depending on your hardware. windows updates and the addition software will add at least an hour.

.......So long as you already have a ntfs partition to start with, getting drivers installed will add at least another hour to one's adventure.   If you choose the long format option, the formatting alone will take an hour or more depending on the size of your drive.

Be careful how you set things up--installing XP second can make things messy for bootloaders.

---

### Post by blake7 on 2008-11-25
ok thanks for your replies

ok i have ubuntu   8.04
the drive is not partitioned
yesi have ubuntu only on this hard drive (160gb)i have ibm x60s
yes i have a copy of xp with the key

yes i would like the dual boot (must of the time i be in ubuntu its just that odd moment that i need to go back to black(windows xp)

what is a grub??

   i do not have all the disks of hardware drivers for my machine (eg: motherboard, graphics card, etc)

---

### Post by Paqman on 2008-11-25
> **blake7 said:**
> 
   i do not have all the disks of hardware drivers for my machine (eg: motherboard, graphics card, etc)

Ok, that'll be your first job then. You'll need to make sure that you have those. The manufacturers of the individual components should have WinXP drivers available for download on their website.

The best thing to do would be to download all those drivers onto a disk, as well as a copy of Firefox and an antivirus suite like Avast. You don't want to connect Windows to the net before you've got your shields up. Other drivers like graphics can be downloaded after you've got the basic setup with security.

---

### Post by blake7 on 2008-11-25
is thier a list of all the driver i need or how do i find that out???

---

### Post by Skripka on 2008-11-25
> **blake7 said:**
> is thier a list of all the driver i need or how do i find that out???

This is why XP is a pain.


You need to know the serial number or name of each piece of hardware you have as well as what version, then go to each individual maker's site to find drivers for your specific device.  No shortcuts here. Audio drivers, wireless drivers, graphics drivers-are a minimum.

BEST advice-find it download it and SAVE ALL of it to a handy USB key or CD-so that when XP crashes (and it will), you don't have to go digging for all of it again.

---

### Post by BDNiner on 2008-11-25
you will need chipset drivers for your motherboard, video, network, and sound drivers to have a basic working computer. Do you have a name brand computer? or is it a custom built? We would need to know all your hardware to determine what drivers you need.

---

### Post by Paqman on 2008-11-25
> **Skripka said:**
> This is why XP is a pain.


^^This.

And people complain that Linux is hard to install. Windows is horrific, even if you already have all fifty disks.

If it's a laptop or a pre-built desktop you probably only need to know what model it is. Is there a sticker on it with the manufacturer and model number?

---

### Post by blake7 on 2008-11-25
no its an ibm x60s its a sweet lapto[p by the way

i have loaded xp on to a harf drive be fore i never had to do all that driver stuff.??
but i take your words for it and st at that pain in hte **** task now chheerrss

---

### Post by sydbat on 2008-11-25
My question is what do you need XP for? 

If it is simply to run one or two programs (not games), would using a virtual machine be a better set-up for the OP? Or trying WINE for things that might run through it?

Alternately, are there programs that are similar/the same for Ubuntu that you could use instead?

I am just asking these questions to help the OP not go insane if/when things go sideways...

---

### Post by Skripka on 2008-11-25
> **sydbat said:**
> My question is what do you need XP for? 

If it is simply to run one or two programs (not games), would using a virtual machine be a better set-up for the OP? Or trying WINE for things that might run through it?

Alternately, are there programs that are similar/the same for Ubuntu that you could use instead?

I am just asking these questions to help the OP not go insane if/when things go sideways...

My thoughts exactly.


The only time one should resort to having an full normal XP install is for having things run perfectly that won't otherwise be "close enough"--a few professional softwares come to mind, and lots of games.

---

### Post by Paqman on 2008-11-25
> **blake7 said:**
> no its an ibm x60s its a sweet lapto[p by the way

i have loaded xp on to a harf drive be fore i never had to do all that driver stuff.??
but i take your words for it and st at that pain in hte **** task now chheerrss

Well, you might have got lucky and had hardware that Windows could just use it's default drivers for. That's pretty unlikely for a laptop though.

[X60S Drivers and software page]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-62938") (Lenovo bought IBM's computer business a while back)

You'll need the all the networking, maybe power management, and definitely "Windows install supplements". Audio/card readers/PCMCIA slots and the like you can do later. I'd also like to reiterate my advice to have an antivirus suite and a browser ready to install *before* going online, especially if your XP disk is an old version. Windows can get infected within minutes online without the recent service packs and an antivirus system.

---

### Post by BDNiner on 2008-11-25
How is the install of XP going. You will need to reinstall grub when you repartition the drive to install XP since XP will use its own bootloader and render grub useless.

---

