---
title: "Broken GRUB on KDM Linux Distro"
date: 2020-04-16
forum: New to Ubuntu
---

### Post by kiddreddlinux96 on 2020-04-16
Hey everyone. 

I am running into an issue where my OS appears to be totally done for. 

I must inform you first that the OS is installed on my Windows Hyper V  thru a VM. 

When booting the onto the hard drive, I get "grub rescue" 

When I do LS, I get (hd0) (hdo,gpt2) (hdo,gpt1) (fd0) . I have tried doing the "set prefix" "set root" on all the listed partitions and it did not change anything when rebooting the system. 

So I went ahead and tried "boot-repair disk" , downloaded from the internet and placed the ISO onto the virtual disk drive. It looked promising because it was noticing the correct partition (sda2) and the correct space but at the end, it gave an error message. 
Please view the link here: [http://paste.ubuntu.com/p/TnVTYvhBZG/](http://paste.ubuntu.com/p/TnVTYvhBZG/)

What else could be done? 

Please help, I am willing to try anything at this point, as long as we're able to get back into the OS (over 200GB of valuable data). Once there, I will update the grub and create a checkpoint in Hyper V in the event this happens again. 

Thanks

Edit 1:

Tried following up from a second reboot from boot-repair disk: [http://paste.ubuntu.com/p/d48pqt3DYY/](http://paste.ubuntu.com/p/d48pqt3DYY/)


Got the following results
[IMG]https://plik.root.gg/file/lZsNwrheTosfYNmw/8WelvmAvoYLN1If2/Grub%20Issue.PNG[/IMG]

edit2: 

Tried with Ubuntu live server and Debian iso and copied the grub folder over to (/dev/sda2) *which is what is displayed in Ubuntu & Debian rescue mode instead of (hd0,gpt2) -- I still get the "error:file '/boot/grub/i386-pc/normal.mod"

I believe its really in need of the above module in order to be booted.. I will continue to do some research to try and find something.

---

