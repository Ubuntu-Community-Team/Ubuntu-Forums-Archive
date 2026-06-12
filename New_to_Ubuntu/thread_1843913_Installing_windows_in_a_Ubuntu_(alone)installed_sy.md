---
title: "Installing windows in a Ubuntu (alone)installed system"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by ksrsubramanian on 2011-09-14
Hi all,
      Accidentally while using windows in my DELL STUDIO(64bit)  i used the partition manger in that. while doing so the partition in which ubuntu installed got collapsed. so i installed ubuntu11.04 in my system for the whole partition. now my system is havinng a single partition with ubuntu 11.04. Now i want to install windows without affecting the currently installed ubuntu. For that i have to make a partition without affecting currently installed ubuntu

i have attached a screen shot of the Gparted partition manager in ubuntu

can any body help

Thanks
Kallis,

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=202147&stc=1&d=1316000648[/IMG]

---

### Post by Mark Phelps on 2011-09-14
Since you can't work on a partition while it's mounted, you will have to boot from the UBuntu CD to do the work.  Once booted, choose the Try Ubuntu mode.  Then open either the Disk Utility or Gnome Partition Editor and shrink the partition to leave some unallocated space.

Do NOT format the unallocated space -- leave it as is.

Then, reboot using your Windows CD (if WinXP) or DVD (if Win7), choose the unallocated space, and do the installation.

---

### Post by ksrsubramanian on 2011-09-14
Hi phelps,
          Thanks for your reply . I hav GParted in my live CD shall i use it ? will the two partitions be formated ?  by using it if so my data will be lost :(

Thanks
Kallis

---

### Post by Lisiano on 2011-09-14
Don't worry. As long as you don't actually tell GParted to format something, it won't. Just pick Resize/Move. Also you CAN format the newly made unallocated space as NTFS (I do that so Win7 doesn't create a hidden partition). Also you will have to restore GRUB since Windows will overwrite it. Check if your BIOS has something like a "Protect bootsector" or "Prevent overwriting the bootsector" and set it to Enabled if you can, less headaches. If you have that in your BIOS, then after installing Windows, boot into Ubuntu and run ```
sudo update-grub
``` in a terminal. If you don't have something like that in your BIOS. Then reference this [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by ksrsubramanian on 2011-09-15
Hi pals,
          Try the things you told. Used Gparted for shrinking my 465 GB partition to 435 (+30) GB left that partition "unallocated". While rebooting my BIOS didn detected my ubuntu in that 435 Gb partition and the BIOS started restarting(** why?**) .After that i tried to install windows ultimate in that 30 GB partition .It said no drivers found like dat. so i didn installed windows too. I think the small size of 30 GB may be the reason for that  **is it so?** Now i installed another ubuntu 10.04  in that 30 GB partiton and now i am using thats GRUB  to boot into my old Ubuntu ,no problem with this. But somehow i want to install windows without losing my "old ubuntu" in that 435 GB 

If i am installing windows will it automatically detect the ubuntu installed already ?and will windows create a GRUB ?


Thanks
Kallis

---

### Post by P05TMAN on 2011-09-15
> **ksrsubramanian said:**
> Hi pals,
          Try the things you told. Used Gparted for shrinking my 465 GB partition to 435 (+30) GB left that partition "unallocated". While rebooting my BIOS didn detected my ubuntu in that 435 Gb partition and the BIOS started restarting(** why?**) .After that i tried to install windows ultimate in that 30 GB partition .It said no drivers found like dat. so i didn installed windows too. I think the small size of 30 GB may be the reason for that  **is it so?** Now i installed another ubuntu 10.04  in that 30 GB partiton and now i am using thats GRUB  to boot into my old Ubuntu ,no problem with this. But somehow i want to install windows without losing my "old ubuntu" in that 435 GB 

If i am installing windows will it automatically detect the ubuntu installed already ?and will windows create a GRUB ?


Thanks
Kallis

Depending on the Windows version, it may erase or replace grub with its own MBR. 
If that happens: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by ksrsubramanian on 2011-09-15
> **P05TMAN said:**
> Depending on the Windows version, it may erase or replace grub with its own MBR. 
If that happens: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)



OK  ill try. could you pls tell what 
 should be minimum partiton size for windows  for working well ?
Thanks
Kallis

---

### Post by P05TMAN on 2011-09-15
Win XP is like 2GB minimum & win 7 is like 16gb minimum disk size. Keep in mind though that Micrsoft programs like MS Office are HUGE, so if you are able to hardware wise, consider like 50GB or so.

---

