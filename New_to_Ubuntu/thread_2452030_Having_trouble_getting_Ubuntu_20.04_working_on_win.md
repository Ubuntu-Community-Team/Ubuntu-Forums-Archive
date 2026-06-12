---
title: "Having trouble getting Ubuntu 20.04 working on windows 10"
date: 2020-10-15
forum: New to Ubuntu
---

### Post by rcwd21 on 2020-10-15
I'm new here and have spent probably a good 4 hours trying to get ubuntu 20.04 lts (and several other versions) working on my windows 10 laptop in order to gain access to the syscon on game consoles to repair them. It requires ubuntu and python to access the system via a ttl converter cable. My cable has a PL2303 chipset.

I've tried so many "tutorials" and tips and hints that I could find on the internet that my brain is fuzzy now.

My biggest issues are I'm unable to get anything related to usb to open up. I'll either get an error message or it'll just give me another blank starting line like when you first open ubuntu.

I've gone through powershell to enable everything and as far as I'm aware everything took correctly.

---

### Post by nnn1308 on 2020-10-15
When you install  ubuntu 20.04 lts from DVD or USB(memory ot HD),  onto other USB HD, I recommend you to select [other] when you select target install device.

 [other] 
 It doesn't change your local devices.
For example,
If the external (target ) USB HD is /dev/sdd,
MBR =>  /dev/sdd
INSTALL => /dev/sdd2   (just example.)

PC power on
[ESC]  or proper key to show boot device select menu.
&#8593;&#8595; select USB HDD (/dev/sdd)
[ENTER]

You would get ubuntu 20.04 lts from menu (*1) .
If you want to use WIN10, it's available from the menu(*1) too.
When WIN10 is up,  open firefox (or edge, chrome) to search [ WIN10 fix MBR] .

Personally, I usually backup mbr like,
sudo dd if=/dev/sda of=mbr_sda.img count=63 bs=512    # in case WIN10's mbr is on /dev/sda
before new installation.

If you want to edit boot menu from ubuntu command line,
grub-customizer is convenient.

#  sudo add-apt-repository ppa:danielrichter2007/grub-customizer 
sudo apt-get update
sudo apt-get install grub-customizer


[https://askubuntu.com/questions/1243113/how-do-i-install-grub-customizer-on-ubuntu-20-04](https://askubuntu.com/questions/1243113/how-do-i-install-grub-customizer-on-ubuntu-20-04)
> What happens is the ppa doesn't support Ubuntu Focal, so you need to remove the external first.
> sudo add-apt-repository --remove ppa:danielrichter2007/grub-customizer
> sudo apt update

> The good news is, grub-customizer exist on default repository.

> sudo apt install grub-customizer



.... sorry if my comment is not to the point.

---

### Post by Impavidus on 2020-10-15
In what sense do you try to get Ubuntu running on Windows 10? Is this a Windows 10 computer where you want to install Ubuntu alongside Windows, dual booting? Or do you intend to run Ubuntu on a virtual machine inside Windows? In that case, configure the virtual machine to give Ubuntu access to the relevant port on the real machine. Or are you referring to Windows Subsystem for Linux? That's a partial Linux environment on Windows that I don't know much about.

---

### Post by oldfred on 2020-10-15
If you have UEFI Secure boot on, your USB ports are normally blocked as booting another system is not secure.
You typically then have additional settings to allow USB boot or allow full USB support in UEFI. You need  to turn that on, but often better to also turn off UEFI Secure Boot.

---

### Post by rcwd21 on 2020-10-15
I would like to be able to run it along side windows so I can just boot up my laptop like usual and operate in Ubuntu via virtual machine (I went through powershell in windows to switch wsl from 1 to 2 and as far as I can tell it should be in wsl 2 now)

I installed Ubuntu via the Microsoft store, it opens and operates fine but I'm having issues with having it access anything related to the USB ports.

---

### Post by CelticWarrior on 2020-10-15
A Virtual Machine - WSL is different - may work as commented above but it's harder than a bare metal installation. And for what you want to do not recommended because the USB connected boards often disconnect during firmware load operations and others. When it happens the device will bounce back to the host and you have to pass it again and again to the guest.

WSL, on the other hand, doesn't even work for the type of hardware access needed.

So, either install Ubuntu alone, as a dual-boot or, if you're masochist then try a virtual machine.

---

### Post by rcwd21 on 2020-10-15
> **CelticWarrior said:**
> A Virtual Machine - WSL is different - may work as commented above but it's harder than a bare metal installation. And for what you want to do not recommended because the USB connected boards often disconnect during firmware load operations and others. When it happens the device will bounce back to the host and you have to pass it again and again to the guest.

WSL, on the other hand, doesn't even work for the type of hardware access needed.

So, either install Ubuntu alone, as a dual-boot or, if you're masochist then try a virtual machine.

I've looked into it more and I've decided to go the dual boot route. It seems easier, more stable, and safer as I won't really get things mixed up.

---

### Post by nnn1308 on 2020-10-16
grub-customizer

I need to fix my previous entry.

[https://askubuntu.com/questions/1243113/how-do-i-install-grub-customizer-on-ubuntu-20-04](https://askubuntu.com/questions/1243113/how-do-i-install-grub-customizer-on-ubuntu-20-04)
> What happens is the ppa doesn't support Ubuntu Focal, so you need to remove the external first.

> sudo add-apt-repository --remove ppa:danielrichter2007/grub-customizer
> sudo apt update

> The good news is, grub-customizer exist on default repository.

> sudo apt install grub-customizer

---

### Post by rcwd21 on 2020-10-16
Ok so I found that the task im trying to do with the game consoles is able to be run on pretty much any version of linux/ Ubuntu so after digging around I've decided to go with Linux Mint as it seems to be based on Ubuntu but its more user friendly for beginners.

I was able to made a dual boot USB and install it on a shrunken partition on my ssd. It installed successfully so all thats left is to update everything.

Once I get that done and if I have any more problems I'll post back on here.

---

### Post by CelticWarrior on 2020-10-16
> [COLOR=#000000]I've decided to go with Linux Mint as it seems to be based on Ubuntu but its more user friendly for beginners.[/COLOR]
It is not.

> [COLOR=#000000]Once I get that done and if I have any more problems I'll post back on here.[/COLOR]
No, you may post at their forums or here only in the section dedicated to other OSes. The main sections are only for Ubuntu and official derivatives. Linux Mint is not one of them.

---

