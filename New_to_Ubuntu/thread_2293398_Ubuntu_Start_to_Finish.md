---
title: "Ubuntu Start to Finish"
date: 2015-09-04
forum: New to Ubuntu
---

### Post by John_Shea on 2015-09-04
Can someone provide the steps to download, install, and have Ubuntu running from my USB Drive from my Windows 7 machine. Like to install the latest version.

---

### Post by cariboo on 2015-09-04
You can start by downloaded the latest stable version from here:

[http://releases.ubuntu.com/15.04/](http://releases.ubuntu.com/15.04/)

Then follow these instruction to create a bootable usb device:

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Make sure to set your BIOS to boot from USB, I won't give instructions for that, as there are so many different ways to do it.

Then boot from your newly created usb device and follow the prompts. Make sure to read each screen carefully, and make sure you understand them before going to the next screen.

There is a step by step guide with screenshots here:

[http://www.linuxtechi.com/installation-steps-ubuntu-15-04-screenshots/](http://www.linuxtechi.com/installation-steps-ubuntu-15-04-screenshots/)

---

### Post by Aidan_Owen on 2015-09-06
If you're looking to have Ubuntu running on your computer for a long time without needing to update to a new version, download [14.04 LTS]("http://releases.ubuntu.com/14.04/"). Otherwise, download [15.04]("http://releases.ubuntu.com/15.04/"), which will be supported for around 5 more months. After that point, you'll need to update to the latest version of Ubuntu to continue to receive security updates, whereas 14.04 will be supported almost until 2020. Once you've decided which version you'd like, download it (it takes around half an hour for me) and save it.

Next, you'll want to format your USB as FAT32. To do so, disconnect all USB media drives from your PC to prevent formatting the wrong drive (!), connect the USB drive to your computer, go to Computer/My Computer, right-click the drive and select Format from the menu.

When I make my Live USB drives, I use [UNetbootin]("http://sourceforge.net/projects/unetbootin/"). It's free to download and very easy to use. Once you've downloaded it, click the box next to ISO, then click the ellipsis (...) and browse to your downloaded ISO. Select it and click **OK**. It will take a while to format and set up Ubuntu on there, so be patient. Once it is done, click Reboot Now.

When your computer is booting up, enter the BIOS (for me on my Asus it's F2) and select the USB as the boot drive. If there's two bootable drives with one with the word UEFI before the USB's name, select that.

Then select **Install Ubuntu **from the menu, or **Try Ubuntu without installing **if you want to toy with it a little first. Be careful though, your activity will be deleted from the USB after you shut down (at least in my case).

Have fun with Ubuntu.

---

### Post by coldraven on 2015-09-07
Hello and welcome to the forum.
If you plan to have a dual boot (Windows/Ubuntu) machine you will probably need to make some space on the drive. This is best done using a Windows utility before you try to install Ubuntu. I don't know Win7 so search for an answer or ask about it here.

---

### Post by fidel5 on 2015-09-10
> **John_Shea said:**
> Can someone provide the steps to download, install, and have Ubuntu running from my USB Drive from my Windows 7 machine. Like to install the latest version.

[Here]("http://geek-university.com/linux/install-ubuntu/") you have instructions on how to download and install Ubuntu.

---

