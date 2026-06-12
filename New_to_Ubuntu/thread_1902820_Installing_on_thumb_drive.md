---
title: "Installing on thumb drive"
date: 2011-12-31
forum: New to Ubuntu
---

### Post by theduke1 on 2011-12-31
Not sure how to start. So i will just tell you what i am trying to do. I am using start key on a portable hard drive (640 bg). I have hundreds of portable app that work great. Now i am trying to put Ubuntu on there. I loaded portable virtual box and it work perfect. Now i am trying to load Ubuntu 64 bit and Ubuntu 32 bit on there. So i can use each one depending on what computer i am working on. But every time i load Ubuntu i load it on the thumb drive but it still keeps looking for it on the hard drive. I have reloaded it several time and have tried all the options. But it still is looking on hard drive. Can you help me figure this out. I want thank you in advance. I will keep an eye on things but this being a holiday weekend i probably won't get back till Monday. Thanks again

---

### Post by Megaptera on 2012-01-01
Have you had a look at this guide?

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by z3nhakr on 2012-01-01
Are you trying to boot of the thumb drive? if so it is best to only install the 32 bit version unless all of your computers are x64. to do this you need to:
1. burn ubuntu to a cd
2. configure you bios so it boots off of the cd
3. boot the cd and start installation
4. partition your thumb drive (you will have to format it first so back it up) I usually partition mine with a 50gb ext4-this is where ubuntu is installed, 2gb swap, and the rest of the drive as fat so it can be accessed from windows.
5. set the 50gb ext4 partition as the primary partition (where ubuntu will be installed.)
6. complete the installation and enjoy :D
just remember that you have to configure the bios to boot off of the usb on every computer you use it on.

---

### Post by C.S.Cameron on 2012-01-01
I dont know if Start Key is compatable with grub 2, if it is you might want to check out MultiBootUSB.

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by grahammechanical on 2012-01-01
May I ask for clarification? Have you installed Ubuntu inside portable virtual box? Or in its own partition on the thumb drive? Do you have Ubuntu on the hard disk?

I recently installed Ubuntu on a USB memory stick. I set USB as the first boot option in the BIOS. Then the USB Ubuntu always loaded when the USB memory stick was plugged in otherwise the BIOS would load the Grub menu from the hard disk.

You seem to be selecting Ubuntu from a menu of some kind. Please give a more detailed explanation of your set up.

You say this:

> Now i am trying to load Ubuntu 64 bit and Ubuntu 32 bit on there. So i can use each one depending on what computer i am working on.

But you mention Virtual Box and that is confusing me.

Regards.

---

