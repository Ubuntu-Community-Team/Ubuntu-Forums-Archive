---
title: "[SOLVED] Installing within windows"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by gettinoriginal on 2008-06-04
I did a search, but cannot seem to find this information.  What are the advantages/disadvantages to installing Ubuntu "within" windows vs doing a dual boot.  Thanks,

---

### Post by Duck2006 on 2008-06-04
> **gettinoriginal said:**
> I did a search, but cannot seem to find this information.  What are the advantages/disadvantages to installing Ubuntu "within" windows vs doing a dual boot.  Thanks,

It run faster as a dual boot than running it from within windoze.
To install it from within windoze this link may help.

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by bumanie on 2008-06-04
I don't think there are any advantages as such. I think wubi has emerged so that some people who are not confident with partitioning/dual booting can try ubuntu. If they like it enough they may decide to dual boot later. The install inside windows is very large - 15gb and it works slightly slower than it does off a dedicated partition. I think it gives some the opportunity to try ubuntu when they would not necessarily go to all the trouble of dual booting. It's also very easy to install, ie just like any other windows program - easier than dual booting, easier than setting up a virtual machine.

---

### Post by aysiu on 2008-06-04
Of course there are advantages (and disadvantages), the biggest one being that you can easily switch back and forth without rebooting your computer.

Try this:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by temaki on 2008-06-04
I thought that installing Ubuntu within windows was dual booting?  I chose that option and now have Vista and Ubuntu available on my laptop.  What's the other method of dual booting?

---

### Post by Duck2006 on 2008-06-04
> **temaki said:**
> I thought that installing Ubuntu within windows was dual booting?  I chose that option and now have Vista and Ubuntu available on my laptop.  What's the other method of dual booting?

or VMWare or with a Qemu file from within win.

[http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/](http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/)

---

### Post by housam on 2008-06-04
> **aysiu said:**
> Of course there are advantages (and disadvantages), the biggest one being that you can easily switch back and forth without rebooting your computer.

+ No resizing or partitioning.
Disadvantages : when windows crashes ( always happen ) you loose the both systems.

---

### Post by meindian523 on 2008-06-04
> **temaki said:**
> I thought that installing Ubuntu within windows was dual booting?  I chose that option and now have Vista and Ubuntu available on my laptop.  What's the other method of dual booting?

THE method of dual booting is repartitioning your hard drive to make space for Ubuntu/any other OS.What you have done is told Ubuntu to make a virtual space for itself **within** an existing partition and work from ther.

---

### Post by aysiu on 2008-06-04
> **temaki said:**
> I thought that installing Ubuntu within windows was dual booting?  I chose that option and now have Vista and Ubuntu available on my laptop.  What's the other method of dual booting?
There are three options available here for installation: [list][*]**Dual-boot with Ubuntu's boot loader**. This is the traditional dual-boot method, where you boot the Ubuntu CD, amd click the *Install* button on the desktop. [*]**Dual-boot with Windows' boot loader.** This is Wubi or "install Ubuntu within Windows." It allows you to create Ubuntu as a large file and removable program within Windows without repartitioning, and then it adds Ubuntu to Windows' boot loader (or boot.ini file). [*]**Ubuntu as virtual machine within Windows**. This uses VirtualBox or VMWare to install Ubuntu as an operating system that launches up as a window inside of a booted Windows session. So you don't have to reboot your computer to switch between the two. You're essentially always booted into Windows, but sometimes you also have a mini-Ubuntu session open inside of Windows.[/list]

---

### Post by Paqman on 2008-06-04
The speed loss from using Wubi is very marginal, to the point of being barely worth mentioning.

I don't see any major disadvantages with Wubi. Maybe it'd be slightly more awkward to reinstall and preserve data/settings, but there's always the upgrade option.

The advantages for first-time users however are huge. The Wubi install process is laughably easy. So unless you've got a burning desire to learn about partitioning at this point i'd say go for Wubi. There's a lot more useful topics on the newbie learning curve (eg: package management, file permissions, the CLI). You can always learn about disk partitioning and mounting partitions on your next install.

---

### Post by aysiu on 2008-06-04
The major disadvantage for Wubi is that you have to still have Windows.

Some people know they don't want Windows any more and want to wipe it right out. Others (a far likelier scenario) may start with a dual boot and want to easily switch over to Ubuntu-only later.

If you move from a regular dual-boot to a sole-Ubuntu installation, it's easy to do - just remove the Windows entry from /boot/grub/menu.lst and reformat the NTFS partition and add it as storage. If you want to move from a Wubi dual-boot to a sole-Ubuntu installation, you'll have to reinstall.

---

### Post by avtolle on 2008-06-04
To go from a Wubi install to a permanent install, there is LVPM, which will allow the existing Wubi Ubuntu install to be made permanent. See the Wubi forum page sticky for more information. This eliminates the need to reinstall Ubuntu and update it to where the user wants it. Just something to consider, too.

---

### Post by Paqman on 2008-06-04
> **aysiu said:**
> The major disadvantage for Wubi is that you have to still have Windows.

Hmm, having the option to boot another OS is really only a disadvantage if you *really* need the disk space.

> 
If you want to move from a Wubi dual-boot to a sole-Ubuntu installation, you'll have to reinstall.


Not so. LVPM will migrate a Wubi virtual partition to it's own partition quite happily. No reinstall required.

---

### Post by temaki on 2008-06-04
> **aysiu said:**
> There are three options available here for installation: [list][*]**Dual-boot with Ubuntu's boot loader**. This is the traditional dual-boot method, where you boot the Ubuntu CD, amd click the *Install* button on the desktop. [*]**Dual-boot with Windows' boot loader.** This is Wubi or "install Ubuntu within Windows." It allows you to create Ubuntu as a large file and removable program within Windows without repartitioning, and then it adds Ubuntu to Windows' boot loader (or boot.ini file). [*]**Ubuntu as virtual machine within Windows**. This uses VirtualBox or VMWare to install Ubuntu as an operating system that launches up as a window inside of a booted Windows session. So you don't have to reboot your computer to switch between the two. You're essentially always booted into Windows, but sometimes you also have a mini-Ubuntu session open inside of Windows.[/list]


Thanks, that makes sense :) and why is there a 30GB limit for the install ?using Wubi?

---

### Post by Paqman on 2008-06-04
> **temaki said:**
> 
-and why is there a 30GB limit for the install using Wubi?

No idea. However, if you're store your data on another partition 30GB will be more than enough for even the fattest Ubuntu system.

---

