---
title: "extend persistent live cd partion"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by Nick_Dyer on 2014-03-16
Hi there,

I have a live ubuntu cd and i used the universal usb installer from pendrivelinux.com, and the file system has almost no data. It seems to not want to open any files anymore either. I'm lucky I got the terminal and chromium open. any suggestions? I can't open system settings either. Last i checked it said i have somewhere around 5 kb of full storage, and i cant see any files in any folders. It also says there is nothing at all in the file system.

---

### Post by sudodus on 2014-03-17
If your computer boots from USB, I suggest that you use a live USB pendrive. Instead of a casper-rw file you can have a casper-rw partition, which will not be limited in size. Another alternative is to install Ubuntu into the USB pendrive (a regular installation, but to USB). Such a system will be more stable than a persistent live system, and completely upgradable, while the kernel cannot be upgraded in a persistent live system.

See this link for more details

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Nick_Dyer on 2014-03-17
I boot it off of a usb and the problem is I can only access the terminal and chromium, but sudo doesn't work on the terminal.

Sorry, i dont know how to paste as code 

nickedy123@ubuntu:/$ sudo -s
sudo: >>> /etc/sudoers: /etc/sudoers.d: Input/output error near line 30 <<<
sudo: parse error in /etc/sudoers near line 30
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin

I can't do anything without sudo to fix it

**Edit: **any sudo command won't work,

---

### Post by sudodus on 2014-03-17
Did your system work from USB before, but now it does not work because it is full? Do you think that the space for persistence, the casper-rw file is full?

In that case it is probably possible to remove some files, that are filling the system, or in the worst case, remove the whole space for persistence and create a new one or restore from backup.

It might be easier to do that when booted from another drive, but maybe possible also from the same drive, if you remove the boot option persistent and reboot.

Or am I misunderstanding? Is there almost no data, meaning that there is too few data, so that the system is not complete? In that case I suggest that you use some other method to create the persistent live system, for example Unetbootin. See this link

[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

- What computer is it (brand name, model and specs)?
- Which version of Ubuntu are you running?
- Are you creating the system in Windows or linux?

---

### Post by C.S.Cameron on 2014-03-17
First, forget Universal, (from pendrivelinux).
Use Startup Disk Creator from the Live CD, it was made for Ubuntu.
Or try UNetbootin, it is easy to use.
Both use casper-rw for persistence. 
You can use the included casper-rw file or as Sudodus said make a casper-rw partition, (ext4), if you need more than 4GB persistence.
If you want to see what is on root of the drive go to filesystem/cdrom in terminal.

---

