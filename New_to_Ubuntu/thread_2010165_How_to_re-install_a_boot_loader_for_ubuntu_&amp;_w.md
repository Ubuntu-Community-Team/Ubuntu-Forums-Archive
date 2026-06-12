---
title: "How to re-install a boot loader for ubuntu &amp; win 7"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by johnnypict on 2012-06-25
Hi,

So I've installed Ubuntu and all is going well.
I also have Win 7 on the same machine.

I've managed to wipe the boot loader so when the machine boots I have to press F8 to load Ubuntu. Ubuntu is on a USB Hard Drive and working normally as an OS.

When I don't press F8, the screen goes to the WIN 'press F11 for recovery' screen. I can press F11 but nothing happens and the machine will happily sit there all day.

My question...
Can I install a boot loader that will recognise both drives, the WIN machine and the usb drive.

I know windows is still there and I'm running Wine to have a go at a flight simulator.

Thanks for any feedback.

John.

---

### Post by NikTh on 2012-06-25
Hi , 
Grub2 its a very configurable and easy to use boot-loader . (my opinion) 
If i understood correct , you must install Grub2 to your internal hard drive . e.g /dev/sda with your external usb HDD connected. Grub2 will recorgnize your OS's and you will have the ability to boot any of them.

---

### Post by jmfal on 2012-06-25
grub2 may listed as:

```
 grubpc     
```

In synaptic.

---

### Post by oldfred on 2012-06-25
To confirm where things are installed it may be best to have to boot info report. Do not run repairs, just yet unless adventurous. 

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by johnnypict on 2012-06-25
Great I'll try that.
Thanks.

John.

---

