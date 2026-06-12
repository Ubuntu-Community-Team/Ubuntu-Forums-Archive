---
title: "Windows XP using VMware Server"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by panand178 on 2008-07-06
I have managed to install windows XP using VMware Server successfully. However, I have a few questions/queries. 

1. I assume that as for an actual machine I will have to install all the drivers for sound, graphics card, network etc to get those working right? However when i tried installing the drivers from the motherboard CD i got the following error:

[ATTACH]76597[/ATTACH]

2. How do I access files/folders from my other drives from within this virtual XP?

---

### Post by frankos44 on 2008-07-06
On MAC you install VMware tools. What is the host machine?

---

### Post by panand178 on 2008-07-06
> **frankos44 said:**
> On MAC you install VMware tools. What is the host machine?

Sorry i forgot to mention that earlier. I've installed VMware server on Hardy.

---

### Post by cariboo on 2008-07-06
You don't need  to install any drivers as in a normal windows install, because everything is run virtually. IF you check in Control Panel-->System-->Device Manager you will see that the hardware has no relation to what your motherboard is. Check here to get soud working:

 [http://ubuntuforums.org/showthread.php?t=6332](http://ubuntuforums.org/showthread.php?t=6332)

post #4

Everything else should work without drivers. For networking set it for nat.

Jim

---

### Post by gate on 2008-07-06
A virtual machine uses the Linux drivers and translates them to fake devices that Windows understands. If you want it to run better, look in the menus for "Install VMWare tools." This will give you a better running system and install the windows drivers needed for some of the fake hardware to run better (sound, video etc).

 There are allot of advantages to doing it this way, so GL!

EDIT:
  FYI: VMWare Server runs a virtual machine. VMWare Tools runs *inside* the virtual machine.

---

### Post by panand178 on 2008-07-07
> **gate said:**
> A virtual machine uses the Linux drivers and translates them to fake devices that Windows understands. If you want it to run better, look in the menus for "Install VMWare tools." This will give you a better running system and install the windows drivers needed for some of the fake hardware to run better (sound, video etc).

 There are allot of advantages to doing it this way, so GL!

EDIT:
  FYI: VMWare Server runs a virtual machine. VMWare Tools runs *inside* the virtual machine.

From where do I install VMware tools? I was not able to see any VMware Tools installables on the VMware website.

---

### Post by superprash2003 on 2008-07-07
vmware tools option would be in your vmware software window itself.. in one of those menu options

---

### Post by hyper_ch on 2008-07-07
power off your virtual machine, edit it's property and add the sound device ;)

---

### Post by panand178 on 2008-07-07
> **superprash2003 said:**
> vmware tools option would be in your vmware software window itself.. in one of those menu options

> **hyper_ch said:**
> power off your virtual machine, edit it's property and add the sound device ;)

Thank you! I have installed VMware tools and also added the sound device to the properties and it is working fine now. 

Now I need to setup SAMBA server to be able to share files between the Ubuntu host and guest XP.

I also had another query. Initially when I installed my virtual machine my only intention was just checking out how windows XP functions as a virtual machine inside ubuntu. Hence i allocated only 2 GB of space for Windows XP installed on the virtual machine. Is there any way i can increase the disk space of windows XP? If this is not possible and i need to remove the current XP and install a new version with more disk space, do i just delete the folder for the virtual machine from "/var/lib/vmware/Virtual Machines"?

---

### Post by superprash2003 on 2008-07-08
first remove the machine in vmware.. and then remove the directory

---

### Post by panand178 on 2008-07-08
> **superprash2003 said:**
> first remove the machine in vmware.. and then remove the directory

Hmmm... So in short i will have to delete my current XP and re-install it again to increase the allocated partition size. :( 

I think i will let it run for as much i can push it before deleting it. 

I am having a couple of other issues with my VMware.

1. If there is some song or something playing on my host Ubuntu I get this message when i launch XP using vmware. 

> Failed to open sound device /dev/dsp: Device or resource busy
Virtual device sound will start disconnected.

Once I get this error message the only way for me to enable sound is to power off the virtual machine and re-launch it making sure that no application in ubuntu is currently using sound. Is there any other work around for this?

2. My Ctrl and Shift keys get locked up when I am on vmware and it either just stops working or keeps shutting down the current active window or application in ubuntu. Currently i have found out a workaround for this by having a launcher created for "setxkbmap" and launching it whenever my keys start acting weird. But is there any other more generic solution for this?

---

### Post by frankos44 on 2008-07-10
I had great success with VirtualBox !

---

