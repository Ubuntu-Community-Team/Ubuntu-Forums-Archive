---
title: "Unable to install Ubuntu 11.10"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by jackn703 on 2011-11-07
I have almost no experience with Ubuntu.
I am trying a clean install of 32 bit Ubuntu 11.10 on a new HP Pavilion p7-1120 using the instructions [here]("http://www.ubuntu.com/download").
The installation seems to start up nicely; it asks if I want to try or install Ubuntu and I select install.
It seems to start the installation, there is a nice Ubuntu splash screen and sounds but then the display gets funny, but its hard to describe. 
I have tried installing from both CD and bootable USB stick but get similar behaviour.
The system is connected to the internet via Ethernet in case updates are needed.
It was asking for an "Other..." username and password but I don't know what that would be since I haven't created any accounts.
When I clicked in the thing that looks like a gear the username/password request went away and left a gray box in its place.
The rest of the screen is fancy violet with "ubuntu 11.10" in the lower left hand corner, but it will go no furthur.
The mouse seems to be happy but I'd like to do more than push an arrow around.
Could the 64 bit Windows 7 which was originally loaded on this PC be interfering with the installation?
Is the HP Pavilion p7-1120 a bad choice for Ubuntu 11.10?
What do I need to do to complete this installation.

_HP Pavilion p7-1120 Specs_
Processor: Intel Core i3-2130 3.4 GHz, DMI 5GT/s
Chipset: Intel H61
Memory: 8 GB DDR3
HD: 1.5 TB SATA
Optical drive: SuperMulti DVD Burner
Graphics: Intel HD Graphics (up to 1.69 GB)
Video connectors: 1 DVI; 1 VGA
Network interface: On-board 10/100/1000Mbps Gigabit Ethernet
Viewsonic VX2450WM-LED 24-Inch Widescreen HD 1080p LED Monitor

---

### Post by Exonimus on 2011-11-07
Just a shot in the dark here, but might that be the dialogue box that actually asks you to PROVIDE a username and password for your new box? As in, set a new one for future use? Would not be surprised if setup does not continue before you entered that.

Also, another OS shouldn't really be able to make any difference whatsoever during ubuntu installation

---

### Post by goldshirt9 on 2011-11-07
can you run a live session

---

### Post by Tri-Booter on 2011-11-07
Where did you download the ISO image from? To me it sounds like you are at the Login screen not the installation setup.

---

### Post by Exonimus on 2011-11-07
> **Tri-Booter said:**
> Where did you download the ISO image from? To me it sounds like you are at the Login screen not the installation setup.

Also crossed my mind. Could you describe what you see exactly?

---

### Post by jackn703 on 2011-11-07
> **Exonimus said:**
> Just a shot in the dark here, but might that be the dialogue box that actually asks you to PROVIDE a username and password for your new box? As in, set a new one for future use? Would not be surprised if setup does not continue before you entered that.

Also, another OS shouldn't really be able to make any difference whatsoever during ubuntu installation

I don't think so since it only asks for PW once before declaring "invalid password; please try again."

---

### Post by jackn703 on 2011-11-07
> **Exonimus said:**
> Also crossed my mind. Could you describe what you see exactly?

I see a nice violet screen with white dots on it, a text box that says "Other...  Invalid password; please try again" and a white :ubuntu 11.10" in the lower left hand corner.

---

### Post by critin on 2011-11-07
Sounds like the login screen to me.  How did you install without answering the questions and creating a username and password?  strange...;)

Did you see it installing, or did this screen come up almost immediately?  Is it a freshly downloaded image?  It sounds like it was i**nstalled on **the usb so it can be used from the usb.  Probably not, but the symptoms are there.

edited to add:  Did it get to the screen where you choose how and where to install it?  Did you see the disk info?

---

### Post by weezyrider on 2011-11-07
I've had that happen when booting into recovery mode in Grub. It will run and at the last it wants a name and password. I've used the name I set up Ubuntu with, and recovery doesn't like that. 
Won't take it. Tells me invalid.  

What I'm wondering is could this be hooked to something for a main password for the computer? From the BIOS or whatever?

I have 2 hard drives and the XP one has never had a password. I might password my account, but not the whole computer. But Grub is controlling access to that drive.

---

### Post by critin on 2011-11-07
Try running a live session and then open Gparted to look at the disk info.  See where it installed to.   The partition number:  sda1?  how large is the disk it installed to?  Make sure it wasn't the usb.  This may sound silly but it happens.  :P
> 
The system is connected to the internet via Ethernet in case updates are needed.

I wouldn't update until after the installation.

---

### Post by jackn703 on 2011-11-08
I believe Ubuntu wasn't getting installed based on the fact that Windows 7 is still on this machine. So rather than blow away the original Windows 7 OS I installed Ubuntu using wubi. This should work for me. Still can't say why it wasn't installing clean but I'm good for now.

---

### Post by audiomick on 2011-11-08
Windows 7 shouldn't interfere. What could be a problem is that the Windows install already had 4 partitions on the drive, so the installer can't create one for the Ubuntu install.

I have to admit, though, that the behaviour you describe doesn't really sound like that is the problem.:confused:

---

### Post by danny1994 on 2012-09-12
I've seen this. 
Just use "ubuntu" or "Ubuntu" as user/PSW
:lolflag:

---

