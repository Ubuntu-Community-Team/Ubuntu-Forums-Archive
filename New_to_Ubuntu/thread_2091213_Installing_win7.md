---
title: "Installing win7"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by Robert1305 on 2012-12-04
I run Ubuntu 12.10, and I wouldnt change it for the world, I thought I had finished with win for ever but now I find that I need to install Win7 to run side by side with Ubuntu.

What I want to know is... do I just put the Win7 disc into my PC and tell it to run alongside Ubuntu, or is it more complicated than that, please don't blind me with science.:):)

Regards Bob

---

### Post by TheFu on 2012-12-04
Do you want to dual boot or run Windows inside a virtual machine?

Dual booting is a little more dangerous, but running inside a virtual machine requires more hardware - CPU, RAM, and probably 30-60GB HDD storage just for the Win7 VM.  If you don't plan on gaming or don't need specific hardware support for a peripheral, then the virtual machine option is much less risky, easier to deal with (IMHO) and very flexible.  The VM also means you can easily move it do completely different hardware without having to contact Microsoft for licensing stuff.

I don't dual boot anymore - haven't in 10+ yrs, but I do use VMs all the time. VMs are extremely flexible.

---

### Post by mlentink on 2012-12-04
I'd recommend to install VirtualBox, and then install Win7 in a virtual machine. 

Or does your machine have low specs?

---

### Post by COMECON on 2012-12-04
Dual booting isn't so difficult. When I have to reinstall Windows, I just install as I did with Ubuntu. 
When the Windows installer asks you to partitionate, you can create a new partition with the free space you have on the disk (if you have), or just decrement the Ubuntu partition space and assing the other space to Windows.
After the installing process, you'll have to download **Super GRUB Disk 2** and burn it on a CD. Boot from it, and select "Detect Any OS". On that menu, boot Ubuntu.
When you booted Ubuntu, open a Terminal and run:
** $ sudo grub-install /dev/sda && sudo update-grub **
(If /dev/sda isn't your MBR, change it)
Then it will install GRUB, the boot loader, and you'll be able to restart and, now, without the Super GRUB 2 CD, you'll see again GRUB, where you can choice between Ubuntu and Windows.
I hope it helped you, if you have any other question just ask!
Catbuntu

---

### Post by Robert1305 on 2012-12-05
> **mlentink said:**
> I'd recommend to install VirtualBox, and then install Win7 in a virtual machine. 

Or does your machine have low specs?

I have installed VB as per the wizard, but when I click on start I get this message/

[IMG]http://i229.photobucket.com/albums/ee246/robert1305/Screenshotfrom2012-12-05103652.png[/IMG]

Where do I go from here please.

Regards Bob

PS/ It is an high spec PC.

---

### Post by black veils on 2012-12-05
you need to click **new** instead. the wizard will help you through setup.

Edit: sorry i realise you did this. thats strange.

---

### Post by TheFu on 2012-12-05
> **Robert1305 said:**
> I have installed VB as per the wizard, but when I click on start I get this message/

Where do I go from here please.

Regards Bob

PS/ It is an high spec PC.

Did you connect the Win7 Installation ISO to the VM and tell it to boot from the DVD?
Also, before you go too far, be certain to setup your VM to get the most performance. Otherwise, VM performance can really, really, really, suck.

---

### Post by Robert1305 on 2012-12-05
Thank you all for the help you gave me.
I now have VB up and running, I had to install Win XP cos it wouldn't accept my 64bit Win7 disc.

How many VBs can you run on one PC, cos I have different versions of Linux I would like to experiment with.

Thanks again, Regards Bob.:P:guitar:

---

### Post by jdmgwaka89 on 2012-12-05
You can access them separately if you install Windows and then re-install Ubuntu. When you reboot after that, you should have an option to boot from either Windows or Ubuntu.

---

### Post by black veils on 2012-12-06
the limitation is your hard drive space. and if you want to run more than one at a time, you will want plenty of RAM.

---

### Post by Robert1305 on 2012-12-06
> **black veils said:**
> the limitation is your hard drive space. and if you want to run more than one at a time, you will want plenty of RAM.

HiBV, I shall only be running one O/S at a time although I do have TB (is that right)HD? and 6meg of ram.

The only problem I have is I cant access the internet in Win, although it tells me I have a connection when I look in the control panel. I have tried resetting the connection but it keeps telling me you have a connection. ???????

Regards Bob

---

### Post by Mark Phelps on 2012-12-06
Actually, if you're going to use a VM, you'll be running TWO OSs at a time -- the native one, and the one in the VM.

Dual-boot setup is different in that you boot to a single OS and only run it.

This is why, unless you have a really fast processor and lots of high-speed RAM, I generally advise against using VMs.

---

### Post by XXYZGuy on 2012-12-06
Hello,

I have a theory, it might even work,  if you have a spare HDD load that with Windows 7 as a boot, leave your other HDD the same as is, when you turn your computer on  select 'exit boot menu' or whatever words to that effect, and select whatever drive it is you have that you want to boot with. 

I'll be doing that on my other  computer, not this one, I have 5 bootable HDD's   it shouldn't be much of a problem finding one, spare. ;)

Good luck.

> **Robert1305 said:**
> I run Ubuntu 12.10, and I wouldnt change it for the world, I thought I had finished with win for ever but now I find that I need to install Win7 to run side by side with Ubuntu.

What I want to know is... do I just put the Win7 disc into my PC and tell it to run alongside Ubuntu, or is it more complicated than that, please don't blind me with science.:):)

Regards Bob

---

### Post by TheFu on 2012-12-06
> **Mark Phelps said:**
> Actually, if you're going to use a VM, you'll be running TWO OSs at a time -- the native one, and the one in the VM.

Dual-boot setup is different in that you boot to a single OS and only run it.

This is why, unless you have a really fast processor and lots of high-speed RAM, I generally advise against using VMs.

My advice is vastly different.  Anyone with a Core2Duo or better and 4GB of RAM can run multiple OSes inside virtual machines just fine.  Almost anything that works fine in the HostOS will work fine in the client (VM) OS.  The VM doesn´t see any real hardware. All hardware is virtual and usually the most popular hardware available, so it is extremely well supported by the clientOS.

If you run high-end graphical games, dual booting is the best answer. For almost any other purpose, using a VM is much easier, offers much greater flexibility and much lower risk to your other OSes. You do not need to repartition your HDD to run another OS inside a VM. If you are going to dual or triple (or more) boot, then you will need to repartition. That is a little risky in my book.

If you cannot wrap your head around running 1 OS inside another, then dual booting is probably best.

---

### Post by Robert1305 on 2012-12-06
> **TheFu said:**
> My advice is vastly different.  Anyone with a Core2Duo or better and 4GB of RAM can run multiple OSes inside virtual machines just fine.  Almost anything that works fine in the HostOS will work fine in the client (VM) OS.  The VM doesn´t see any real hardware. All hardware is virtual and usually the most popular hardware available, so it is extremely well supported by the clientOS.

If you run high-end graphical games, dual booting is the best answer. For almost any other purpose, using a VM is much easier, offers much greater flexibility and much lower risk to your other OSes. You do not need to repartition your HDD to run another OS inside a VM. If you are going to dual or triple (or more) boot, then you will need to repartition. That is a little risky in my book.

If you cannot wrap your head around running 1 OS inside another, then dual booting is probably best.

Hi TF,

I totally agree I don't find many problems running Win7 on a VM, and if it wasn't for the fact that my internet connection is not working properly I wouldn't have a single problem.

Regards Bob

---

