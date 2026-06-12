---
title: "Grub Error 13: &quot;Invalid or unsupported executable format&quot;"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by nicholasbgr on 2008-08-19
Hi. I was dualbooting vista and ubuntu for a long time, but today I needed to use a software that only works on windows xp. So I created a new partition and instaled on it. After that I restored the grub loader and tried to boot on windows vista. The problem is: i get the error Grub Error 13: "Invalid or unsupported executable format" and windows xp is not showing up. Can someone help me fixing windows vista entry and creating a new one for XP?

This is what I got on fdisk -l:
> Dispositivo Boot Início Fim Blocos Id Sistema 
/dev/sda1               1        2117    17004771   83  Linux 
/dev/sda2   *        2118        2366     2000092+  82  Linux swap / Solaris 
/dev/sda3            2367        5764    27292866    7  HPFS ou NTFS  **[VISTA PARTITION]**
/dev/sda4            5765        9729    31848862+   f  Win95 (LBA) Partição Extendida 
/dev/sda5            5765        8643    23125536    b  W95 FAT32 
/dev/sda6            8644        9729     8723263+   7  HPFS ou NTFS   **[XP PARTITION]**


And this is my menu.lst:
> 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a5acf5fa-00cb-4bf9-acfb-9d42d592312d ro quiet splash locale=pt_BR 
initrd		/boot/initrd.img-2.6.24-19-generic 
quiet 
 
 
# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda2 
title		Windows Vista/Longhorn (loader) 
root		(hd1,0) 
savedefault 
makeactive 
chainloader	+1 


---

### Post by MarkieB on 2008-08-20
no longer participating in ubuntuforums.org

---

### Post by bumanie on 2008-08-20
Generally windows is best installed first, with ubuntu installed last. When xp and vista are installed together, it is best for vista to be installed first, then xp. Xp will overwrite vista's bootloader, thus, vista's bootloader needs to be fixed via a recovery cd - you will then get the choice of booting vista, or 'an older windows version'. Installing ubuntu at this stage should allow chainloading of the vista bootloader, which in turn gives the choice of vista or the older version of windows to boot, or of course, boot straight into ubuntu. As said above windows does not like trying to boot from a logical partition, linux does this OK. Despite having had vista and ubuntu booting OK until you installed xp, it is preferrable to have windows installed first. Also fdisk -l indicates that the boot flag is pointing to the swap partition, this also will cause problems as swap will not contain the stage 2 part of the bootloader that grub will be looking for. If it were me, I would save any important information via a live cd and reinstall from scratch with vista first, then xp (then fix vista's bootloader) and then finish with ubuntu. Make sure windows partitions are not within logical partitions. You could have a look at easybcd bootloader from neosmart, but in this situation, I doubt that it will help due to the above partitioning/boot flag anomalies.

---

### Post by caljohnsmith on 2008-08-20
> **bumanie said:**
> If it were me, I would save any important information via a live cd and reinstall from scratch with vista first, then xp (then fix vista's bootloader) and then finish with ubuntu.
If it is not a great inconvenience to do a complete reinstall of everything, I'm all for your idea, Bumanie; but nicholasbgr may not even have a Windows Vista install CD/DVD, and he may have a mature system that has many additional programs in Ubuntu/Vista and other customizations. I think he has a good chance of getting things working if he installs Windows XP to a primary partition, restores Grub to the MBR, and tweaks Grub's menu.lst to boot everything. The choice is his of course. :)

---

### Post by LUS93 on 2008-08-20
Assuming you have enough RAM for it, put XP in a VMWare or VirtualBox machine. Problem solved.

---

