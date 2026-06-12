---
title: "HP Officejet Pro 8600 - Cannot print from Win XP VM"
date: 2013-08-13
forum: New to Ubuntu
---

### Post by Shallowmind on 2013-08-13
Hello,
I recently got a new printer (HP Officejet Pro 8600). I got it connected to Ubuntu 12.04 without too much trouble (though it had to be through a cable not wirelessly, it will not "pick up" the printer wirelessly:().  


I had a Brother MFC 8440 printer that never one time showed up in Win XP VM.  However my new HP printer shows up as being connected to USB port.  When I click on it in the status bar there is a check by it.  But I still cannot print from the VM.  No printer shows up in the control panel for printers.  When I try to install it with the wizard it will not really install.  What can I do to solve this problem?  Thanks in advance!

Matt

---

### Post by NM5TF on 2013-08-13
R U running XP under VirtualBox???
do you have the "guest additions" installed???
I assume your HP is connected to a USB port

if so, you might want to check out this link:

[https://www.virtualbox.org/manual/ch03.html#idp10920688](https://www.virtualbox.org/manual/ch03.html#idp10920688)

I also run XP under Vbox and my HP deskjet F4180 works flawlessly after
I followed the suggestions in the above link...

good luck,

Tommy

---

### Post by Shallowmind on 2013-08-15
Yes I am running XP in VirtualBox.  I think I have guest additions installed?  And yes connected to a USB port.  I will check out the link and see what I can do, thanks for your help.

---

### Post by Shallowmind on 2013-08-15
OK.  So yes guest additions are installed.  When I open XP in VB the printer shows up in "devices" at the top of the screen and in the USB icon in the tool bar at the bottom of the screen.  The computer (XP) then indicates that there is new hardware and ask me to install it (with a wizard).  When I try to do this it will not recognize the printer, and shows no printer in the "printers and faxes" section of the control panel.  Also the wizard keeps popping up several times for me to install the printer and a mass storage device (which is not currently connected).  

Any help is appreciated, thanks.

---

### Post by Mark Phelps on 2013-08-15
> and a mass storage device (which is not currently connected)

If your 8600 has either USB ports or memory card readers, those are considered mass storage "devices" and Windows will install drivers for those.

---

### Post by NM5TF on 2013-08-15
> **Shallowmind said:**
> OK.  So yes guest additions are installed.  When I open XP in VB the printer shows up in "devices" at the top of the screen and in the USB icon in the tool bar at the bottom of the screen.  The computer (XP) then indicates that there is new hardware and ask me to install it (with a wizard).  When I try to do this it will not recognize the printer, and shows no printer in the "printers and faxes" section of the control panel.  Also the wizard keeps popping up several times for me to install the printer and a mass storage device (which is not currently connected).  

Any help is appreciated, thanks.

it's been a couple of years since I installed XP in VB.....seems like I had to download
the drivers from either M$ or HP while XP was running.....sorry can't be more specific...

Tommy

---

### Post by Vladlenin5000 on 2013-08-15
You need to install the printer in the same way you'd have to in a standalone Windows XP OS. Unlike your other Brother printer the HP OfficeJet Pro 8600 ISN'T natively supported in XP (maybe it is in Vista or newer but certainly NOT in XP). As such you need to either download and run or run from the CD - in the VM, obviously - the proprietary drivers&software provided by HP. A few advices:
1. Do NOT connect the printer to the VirtualBox Windows XP before installing the drivers&software; keep it (physically) connected to the host OS ready to be added to the VM.
2. Run the HP drivers&software installer.
3. Using the VirtualBox menus as usual connect it to the running Windows XP  IF AND ONLY IF the installer requests that; if not just let the installation finish and "reboot" your Windows CP VM; after rebooting connect the printer and then it'll be recognized and properly installed by Windows XP.


Obs.: Your question has NOTHING to do with Ubuntu/Linux or even virtualization/VirtualBox. Your question reveals you don't know how to install such printer in Windows XP.

---

### Post by Shallowmind on 2013-08-16
> **Vladlenin5000 said:**
> Obs.: Your question has NOTHING to do with Ubuntu/Linux or even virtualization/VirtualBox. Your question reveals you don't know how to install such printer in Windows XP.


You are more than likely absolutely correct in saying I don't know how  to install the printer in WIndows XP.  However I've never had trouble in  the past installing printers into WXP or other Windows computers.  And I  am indeed a noob with Ubuntu/Linux.  Best I can tell though the VM  doesn't even notice that I have inserted the CD into the drive.   Whatever the case the VM XP is not very happy on my computer.

Thanks for your suggestion I will give them a try.  Of course I don't  know how I can have the printer physically connected to the computer and  not be connected to it.  YES very confused.

Thanks

---

### Post by Petro Dawg on 2013-08-16
> **Shallowmind said:**
> Hello,
I recently got a new printer (HP Officejet Pro 8600). I got it connected to Ubuntu 12.04 without too much trouble (though it had to be through a cable not wirelessly, it will not "pick up" the printer wirelessly:().  

... 

Matt

As far as your wireless issue on Ubuntu, if you haven't already, you might try installing HPLIP from the software center and make sure you have the printer actually connected to the network.  HPLIP is pretty good at doing most of the install work automatically.

I never used a VM, so can't help you with your XP issues.

---

### Post by Shallowmind on 2013-08-16
Thanks to everyone for your help.  I used a combination of all the replies above to figure it out.  

What I did wasforgot about it being a VM "in" my linux and just went on the internet and downloaded everything I needed.  Interestingly enough I can now print wirelessly from XP but it has to wired to print from Ubuntu.  But I'm still happy.

Thanks

---

