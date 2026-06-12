---
title: "How do I get UBUNTU on Aspire One?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by bobkat205 on 2008-10-14
I have a new aspire one which has linpus on it and I am told that I would be better off with ubuntu. I went to the site to download it and it indicates that I have to download to a CDROM. The aspire one does not have a CDROM reader. Is it possible to download to an sd Card. Or is there another option?

























?

---

### Post by Nxion on 2008-10-14
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Try this link.

Nx

---

### Post by bobkat205 on 2008-10-19
Thank you. I tried to download Ubuntu as described on that websight but I couldn't install it. I have been trying for two days. I sure missing XP.

It doesn't describe the ubuntu that i downloaded. It mentions something called UNetbootin?? and SYSLINUX.CFG that isn't in my ubuntu and I DON'T KNOW HOW TH CHANGE IT IF I found it.

I tried booting with the SD but it didn't.

---

### Post by palinode on 2008-10-19
I've always run into trouble trying to install from an SD card. I recommend that you install from a USB flash drive, using the program Unetbootin (you mentioned that you were having difficulties with Unetbootin, but it's the easiest and most reliable method I've encountered if your computer doesn't have a DVD/CD drive).  Instructions for downloading, installing and using Unetbootin can be found here: [http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Using_Unetbootin](http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Using_Unetbootin)

Note that the instructions on that link are for installing Ubuntu to an Asus eee, not the Aspire, so some details aren't going to work - for example, you don't want to download the ISO for the eee-tweaked Ubuntu; instead you'll want the standard desktop ISO available from the main Ubuntu site.

If you're not used to the Linux environment at all, I recommend that you create the bootable USB drive on a Windows machine.  All you need to do on Windows is download Unetbootin, download the ISO, plug the USB drive into the computer and then run Unetbootin.  The interface is simple and easy to navigate.

I also recommend that you try the beta version of 8.10 instead of 8.04.1.  The wireless and the sound work right out of the box in 8.10.

---

### Post by nothingspecial on 2008-10-19
Download Ubuntu as you normaly would from the Ubuntu home page.
Download unetbootin
Format your usb stick to FAT32
When you open unetbootin select Ubuntu Hardy or which ever version you`ve got.
Point it to the iso image of Ubuntu that you have downloaded.
Point it to your usb stick
Let unetbootin work it`s magic.
Reboot your aspire.
Before it loads press what ever button it tells you to in order to get into the bios or change boot order.
Put boot from usb drive at the top of the list.
The usb stick should then load exactly like a live cd
Install as normal.
I seem to remember it helps if you have a wired internet connection during this process.
Sorry if this is a bit vague but I`m not in the same place as my aspire.

---

