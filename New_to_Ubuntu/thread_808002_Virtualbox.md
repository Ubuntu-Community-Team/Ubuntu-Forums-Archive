---
title: "Virtualbox"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by nilsolaris on 2008-05-26
I have now installed virtualbox and the modules.. but when i go to run virtual box i get this error:

You are not a member of the "vboxusers" group.  Please add yourself
         to this group before starting VirtualBox.

	 You will not be able to start VMs until this problem is fixed.

What is this vboxusers group?:S

---

### Post by SlappyPappy on 2008-05-26
Go to terminal, type: groups.

You should see a group labeled: vboxusers.

If you don't, add it in System/Administration/Users and Groups.

Good luck.

---

### Post by nilsolaris on 2008-05-26
Thanks for the reply, figured out the vboxusers problem, yet now i keep getting the error: "No bootable medium found! System halted"

---

### Post by Joeb454 on 2008-05-26
Go to System > Administration > Users and Groups

Then add yourself to the vboxusers group :) Then start up VirtualBox again :)

---

### Post by damis648 on 2008-05-26
> **nilsolaris said:**
> Thanks for the reply, figured out the vboxusers problem, yet now i keep getting the error: "No bootable medium found! System halted"

This just means that there is no OS installed on the guest HDD, no bootable CD mounted in the virtual machine, or no guest hdd installed.

---

### Post by overdrank on 2008-05-26
> **nilsolaris said:**
> Thanks for the reply, figured out the vboxusers problem, yet now i keep getting the error: "No bootable medium found! System halted"

HI and I do not have VB installed at the moment but you may check under details of the virtual machine and make sure the cd drive is enabled.

---

### Post by nilsolaris on 2008-05-26
Im not booting through a cd, ive been trying to boot this through an ISO.

---

### Post by Joeb454 on 2008-05-26
Open up virtual box, make sure you have a virtual machine configured (so you have the virtual hard drive set up etc.)

Then before you click start, click settings, and then CD/DVD ROM, then mount an iso image in that. Once that is done you can start the Virtual Machine.

I hope that was clear ;)

---

### Post by nilsolaris on 2008-05-26
Thanks for all the help:) Just out of curiousity, what runs more smooth between VirtualBox, Qemu and VMWare? Im am running xubuntu 8.4 and trying to virtualize Windows Ultimate XP for mainly music production programs... Reason 4, Adobe Audition, Fruity Loops.

---

### Post by Joeb454 on 2008-05-26
I've never tried VMWare under Linux, though Virtual Box runs just fine for me :) (I'm running Ubuntu 8.04 64 bit :))

---

