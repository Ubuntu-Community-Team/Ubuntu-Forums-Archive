---
title: "Dual boot using Windows NTLDR"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by yezlyin on 2011-11-05
Hi, back in the old days of legacy GRUB, it used to be possible to set up a dual boot system with WinXP and Ubuntu in which the Windows NTLDR was in control of the boot process, but would chainload legacy GRUB on demand.

The process is detailed [here]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/"), but in a nutshell GRUB was installed to the root of the Ubuntu partition (not the disc MBR), a copy of the 1st 512 bytes of the Ubuntu partition was made and the file (Ubuntu.bin) put in the WinXP C drive, and the Windows Boot.ini file was modified to point to Ubuntu.bin. On booting, the Windows NTLDR was in charge, but could chainload GRUB via the Ubuntu.bin file.

My question is; is this chainloading method still valid now that Ubuntu uses GRUB2 as a bootloader?

---

### Post by oldfred on 2011-11-05
Welcome to the forums.

Well, I like grub2, so my question is why? Grub2 will boot XP without any issues and if you prefer XP can set it to boot XP as the default. It chain loads to Windows better than Windows chain loads to Ubuntu.

Grub2 is larger than grub legacy. If you force it into a partition it converts to using  blocklists or hard coded addresses for the rest of the grub files needed to boot. If on an update or even aggressive fsck the files may move and you then cannot boot until you reinstall grub to the PBR. Since that is not so reliable it is not recommended.

---

### Post by yezlyin on 2011-11-05
Hi oldfred, thanks for taking the time to reply.

There is a short and long version of my answer:

**Short version**: I would like to experiment with Ubuntu, which includes the option of deciding I don't like it and removing it completely from my PC without destroying the existing WinXP installation. Installing GRUB2 to the MBR and then removing Ubuntu makes WinXP unbootable without repairing the MBR.

From your reply, it seems it is possible to chainload to GRUB2 in a partition, but at the risk of destroying the Ubuntu boot at some stage?

**Long version**: Windows is essential for me because of 2 aspects - photo editing and  geographic tools - which currently can't be duplicated in the Linux environment. Worst case scenario with a failed boot is having to reinstall WinXP - a major pain. My PC is a Dell, which means that it didn't come with an XP installation disc (very annoying) but it does have a hidden partition with a restore disc image. That partition is accessed through a modified MBR. So if I install GRUB2 to the MBR, then remove Ubuntu and use FixMBR to restore the MBR, I lose the custom Dell code and can no longer access the WinXP restore image. I can (and have) imaged the drive with 3rd party tools for disaster recovery purposes, but the only way to find out if that image is good is to try it - bad news if it fails.

**To summarise**, Ubuntu installation is brilliant - in about 30 mins you have a fully functional OS *and *a good selection of apps and can easily add more. WinXP installation is a real pain, even if you have the install CD (I don't): the install only takes about an hour, but then you have to download and install massive service packs, then add all the security updates, then reinstall all of your apps. This takes days. Given that WinXP is essential for me, I really, really really want to avoid any possibility of having to reinstall. On the other hand, I'm quite happy to reinstall Ubuntu (to its credit)

**Last thought**: The Ubuntu install process for dual booting seems to me to be schizophrenic. It does an excellent job with default settings, and as you point out GRUB2 is an admirable boot manager. But should you wish to uninstall Ubuntu and retain Windows, that same set-up seems to pitch the hapless user into disaster recovery mode. I think this is a big deal for people like me dipping their toes into Linux territory. I wonder why nobody in Canonical (which seems to want to encourage Win users to move over) has given thought to making it easy to undo a Ubuntu dual boot install? I imagine it is a very common way for Windows users to test Ubuntu.

Sorry for the long reply (if anybody actually got this far)

---

### Post by oldfred on 2011-11-05
In your case, I would make a dd backup of the MBR to save the custom MBR. But for those who really need Windows a second drive is often the better choice as then each can be independant. But grub defaults to installing to sda, so you still have to be careful if installing to a second drive.

I always hesitate to use dd. As its nickname is Data Destroyer. But it can do some detailed things like copy the MBR.

Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)
Backup the MBR e.g. 
sudo dd if=/dev/sda of=mbr.bin bs=446 count=1

Note if you use 512, the full MBR that includes the partition table. But then changes to a partition table & a restore of an old full MBR can create partition table issues.

---

### Post by yezlyin on 2011-11-05
If one installs Ubuntu to a second drive (say sdb) and also puts GRUB2 in the mbr of sdb, how do you then chain load from the NTLDR (in sda)?

Good point about the dd command - I have already used it to copy the first 446 bytes of the WinXP mbr. Bit nerve wracking tho' since a any syntax error can have disasterous consequences - particularly writing back to the mbr. On the subject of the dd command, if i want to copy the first track (63 sectors), are the sectors numbered from 0-62, or 1-63?

Just for clarification, and I understand that you really don't like/recommend installing GRUB2 to a partition - but this can be done, and one could then chain load from the windows NTLDR to GRUB2? And am I understanding correctly that the risk of doing this is that the GRUB2 in the partition may be overwritten, thus breaking the Ubuntu boot?

---

### Post by oldfred on 2011-11-05
I believe it is 1-63, but am not sure as I have not done it.

I also saved this:
Partition boot sector 16
sudo dd if=/dev/sda16 of=sda16_63sectors.bin count=63 bs=512

It is not that grub in the PBR gets overwritten, but if the grub files in /boot/grub change location, the block list in the PBR will be looking in the wrong place.

Both old grub & grub2 chain load to a Windows PBR without any issue on any drive. Even the Windows boot loader in the MBR is really just a chain load to the PBR.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by yezlyin on 2011-11-05
olfred - thanks very much for your helpful advice and pointers. The multibooters site is a great resource, and the dd commands a big help.

At the moment, I'm inclined to go with  chainloading using GRUB in the PBR, mainly because at this stage its much easier for me to replace an Ubuntu installation than WinXP in the event of things going wrong.

I really appreciate you taking the time to help, even if it seems like I'm ignoring your sage advice. I've learnt a lot from your comments, and consequently, I've marked the thread as "Solved".

---

### Post by oldfred on 2011-11-05
That is fine. One nice thing about Linux is you have many choices. 

When grub2 first came out, I  still chainbooted to grub2 in a PBR as I used only chainbooting with grub legacy. It worked for the few months I used it. I think you can in synaptic (which now you may have to install) lock grub2 so it does not update.

If reinstalling grub2 to a partition you may have to add --force to the reinstall command as it fights you on partition installs.

---

