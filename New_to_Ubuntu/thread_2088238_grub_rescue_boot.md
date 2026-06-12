---
title: "grub rescue boot"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by Flynn58 on 2012-11-25
Okay, I have a system with a dual boot of windows 7 32-bit ultimate and ubuntu 12.04 LTS 64-bit. I use EasyBCD to manage my boot menu. Apparently during my upgrade to ubuntu 12.10 64-bit, grub failed to reinstall. I now have a grub prompt on a black and white screen. I have tried doing ```
linux /vmlinuz root=/dev/sd1 ro
```
however I got back the waring that the linux command is non-existant. Any help is welcome, and I would really prefer not to do a complete reinstall of ubuntu.

---

### Post by oldfred on 2012-11-25
Do not know EasyBCD. May be best to use their forums if you want to keep it.

If you want help with grub2's boot loader.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

