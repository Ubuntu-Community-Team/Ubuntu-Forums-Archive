---
title: "Boot order doesn't do anything"
date: 2013-08-06
forum: New to Ubuntu
---

### Post by pyroph2 on 2013-08-06
Hey everybody,

I'm currently trying to install Ubuntu 12.04 via a USB in my laptop. I've already created the live-sub and I've also changed the boot order in the BIOS. I've put the "USB HDD" in first place. However, when I turn my computer on, it simply starts as it always did. Do you have any explanation?

By the way, why do the USB I've turned into the live-usb possess a file named "wubi" in it?

---

### Post by oldfred on 2013-08-06
There has been a wubi on the live installer for quite a while. I thought it was because you could install wubi from a live installer with the older versions. But they now have changed it that you only install wubi from inside Windows. And wubi does not work with gpt partitions, so it is being depreciated.

I mis-read your post. I thought you installed. If you cannot boot live flash drive it then is not a bootable flash drive. Did you verify download with md5sum. And how did you install to flash drive, you do not copy ISO to drive but use an installer to extract the files and make the flash drive bootable.
       Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

    
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
    

If you have installed and have boot issues:
Where did you install grub2's boot loader? May be best to see what is where.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by will1982 on 2013-08-06
Your flash drive may not be bootable.
That happened to me once, I used a tool called "unetbootin" ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)). It worked correctly, and I'm still using that install.
Good luck!

---

### Post by andrea3 on 2013-08-08
Ciao,
 I had a similar problem. 
 I solved it in the following way. I have usually used F2 to edit my BIOS. However with my new computer I can also use F12 to edit just the boot order. So if I want to boot from usb, just after the start I press F12 change the boot order and it works. They told me that in this second way the computer already see the usb connection while if you change the boot order in the bios setting it doesn't and this can make some differences (I do not know if I am reporting correctly this explanation).  
 Also there is some setting you can change in the BIOS if you have something called secure boot which should be disabled. 
 Finally I also had this file named wubi. I lanched it and offer me other possible ways to go through the installation procedure.

Ciao
Andrea

---

