---
title: "debutant..."
date: 2021-02-12
forum: New to Ubuntu
---

### Post by arkhane on 2021-02-12
Hello.

I have a [COLOR=#333333][FONT=Inter] laptop with 3 internal SSDs

[/FONT][/COLOR]
[LIST=1]
[*]bought with the laptop with W10 (C drive)
[*]bought separately, this will contain Ubuntu (E drive)
[*]2.5 inches SSD with all my data (D drive)
[/LIST]

[COLOR=#333333][FONT=Inter]So my goal is to not touch the C: drive and install it on the 2nd SSD.[/FONT][/COLOR]
[COLOR=#333333][FONT=Inter]I have already installed this 2nd SSD in the laptop, went to disk management in windows to format it, give it the drive letter e:

what installation should I select?

 &#8220;Install Ubuntu alongside Windows 10&#8221; 
&#8220;erase disk and install Ubuntu&#8221;
&#8220;something else&#8221;

I absolutely do not want to install it on the same drive as W10. once completed I want W10 to be the default OS and if I want to go to Ubuntu I must select it during the boot.

Thank you to give me usuefull information[/FONT][/COLOR]

---

### Post by mrdc76 on 2021-02-12
Select "something else". This is the manual partitioning option.

---

### Post by arkhane on 2021-02-12
ok...then I have no idea what to select...and I already did the partition in Windows...I want it on the disk without special partition...

?

---

### Post by Hagar Delest on 2021-02-12
In GParted, you should be able to select the drive that is displayed (top right).
Then create a single partition for / and that's all.

---

### Post by Impavidus on 2021-02-12
Ubuntu can only be installed on partitions with a Linux filesystem and Windows doesn't know about Linux filesystems, so creating the partition in Windows is pointless. You have to use the Ubuntu live disk to format your ssd. And, as Windows won't understand your Linux filesystem, it won't give it a drive letter.

On the live disk you'll find a tool named gparted. It's a good program to partition your drives. You can use that to make the partitions you want for Ubuntu. You need at least one partition of at least 30GB as your root partition (mountpoint will be / ). Make it of type ext4, unless you know why you want something else. More advanced partitioning schemes may be useful, but not vital.

If you want good control over where Ubuntu gets installed, use option "something else", which allows manual partitioning. You can edit the partitions of your drives there, or just point to the partitions you created before. I prefer to create them before.

Ubuntu's boot loader (grub) will be stored in the same EFI partition as your Windows boot loader. You can avoid that if you disable that harddrive in UEFI or physically disconnect it. Do that if you want Ubuntu bootable even with the Windows drive removed. In any case, you'll get two bootloaders. The Windows bootloader will boot Windows, the Linux bootloader will boot both Ubuntu and Windows, defaulting to Ubuntu (but you can change that). You can use UEFI setting to select your bootloader.

Linux does understand Windows filesystems (to some extend) and can read/write files there, but only if the filesystem is undamaged and Windows isn't hibernating. So you can access your data drive (D) from both OSs, but only if you disable FastStartup in Windows.

---

### Post by grahammechanical on 2021-02-12
Please read this help document.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Note these points:

> 
[LIST]
[*]if the other systems (Windows Vista/7/8, GNU/Linux...) of your  computer are installed in UEFI mode, then you must install Ubuntu in  UEFI mode too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 


[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not.
[/LIST]


It might be best to disconnect the other drives then you can with confidence select the Erase Disk and install Ubuntu option. It can be intimidating doing a Something Else install for the first time.

Regards

---

