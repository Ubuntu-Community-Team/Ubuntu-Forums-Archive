---
title: "Multiboot USB with persistence."
date: 2012-01-06
forum: New to Ubuntu
---

### Post by HittingSmoke on 2012-01-06
I don't know if this is the best place to ask this, but I'm at my wit's end and this is the most helpful Linux community around. I hoping since I'm trying to boot Ubuntu on the drive, it falls under the realm of appropriate questions here.

I'll start from the end as a sort of tl;dr. My aim is to have a bootable USB thumb drive running Ubuntu 10.04 with persistence. Simple enough. However, I also want to multiboot this drive with Hiren's BootCD, UBCD and Trinity Rescue Kit. On top of that I want to be able to boot into the installers and recovery menus for Windows XP Pro, Vista 32/64 and Win 7 32/64. I can do different combinations of this extremely easy without Ubuntu persistence, but that's a bit of a deal breaker for me.

My first thought was to create a persistent Ubuntu bootable drive then create an ISO from that and load it onto my thumb drive using YUMI. This didn't work as YUMI tries to load the entire ISO into RAM, and with persistence my Ubuntu ISO was 4GB. This drive has to work on older PCs.

My second thought was to hand-code GRUB to make this work myself. However there seems to be a serious lack of resources for newbies who want to learn how to use GRUB. I'm proficient enough with Linux to work my way around the desktop, install packages and keep a small web server running, but that's about it.

So, is there a way to get a persistent Ubuntu 10.04 bootable USB drive, add my own files from other ISOs and edit GRUB to not boot directly to the Ubuntu menu but give me options as if I were dual booting Ubuntu and Windows?

Again, sorry if this is an inappropriate place to ask this question. I don't know where else to turn.

---

### Post by C.S.Cameron on 2012-01-07
I explain how to make a persistent multibooter in post 41 of this thread.

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

EDIT;
MultiBootUSB sets up grub2 for multibooting via script.

---

### Post by HittingSmoke on 2012-01-07
> **C.S.Cameron said:**
> I explain how to make a persistent multibooter in post 41 of this thread.

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

EDIT;
MultiBootUSB sets up grub2 for multibooting via script.

I actually managed to get Ubuntu 10.04 running with persistence through GRUB. It comes up with a menu, but only Ubuntu is installed at the moment.

Do you have any insight as to how to get GRUB to boot other ISOs, like a Windows installer DVD, Hiren's BootCD or UBCD?

---

### Post by C.S.Cameron on 2012-01-07
UBCD is on the list of O/S bootable with MultiBootUSB.

Windows 7 installer DVD needs to be copied to the first partition of the flash drive, that partition needs to be formated NTFS with the boot flag set. Gparted works well for this. 
There should be some way to get grub2 to boot this on a multibooter.

---

### Post by oldfred on 2012-01-09
I did not do it with the Windows 7 install, but with a Windows 7 repairCd.

I used a Windows 7 repair CD to install/copy to a flash drive. Made sure it booted, but then realized it had lots of room. So I just installed grub2 to the MBR of the flash drive. I did have to be careful to make sure the /boot/grub folder was the same /Boot folder in Windows with the BCD. I renamed/moved files so I only had one /Boot folder with both the BCD & a /grub under the /Boot. Then with a standard chainload entry in grub2's grub.cfg I could boot with grub & chainload the the partition boot sector of the NTFS partition. I then shrank the NTFS partition and added another ext3 partition and put several ISOs into that to boot with grub2.l

---

