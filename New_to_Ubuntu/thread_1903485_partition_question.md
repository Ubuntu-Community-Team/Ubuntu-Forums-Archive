---
title: "partition question"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by chris1216 on 2012-01-02
All,

I have a netbook with a 150 GB hard drive.  I would like to install two or maybe three operating systems.  I have been reading up on how to partition the drive, but I am confused; if I make two partitions and install two versions of Ubuntu will their boot up protocols be confined to the partition I install them to? 

Chris

---

### Post by ratcheer on 2012-01-02
No, usually the boot manager of one will control the booting of the other and any additional OS's that are installed. For example, I have Ubuntu and Arch installed on mine. The grub2 installation on Ubuntu controls the booting of both. If I were to install more OS's, I would still use Ubuntu's grub2 to manage their booting.

Tim

---

### Post by GreenRaccoon on 2012-01-02
I don't completely understand your question.  You will be able to choose between all of the operating systems on your computer when it starts up, if that's what you're worried about.  When you say "boot up protocol", I think you're referring to GRUB, which is what you first see when you start up your computer, after the hardware logo screen (when you can choose which operating system or kernel to boot).  GRUB will be overwritten anytime that the kernel is changed in one of your Linux partitions.  It's not that big of a deal when this happens, but if you've customized GRUB (background, colors, etc.), you might lose those customizations.  It'll still work fine though.

You might want to look at a couple threads I created when I was trying to figure out how to create multiple Linux partitions:
[http://ubuntuforums.org/showthread.php?t=1872283]("http://ubuntuforums.org/showthread.php?t=1872283")
[http://ubuntuforums.org/showthread.php?t=1873849]("http://ubuntuforums.org/showthread.php?t=1873849")

Make sure you keep a Live USB or CD on hand in case you have problems booting up.  Then you can use the Live disk to fix it; that's what I did.

Also, you only need one Linux swap partition.  Since only one Linux operating system runs at one time, all of your Linux partitions can use the same swap partition.

---

### Post by cortman on 2012-01-02
When you go to install your second or third operating system, you just need to be sure to select "Install alongside" or edit the partition table manually, which isn't hard at all and you'll be able to find plenty of advice about.
The bootloader from the OS that was installed the last is the default one for all OS's.

---

### Post by GreenRaccoon on 2012-01-02
Here's the walkthrough I used to manually create partitions (which is what you should probably do).  It's very thorough.
[http://members.iinet.net.au/~herman546/p23.html]("http://members.iinet.net.au/~herman546/p23.html")

---

### Post by chris1216 on 2012-01-02
Thank you guys.  I guess part of what I am asking is it is possible to have each OS use its own GRUB?  GreenRaccoon, I will start reading those threads right now.

---

### Post by cortman on 2012-01-02
> **chris1216 said:**
> Thank you guys.  I guess part of what I am asking is it is possible to have each OS use its own GRUB?  GreenRaccoon, I will start reading those threads right now.

No, not really- what would be the practical use of it? If you want to ensure that everything will boot regardless what OS shenanigans you do, you can install grub to the MBR, which won't be affected by OS shuffling.

---

### Post by I_can_see_the_light on 2012-01-02
> **chris1216 said:**
> Thank you guys.  I guess part of what I am asking **is it is possible to have each OS use its own GRUB?**  GreenRaccoon, I will start reading those threads right now.

Yes.
You need to install the bootloader (GRUB) to the root partition instead of master boot record for **all but one** of your distros. You can then chainload into the bootloader of the distro you want to boot. I can't recall the exact procedure but it should be fairly simple with a bit of googling.

---

### Post by chris1216 on 2012-01-02
Green Raccoon those were helpful tutorials to read.  I will google "chain boot loaders" and see what I find.

---

