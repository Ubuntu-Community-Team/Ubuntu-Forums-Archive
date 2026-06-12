---
title: "Need Help to Repair My Boot"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by rhalls on 2012-04-09
I am new to linux, about 6 months experience, but I have accomplished alot in that time:
My travel laptop is triple boot (on one HDD), Mint11, Maverick 10.10 and WinXP
My wife's desktop is dual boot WinXP & Mint11 on dual HDDs.
My fun desktop has a DEDICATED boot partition, dual HDDs with WinXP on one HDD, and Mint & Mav on the other, ready to test out other distros like 12.04 when released
So, having some success & feeling (over) confident, I guess it was time I screwed up my next install, and that screw up happened in a big way on my most important machine, my home office business desktop:
Dell Precision 380 (2005) with Pentium D, dual HDDs, Nvidia Quadro 1400, 4Gb RAM, originally with WinXP.

The process: I backed up image of the old WinXP drive with Clonezilla Yeah!
I took out the old sda WinXP drive and put it away for safe keeping.
I added 2 new empty HDDs,  one small for WinXP and one large for linux distros. I connected the small HDD to sdb (SATA-1 port), and connected the large to sda (SATA-0 port). I restored the WinXP image to sdb, Clonezilla detected the change from sda to sdb, and made all needed adjustments, per info on its screen. WinXP booted fine. 
Then I installed Mint11 64-bit on large HDD (sda), installed Grub2 onto sda, and everything worked fine, with Grub2 menu offering Mint11, Mint11 recovery mode, memtest, and WinXP. Sweet! Everything worked well, both OS's booted flawlessly. I customized Mint and smiled.
Next, I'm ready to create a DEDICATED boot partition on sda, install Maverick and Precise when released.
Worried I am going to screw up the WinXP drive during the install (with all my business data), I disconnect it!!!!    What a mistake.
 My boot process became a mess. I never got a chance to make the dedicated boot partition because I have been trying to recover my boot process ever since. 
I have gotten the strangest BIOS messages:
Error: Can't enter Setup. video mode 103 is not supported by this video card
error: no such device 6ca33faa-f827-...........
grub rescue>
Remember, WinXP drive is still disconnected.

I tried using Boot-Repair CD, but it would not boot from the PATA master DVD-ROM drive or the slave DVD-RW
I tried using my Super Grub2 disk, it would not boot
I tried booting clonezilla live CD, it would not boot

The only thing that would boot was my Mint11 64-bit iso CD, so I installed and ran Boot-Repair from within the live Mint11 session. This failed to give a complete repair: sometimes the installed Mint would boot, sometimes not. 
Boot-Repair logs are at:
[http://paste.ubuntu.com/917916](http://paste.ubuntu.com/917916)
                                     /918008
                                     /918060
                                    /918403
                                    /919863
                                   /919866
Finally, when I got Mint11 to boot after 5 repairs in Live Mint11, I installed and ran Boot-Repair from within the INSTALLED Mint11, and this seemed to help.  I now have a Mint11 install that I can boot into consistently, it comes with a boot menu.
The DVD drives will only boot a live distro (nothing else) and the WinXP drive is disconnected.
I cannot boot clonezilla, Boot-Repair, or SGD from the DVD-ROM. 

Before I screw up anything else, I have to humbly ask for some help.
Have I corrupted the BIOS?
Last time I tried I could not enter BIOS Setup. I am afraid to try again since I have one distro running, don't want to screw it up
How do I now handle my disconnected WinXP drive?
Why doesn't a new install of Mint11 fix the boot problem?

If you have read this post, your brain probably hurts by now

Anyway, thanks in advance to the kindness of strangers for any help you can offer.
Bob

---

### Post by Bucky Ball on 2012-04-09
You could try Boot Repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by forrestcupp on 2012-04-09
Lol. Bucky Ball didn't wade through your entire post.

A couple of suggestions. You need to reconnect your XP drive, and don't disconnect it again. Just doing that will probably help matters. Just be careful to know which one is XP, which shouldn't be a problem because it's probably NTFS filesystem.

Next, why are you making it hard on yourself by trying to create a dedicated boot partition? Why not just let the installation take care of that for you? Just install a version of Linux, and let it put Grub wherever it wants, and then install your next version and let it automatically modify Grub during the installation. You shouldn't have to manually do anything at all with Grub.

Also, why do you really need more than one version of Linux on your important work computer? If that computer is really that important, it would be a lot safer to just install one version of Linux, and try out other versions in virtual machines. Virtual Machine programs, like VirtualBox, have really come a long way. If you install the Guest additions, you won't hardly even be able to tell it's not a real install.

---

### Post by oldfred on 2012-04-09
You said you installed Windows to the second SATA port. Always best to have Windows first, so it is sda. Windows XP is like older versions of Ubuntu that used device (/dev/sda1) not UUIDs. Your boot.ini still says disk 0 or sda in Ubuntu (the drivemap command maybe what allows it to work? as that may let it think it is still sda):
> multi(0)disk(0)[COLOR=Red]rdisk(0)[/COLOR]partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetectGrub 
Grub in MBR in both drives is booting from the same sda6 partition. But only one gets updated on updates, so which is the most current. If you can boot again.
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc


You may not understand a boot partition. That is just one of the folders off of / (root) like /home and many others. Some servers with RAID,LVM, special formats or very old systems with a boot limit of 137GB may need a separate /boot. Standard desktops do not need a separate /boot and it actually makes it a bit more complex. You cannot share a /boot with different installs.

Was results.txt (pastebin link) after you made fixes? I do not see anything really wrong with boot.
Did you change anything with video modes? I have seen some with issues not getting to CD or BIOS have systems get 'locked-up' and a cold (total power off) boot resets that. And/or you may have some corruption in your Linux partition. Then a e2fsck may be worthwhile on the Linux partitions.

---

### Post by rhalls on 2012-04-09
Here's what I get when I run sudo debconf-show grub-pc
Remember, smaller WinXP drive still disconnected
WDC_WD1003FBYX..... is large (1Tb) "linux" drive

bob@bob-Precision380 ~ $ sudo debconf-show grub-pc
[sudo] password for bob: 
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD1003FBYX-01Y7B0_WD-WCAW30674443
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: true
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10
bob@bob-Precision380 ~ $ 

Thanks.
Bob

---

