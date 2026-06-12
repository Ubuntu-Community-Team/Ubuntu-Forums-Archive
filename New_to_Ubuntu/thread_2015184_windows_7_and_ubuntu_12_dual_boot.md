---
title: "windows 7 and ubuntu 12 dual boot"
date: 2012-07-02
forum: New to Ubuntu
---

### Post by dylanb2cm on 2012-07-02
I've just installed Ubuntu 12 on my Samsung Netbook.  At time of install, I chose to install  Ubuntu along side Windows.   I partitioned my hard drive.  It looks like everything worked. 

After I installed Ubuntu I reset the boot sequence to start with the internal hard drive.   

upon reboot windows 7 started up automatically.  

How do i make my netbook allow me to choose from windows 7 and ubuntu 12 at boot up

---

### Post by papibe on 2012-07-02
Hi dylanb2cm.

Follow the instructions [here]("https://help.ubuntu.com/community/Boot-Repair") on how to use 'Boot Repair' to both fix grub (in case wasn't installed correctly), and to select which OS will be the default.

Tell us how it goes.
Regards.

---

### Post by LADmaticCA on 2012-07-02
It sounds like grub did not install. I would try booting from your ubuntu live CD and re-installing grub. This tutorial looks pretty good.

[http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)

If you have trouble finding your exact Ubuntu partition label, the Disk Utility program lists the layout exactly. It's included on the live disk.

---

### Post by dylanb2cm on 2012-07-02
to show how much of a newb I am, what exactly is a GRUB

---

### Post by papibe on 2012-07-02
> **dylanb2cm said:**
> to show how much of a newb I am, what exactly is a GRUB

Grub is the program that installs itself on the boot sector, allow you to boot into a little text-mode, and choose which OS you want to boot your computer on.

Does that help?
Regards.

---

### Post by ttrublu on 2012-07-02
@Papibe : Correct me if I am wrong, but one can also say GRUB is the linux equivalent of MBR (Master Boot Record) in Windows. Am I right?

---

### Post by dylanb2cm on 2012-07-03
@papibe, Thanks.  Yes I've seen GRUB screen before.  Thanks for the clarification. 

I'm having a tough time getting The Boot-Repair Software as suggested in your link.   

I tried to make a bootable jump drive of the ISO image using lili USB.  Lili said it didn't like the ISO image.  I tried it anyway.  Needless to say when I booted from the jump drive I didn't get much more than a black screen with an error message.  

I also tried using the terminal instructions to install in ubuntu, but I really don't know how to use the terminal yet. 

Lastly I tried to get the boot repair using the software centre but not much luck there either.   

Can anyone give a little more detailed instruction on how to get the boot repair going?

---

### Post by papibe on 2012-07-03
I was under the impression that you 'just' installed 12.04. Why don't you use the same CD or USB that you used to install it?

Regards.

---

### Post by dylanb2cm on 2012-07-03
The other thing I've noticed, is that if I boot from the original linux live usb stick, it then gives me the GRUB

---

### Post by dylanb2cm on 2012-07-03
@papibe,  I think I just tried that.  Although I'm not really sure what you mean by that.  I did just try booting from the USB that I used to install it.  I Get Grub, I can choose between windows and ubuntu.  If i Choose ubuntu, pull out my usb and restart than it goes to windows.

---

### Post by MIJ-VI on 2012-07-03
(Replacing a missing GRUB2)

[HowTo] Recover Ubuntu After Installing Windows
[https://www.youtube.com/watch?v=sxZRjjPjic8](https://www.youtube.com/watch?v=sxZRjjPjic8)

---

### Post by dylanb2cm on 2012-07-03
Ok I got to work!  GRUB was fixed using this link

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) ,

I figured out how to use the terminal to install Boot Repair.  

thanks to everyone and especially papibe

Learning how to use UBUNTU!!!!!!!

---

