---
title: "Sticky suggestion"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by newb85 on 2012-09-20
*It seems all-too-common that new users aren't making an informed decision about how to install Ubuntu with Windows, and the resulting setup is often not what they want or non-functional.  I suggest a sticky.  My proposal needs editing, and someone else should write the up side for the Wubi installer, as I'm having trouble coming up with anything but snyde remarks and sarcastic comments.*

So, you have a machine with Windows, and you'd like to install Ubuntu.  Before you begin installing, it's important that you choose the right installation approach.

1. Boot from a Live CD or USB and run the installer. This will place Ubuntu on its own partition. You will have the choice to run either Windows or Ubuntu when you power up your machine, assuming you install alongside Windows.  This is the tried-and-true method.
The up side: Other than harddrive space, each system will have access to all your machine's resources.  The two systems are independent, so if one becomes unbootable, it shouldn't affect the other one.
The down side: You have to reboot the machine to switch between systems.

2. Run the Wubi installer in Windows. This will place Ubuntu on the same partition as Windows. Again, you will have the choice to run either Windows or Ubuntu when you power up your machine. 
The up side: ???
The down side: Ubuntu is a slave to Windows, using the sub-optimal NTFS.  If Windows is ever removed or becomes unbootable, Ubuntu will become unbootable, too.  On newer systems (the ones that use UEFI instead of MBR), Ubuntu often won't load because Wubi doesn't support UEFI.  Moreover, Wubi's lead developer has stated that it was designed for experimental installs, not long-term installs.


3. Install on a Virtual Machine (VM) using a client like VirtualBox ([www.virtualbox.org](www.virtualbox.org)). A Live CD or USB will work, or you can simply point to the ISO. It will be installed on a virtual HD within Windows. You will have to run Windows and your VM client in order to boot Ubuntu.
The up side: Switching between systems is really easy.
The down side: While you're running Ubuntu, the two systems will be competing for resources.  Again, if Windows becomes unbootable, so does Ubuntu.

---

### Post by drmrgd on 2012-09-20
Possibly not a sticky as many new users might not know this forum and won't think to check here.  But, a link or something to the Community Documentation (which has to be kept up to day on a regular basis I would guess) on how to dual boot near where the Ubuntu .iso is located would probably be super helpful.  This way, when new users want to download and install Ubuntu, they'll have a good approach right there at the same time and may be able to stave off problems right off the bat.

---

### Post by newb85 on 2012-09-20
Ideally, this info would be available on the download website.  However, I don't even know how to suggest that.

---

### Post by philinux on 2012-09-20
> **newb85 said:**
> Ideally, this info would be available on the download website.  However, I don't even know how to suggest that.

Main info is here.

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

