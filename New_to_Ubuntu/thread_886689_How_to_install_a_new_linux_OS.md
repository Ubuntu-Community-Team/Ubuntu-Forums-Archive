---
title: "How to install a new linux OS?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by appi2012 on 2008-08-11
I have some extra space on my hard drive, and was wanting to try out linux mint (I think ubuntu is awesome btw) Can I just install it to the free space? Is the installer similar to the ubuntu one? 

I also noted that linux mint comes with grub gfx. If I install it, and for some reason it fails, can I somehow get my ubuntu grub back? How would I do that. Also, if you recommend not installing grub gfx, how can I skip that step? 

Thanks in advance!

---

### Post by tech9 on 2008-08-11
> **appi2012 said:**
> I have some extra space on my hard drive, and was wanting to try out linux mint (I think ubuntu is awesome btw) Can I just install it to the free space? Is the installer similar to the ubuntu one? 

I also noted that linux mint comes with grub gfx. If I install it, and for some reason it fails, can I somehow get my ubuntu grub back? How would I do that. Also, if you recommend not installing grub gfx, how can I skip that step? 

Thanks in advance!

you want to download the latest ISO and burn it to a CD as an image (ISO) - Then boot up your PC with your the new CD that you created... You can install mint from the liveCD... let me know if you have any more questions.

also, you can try to repair your ubuntu grub with supergrub disk

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by mahela007 on 2008-08-11
I,m pretty sure you can get brub back but as I'm not much of an expert on partitioning and harddrives , I dont know whether it will erase the data on your harddrive. you should however be able to install it one the extra harddisk space.
like the previous post said you can use supergrub disk to repare your grub. believe me.. its totally easy. I did it once and it was extremely easy to find help. Just be sure to back up data before you do any installing

---

### Post by WRDN on 2008-08-11
> **appi2012 said:**
> I have some extra space on my hard drive, and was wanting to try out linux mint (I think ubuntu is awesome btw) Can I just install it to the free space? Is the installer similar to the ubuntu one? 

I also noted that linux mint comes with grub gfx. If I install it, and for some reason it fails, can I somehow get my ubuntu grub back? How would I do that. Also, if you recommend not installing grub gfx, how can I skip that step? 

Thanks in advance!

Linux Mint uses a LiveCD, like Ubuntu, so you will be able to identify any problems before installing. You may want to use a partition editor such as GParted to create a partitiono from the free space, then install Linux Mint on this.
An alternative to this is to run Linux Mint in a Virtual Machine. This way, it is completely isolated from the rest of the system (as it uses a virtual hard drive), you will be able to try it out, and find any issues.

---

### Post by kansasnoob on 2008-08-11
> Can I just install it to the free space? Is the installer similar to the ubuntu one? 

Yes and yes. One difference in the live CD is that it does not show the "options" screen when you boot the live CD, it automatically goes for running the live CD with no changes to the hard drive ....... you want that anyway.

If everything seems fine running the live CD then open Gparted (aka, Partition editor) and make sure you have at least 8GB of unpartitioned space available (I recommend at least 10GB or more but 8GB will work), then just double click the installer icon on the desktop and it's identical to the Ubuntu installer.

> If I install it, and for some reason it fails, can I somehow get my ubuntu grub back? 

Yes! Create a backup of your menu list:

```
sudo gedit /boot/grub/menu.lst
```

I just copy & paste mine into a word document using Abiword and put it where I can find it. Just pay attention to which drive/partition your Ubuntu grub is on.

Then if you decide to remove Mint just boot the live CD, use Gparted to get rid of Mint, then open the terminal and:

```
sudo grub
```

Then in sequence:

- root (hdx,y)
- setup (hdx)
- quit
- exit 

NOTE: x = drive# and y = partition# ............. and you know what they are because you wrote it down from your menu list!

Then you can boot into Ubuntu again (not the live CD) and either edit your menu list or just replace it with the copy you made earlier.

---

### Post by .nedberg on 2008-08-11
If you are just going to try out a new OS, the I recommend using a virtual machine. VirtualBox is fine and in the repos! If you want to see if it runs on your hardware and maybe switch, then a liveCD and then dualboot is better for you.

---

### Post by sandysandy on 2008-08-11
mint is nothing but a derivative of ubuntu.

u can just add repositories to ur ubuntu to make a MINT machine. 

more or less:)

regards

---

### Post by philinux on 2008-08-11
Why not just run the live cd and see if you like it.?

It didn't work out for me.

---

### Post by bobnutfield on 2008-08-11
You can install any Linux you want and boot it from your existing Ubuntu Grub.  When you are asked to whether or not to install a bootloader, say no or uncheck the box or whatever the option is.  For Linux Mint, you simply click on Advanced and uncheck the box that says "Install Bootloader".  Then just edit you /boot/grub/menu.lst file to boot the new OS.  Make sure you put the entry BELOW the "End of Debian Kernels" line so that it will not be edited when you update Ubuntu.  

It is a very simple entry to edit the menu.lst file and you will not have to reinstall Grub.

---

### Post by bobnutfield on 2008-08-11
> **philinux said:**
> Why not just run the live cd and see if you like it.?

It didn't work out for me.

+1 to that.  My Ubuntu install is not performing very well, so I thought I would install Mint.  I think this is the first distro that actually performed BETTER from the live cd than it did after I installed it.  Beware if you have an ATI graphics card and you install the prop. driver.

---

### Post by kansasnoob on 2008-08-11
I'm running Mint in a triple boot with XP and Ubuntu. Mint does have trouble keeping up with the Ubuntu updates. I love the Desktop but if you leave the Mint Update tool set to install level 3 (or higher) updates it breaks!

If you run sudo apt-get update it breaks! If you select Reload and Mark all Upgrades in synaptic and install them it breaks!

This is why Mint Elyssa is still running Kernel 2.6.24-16 instead of 2.6.24-19 like Hardy. The most recent thing to break my Mint was an xulrunner update.

But I love the desktop!

---

### Post by bodhi.zazen on 2008-08-11
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

