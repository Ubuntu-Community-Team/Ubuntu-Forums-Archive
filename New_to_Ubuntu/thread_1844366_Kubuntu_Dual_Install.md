---
title: "Kubuntu Dual Install"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by Wiking on 2011-09-15
Hi, up until now I've only been using Kubuntu 11.04 on a live CD. I now want to fully install it on a HD but have a few questions.

I'm going to install it on 356 GB hard drive. The drive currently is empty, but it is in NTFS file format. My W7 installation is on a separate drive.

1- Should I delete this drive using Windows disk management tool so it is unallocated when I begin installation, or should I just leave it in NTFS and partition it when I install it?

2- Will I have to install GRUB 2 for the boot? Or can I just boot it at the bios menu since it will be on a separate drive?

3- I would also like to install another Ubuntu Distro on the same 355GB HD, is this possible? Or would having 2 /boot, swap, home folders, and root partitions on the same drive make this impossible.

So in the end I will have 1 HD with W7, and another HD with 2 Ubuntu Distros. 

Thanks.

---

### Post by mastablasta on 2011-09-15
> **Wiking said:**
>  
1- Should I delete this drive using Windows disk management tool so it is unallocated when I begin installation, or should I just leave it in NTFS and partition it when I install it?

Both will do ok. you will have to tell it manually to install to the second drive if you leave it NTFS. it will reformat it anyway...
> 
2- Will I have to install GRUB 2 for the boot? Or can I just boot it at the bios menu since it will be on a separate drive?

you will need to install GRUB 2, however depending where you install it will give you or not give you the option of using BIOS. personally i would just install it and use it. it doesn't affect windows in any way as it loads before windows loads. keep a recovery or windows install cd ready.
>  
3- I would also like to install another Ubuntu Distro on the same 355GB HD, is this possible? Or would having 2 /boot, swap, home folders, and root partitions on the same drive make this impossible.
 
yes it is posisble. it is posisble to have even more systems (epsecially linux ones since they can boot from extended partitions).

---

### Post by Wiking on 2011-09-15
Just to clarify when installing GRUB 2, it says to install to the Master Boot Record (MBR). Now if the HD is sda, do I install Grub 2 to /dev/sda, or /dev/sda1 ( /boot) ?

---

### Post by Wiking on 2011-09-15
So I went ahead and installed the boot to dev/sda1 the /boot partition.

It looks good so far.

---

