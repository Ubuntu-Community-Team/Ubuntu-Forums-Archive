---
title: "Kubuntu 12.04 will not boot from hard drive"
date: 2012-09-26
forum: New to Ubuntu
---

### Post by norima on 2012-09-26
,me too experience the same problem :mad: Please help!

---

### Post by oldfred on 2012-09-26
I moved you to your own thread as your boot issues will be different. 

Please describe a bit more what Windows and  Ubuntu you have and how you installed.

From Ubuntu liveCD or USB download this and post the link it creates when you run BootInfo report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by norima on 2012-09-27
I installed kubuntu 12.04 LTS 32bit but when I boot the machine it displays entirely black screen with a cursor blinking on the top left corner. But it will work just fine when I boot the machine from USB.  I don't think there's anything special installed in the USB coz I'm using an empty USB (freshly formatted).  Any ideas?

---

### Post by YannBuntu on 2012-09-27
Seems like GRUB was installed in your usb.
Please run Boot-Repair, and indicate the URL that will appear.

---

### Post by oldfred on 2012-09-27
When you say boot from USB is that to your full install as Yann suggests or just your LiveCD/USB installer version. If full version follow Yann's suggestion on Boot-Repair.

If it is just the installer version, what video card/chip do you have? You may need nomodeset or other boot parameter. With USB have you used any boot parameters?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by norima on 2012-09-27
thank you all to your replies.  well, after searching throughout the internet,  it turns out that my processor doesnt support PAE.   so i guess, i don't have much choice but revert it back to 11.10. Kubuntu 12.04 is kinda stable but i dont like the gray anyway hehe.:D

---

### Post by oldfred on 2012-09-27
I think you could use Lubuntu.

[http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae

---

### Post by deadflowr on 2012-09-27
You can reinstall 11.10, then network upgrade to 12.04. You will upgrade a normal kernel not the PAE kernel.
However, it will be the last time it will upgrade, as 12.10 onward will only support PAE.

---

