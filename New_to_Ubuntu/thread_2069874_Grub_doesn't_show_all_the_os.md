---
title: "Grub doesn't show all the os"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by Keshav2050 on 2012-10-11
I had ubuntu 12.04 and windows in my computer, I wanted to try fedora and installed it in one partition of three equal partitions. while upgrading to ubuntu 12.10, I realized that process was not progressing and tried to restart the computer(actually the RAM was loosely fitted). After that ubuntu was not booting properly so I installed ubuntu 12.04 in place of quantal and upgraded it again, but the grub doesn't show the option of fedora. Below is the image of GParted.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=225400&stc=1&d=1349968662[/IMG]

---

### Post by oldfred on 2012-10-11
Fedora's normal install is LVM with a separate /boot. Even if you set not to use the LVM, it usually installs with the separate /boot partition. With the LVM you have to install the lvm driver lvm2 in Ubuntu to see the Fedora install.

May be best just to post the link that BootInfo creates to a report of your system.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by zhogan85 on 2012-10-11
Also, from Ubuntu, run the following, then reboot.

```
sudo update-grub
```

---

### Post by grahammechanical on 2012-10-11
You should also be aware of the fact that Ubuntu 12.04 uses Grub 1.99 but 12.10 uses Grub 2.0. There are differences. Grub 2.0 has sub-menus. I do not think that the OS_prober utility is very good at compiling menu entries drawn from Grub 1.99 and Grub 2.0, let alone other operating systems.

I have just been reading the Grub 2 manual from here:

[http://www.gnu.org/software/grub/manual/grub.html]("http://www.gnu.org/software/grub/manual/grub.html")

Gnu.org are aware of issues. They say this:

> Currently autogenerating config files for multi-boot environments depends on os-prober and has several shortcomings. While fixing it is scheduled for the next release,

12.04 will get Grub 2.0 in the new year. I have 1 x 12.04 install and 3 x 12.10 installs and no other OS. I found multiple entries not just for older kernels but for the same kernel image. They also had labels that did not distinguish between partitions or kernels, as we get in Grub 1.99.

You have upgraded to 12.10 which is not yet officially released. That is fine if you want to test but not so good if you want a stable OS.

What version of Grub does Fedora use? Has it switched to Grub 2.0? How much testing has been done on upgrading 12.04 with Grub 1.99 to 12.10 with Grub 2.0? What about testing dual booting 12.10 with Windows or Fedora or others?

It is common place in Linux for the user to be the tester.

Regards.

---

### Post by zhogan85 on 2012-10-11
> **grahammechanical said:**
> You should also be aware of the fact that Ubuntu 12.04 uses Grub 1.99 but 12.10 uses Grub 2.0. There are differences. Grub 2.0 has sub-menus. I do not think that the OS_prober utility is very good at compiling menu entries drawn from Grub 1.99 and Grub 2.0, let alone other operating systems.

Good to know thanks! I shall have to read the documentation. I only recently upgraded so have not been using grub2 for very long.

---

### Post by NikTh on 2012-10-11
Hi , 

try this solution. 

Boot normally in Ubuntu open a terminal and _**FIRST mount**_ the partition with fedora OS and then update grub.


```
sudo mount /dev/sda10 /mnt
sudo update-grub
``` 

Thanks

---

### Post by YannBuntu on 2012-10-12
Hi
It is probably this bug: [https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/1038093](https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/1038093)

Boot-Repair should be able to fix it.

---

### Post by Keshav2050 on 2012-10-12
Thanks, I already tried boot-repair but it didn't work, may be because I didn't mount the fedora partition, but it is working fine after I tried the commands

[B]sudo mount /dev/sda10 /mnt
sudo update-grub[/B]
Thanks for helping.

---

### Post by NikTh on 2012-10-12
> **Keshav2050 said:**
>  but it is working fine after I tried the commands

[B]sudo mount /dev/sda10 /mnt
sudo update-grub[/B]
.

Have in mind that it is possible after a grub update to lose again the fedora OS from grub menu. Anytime you update grub first mount the partition and then update the grub. 

grub-update runs automatically every time when a newest version of kernel installed in your system (with updates). So just keep in mind that after a grub update , you must run it again with fedora partition mounted. 

I have the same problem , exactly , with Arch Linux. I don't know if is grub's problem or have something to do with the boot files of the Distribution. 

Thanks

---

