---
title: "Need to know: addl Red Hat/Fedora as a tri-boot"
date: 2007-07-18
forum: Other OS Talk
---

### Post by Browser_ice on 2007-07-18
On my PC I have a dual boot Win-XP and Ubuntu 7.04.  Due to possible office project involvements with Red Hat or Fedora, I am thinking about the possibility of installing either one on my PC as a tri-boot.

Running Red Hat/Fedora install, will it safely and automaticaly be installed as a tri-boot or will I have to do manual stuffs (if so, what ?)  ?

Could I install either as the latest version or will I have to go with specific versions ?

What would be the possible problems I may or will encounter if I go ahead with this ?

Doing it, I will have to re-use one of my Win-XP partition. I only have one linux partition and its for Ubuntu.

---

### Post by igknighted on 2007-07-18
> **Browser_ice said:**
> On my PC I have a dual boot Win-XP and Ubuntu 7.04.  Due to possible office project involvements with Red Hat or Fedora, I am thinking about the possibility of installing either one on my PC as a tri-boot.

Running Red Hat/Fedora install, will it safely and automaticaly be installed as a tri-boot or will I have to do manual stuffs (if so, what ?)  ?

Could I install either as the latest version or will I have to go with specific versions ?

What would be the possible problems I may or will encounter if I go ahead with this ?

Doing it, I will have to re-use one of my Win-XP partition. I only have one linux partition and its for Ubuntu.

I would look at CentOS as a possibility as well.  CentOS IS red hat, just free.  They remove the red hat logo's and thats it.

No matter what you go with, if you use anaconda to partition space (the red hat/fedora installer) and do the install normally, it will ask you where to install grub (if at all).  The easiest option would probably be to install grub to the partition red hat/fedora is on and add a chainloader line (just like the windows partition).  This way when red hat/fedora updates a kernel it will update its grub and Ubuntu's will obviously update its own, and there will be no worries about updating manually past adding the first chainloader line.

---

### Post by Browser_ice on 2007-07-18
> **igknighted said:**
> ... and add a chainloader line (just like the windows partition).  This way when red hat/fedora updates a kernel it will update its grub and Ubuntu's will obviously update its own, and there will be no worries about updating manually past adding the first chainloader line.


Sorry, but you lost me there. I'm a part time Linux Noob.

---

### Post by igknighted on 2007-07-18
> **Browser_ice said:**
> Sorry, but you lost me there. I'm a part time Linux Noob.

Sorry.

The grub entry line that boots windows uses the command chainloader.  Basically this means that Windows has a bootloader on its own partition.  The GRUB bootloader merely points to that bootloader and lets it take over.  You can do the same to another linux distro.  If you choose to install GRUB from Fedora/Red Hat onto the partition (NOT the MBR... in other words (for example) to /dev/sda3 instead of /dev/sda), then you can copy and paste the windows entry in your Ubuntu's /boot/grub/menu.lst file (use sudo to open it, then copy/paste the entry right below windows).  Change the title to something that will identify Fedora (or Red Hat), thats just for display so you know, it doesn't really matter what you call it.  Then you need to change the partition to point to the one with the fedora/red hat bootloader instead of Windows.  Then save and exit.  Now on reboot you chould get to choose.

If you install Fedora's to the MBR it will write over Ubuntu's.  Which is OK, it should configure Ubuntu as a boot option, but if you update the Ubuntu kernel you will need to manually update the GRUB entry to the new Ubuntu kernel.  The first method will save you work in the long run.

If you tell us the partition structure and paste the /boot/grub/menu.lst file we can help you set it up.

---

