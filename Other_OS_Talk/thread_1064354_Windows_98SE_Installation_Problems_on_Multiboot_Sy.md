---
title: "Windows 98SE Installation Problems on Multiboot System"
date: 2009-02-08
forum: Other OS Talk
---

### Post by dbsoundman on 2009-02-08
I'm working on setting up a multiboot system that will eventually have Windows 95, Windows 98SE, Windows 2000, and Ubuntu on it, in that order. Using the instructions on [this site (click for link)]("http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html"), I followed his steps, creating a [grub boot floppy (click for link)]("http://users.bigpond.net.au/hermanzone/p15.htm#grub_floppy_howto_make") with special options to mount the empty partitions, using the "chainloader (fd0)+1" option. I had no trouble getting Windows 98 setup started; I used a boot disk I created, which initialized the CD ROM driver, then began setup. The problem I'm having is where the setup program requires a computer restart. I can't seem to figure out how to get back to where I left off in the setup after the restart. If I use the boot floppy (since grub is temporarily wiped off the HD), it won't start up without a Windows 98 boot floppy in the drive, then it starts me back where I left off; I boot with the floppy, get the CD ROM initialized, change to the CD ROM drive, run setup. So does anyone know what workaround there is to getting this working? The first site I mentioned is my guideline for doing this, but he gives no details on how to actually install the OS. Any help would be appreciated; I have a feeling I will have this problem when I get around to Windows 2000 as well.

Thanks,
Dan

---

### Post by maybeway36 on 2009-02-08
When you reboot, I think you should boot to the partition you are installing Windows 98 SE into, but with the CD in the drive.

---

### Post by dbsoundman on 2009-02-08
I think I tried that, and it said there was a disk I/O error or something.

-Dan

---

### Post by Frak on 2009-02-08
IIRC, none of the 9x supported SATA. If your disk is SATA, that may be causing the I/O error. I don't see why you couldn't run it in a VM, since on a modern machine, even fairly modern (like 2002) would run 9x's like a beast.

---

### Post by dbsoundman on 2009-02-08
The computer is actually all IDE; it's a 2001 Dell Workstation 420. I could run a VM, but I wanted to setup an old-school PC for old games basically, sort of a living room entertainment piece. So I'm still not sure what the error is about...

-Dan

---

### Post by maybeway36 on 2009-02-08
Using a VM is too easy! :)

---

### Post by saulgoode on 2009-02-08
VMs typically have rather poor performance with 16-bit OSes. Instructions are interpreted rather than executed. Certainly this has been my experience running 98SE in VirtualBox. It works, but at a crawl.

---

### Post by Frak on 2009-02-08
> **saulgoode said:**
> VMs typically have rather poor performance with 16-bit OSes. Instructions are interpreted rather than executed. Certainly this has been my experience running 98SE in VirtualBox. It works, but at a crawl.
Works fine in Parallels (you can get it from the Ubuntu/Canonical partner repository) and VMWare Workstation for me. Virtualbox is just god awful at 16-bit OS's.

---

