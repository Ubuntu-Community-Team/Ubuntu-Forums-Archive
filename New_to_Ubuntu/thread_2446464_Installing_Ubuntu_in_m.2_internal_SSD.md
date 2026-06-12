---
title: "Installing Ubuntu in m.2 internal SSD"
date: 2020-07-01
forum: New to Ubuntu
---

### Post by premrishi on 2020-07-01
Hi, I've my hp 1056 tu pre-installed with Windows 10 in primary HDD. I'm planning to get an m.2 type SSD and install Ubuntu on it. I don't want to disturb or interact with the HDD. i want my Ubuntu completely in my SSD and windows completely in my HDD and i want to switch between them for my work and gaming. I'm new to Ubuntu, please provide me the steps to be followed from the scratch. Thanks

Specs:
hp 1056tu 
hdd 1tb
ssd 120gb

---

### Post by tea for one on 2020-07-01
In your position, I would first explore the following:-

_Examine your hardware_.

Can you physically remove your Windows HDD?

_Explore your UEFI software_.

Can you deactivate or isolate any drives (especially the existing HDD)?
Can you select a drive and boot it from within the UEFI screens?

If you can remove or isolate your Windows HDD (not essential but it gives peace of mind), then you will be perfectly placed to examine Ubuntu.

The next step is to try Ubuntu [https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)

Make sure that _all_ your hardware functions OK, particularly keyboard (including language selection), graphics, wifi, sound and touchpad.

Have you backed up your data in your Windows drive - fundamental?

---

### Post by premrishi on 2020-07-01
Thanks for the reply, and to answer your questions
I can't physically remove my windows HDD, due to the current situation in my locality, and secondly i haven't tried anything to boot, I'm a newbie, and the pc is also a week old. I haven't backed up my data in my windows drive.

---

### Post by tea for one on 2020-07-01
> **premrishi said:**
>  I can't physically remove my windows HDD, due to the current situation in my locality

I don't understand this comment. However, you may be able to deactivate it if you explore the UEFI Start Up screens.

> **premrishi said:**
>  I haven't backed up my data in my windows drive.

This is essential before you attempt to install another operating system.

> **premrishi said:**
> and the pc is also a week old.

As I mentioned earlier, take some time to examine your hardware and the UEFI Start Up menu.

Here is one link and I'm sure that there are many more:-

[https://support.hp.com/gb-en/document/c03801890](https://support.hp.com/gb-en/document/c03801890)

---

### Post by oldfred on 2020-07-01
Ubuntu's Ubiquity installer only installs grub to ESP on first drive. Usually Windows drive.
But not sure with NVMe & sda drive which grub will see first. Probably depends on UEFI and which drive it reports as first drive. 

To be safe, see if you can disable Windows drive in UEFI settings. You have to make other UEFI setting changes, so best to review UEFI, download its manual and understand the settings.

If you cannot disable drive, see this work around.
Also see work around during install in #23 & 26
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Other distributions let you change to the ESP of your choice. Ubuntu's Ubiquity in UEFI mode does not, even though the screens seem to offer change, but change only works for BIOS installs which you do not want.

Best to partition in advance using gparted & then use the Something Else install option.

---

### Post by premrishi on 2020-07-01
hey there, regarding the windows hard drive, yes it's possible for me to disconnect it. so, if I'm right, i want to disconnect my hdd when booting up the system and insert bootable ubuntu os stick, with m.2 ssd connected internally. Then i've to choose "ERASE DISK AND INSTALL UBUNTU" and follow up. Then boot to Ubuntu and connect the hard drive. if i want to switch between them, pressing f12 while booting will lead to select one of the two. correct me if I'm wrong, thanks.

---

### Post by oldfred on 2020-07-01
Some UEFI "forget" UEFI boot entries for disconnected drives. But most find Windows, but not Ubuntu.
If entry lost you can use efibootmgr or Windows repairs to restore.
Make sure you have Windows fast start up off & make a Windows repair/recovery flash drive.

If fast start up off in Windows, you can run this in Ubuntu & it will add Windows back into grub menu after you plug Windows drive back in.
sudo update-grub

Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive) & 
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by tea for one on 2020-07-01
> **premrishi said:**
> hey there, regarding the windows hard drive, yes it's possible for me to disconnect it. so, if I'm right, i want to disconnect my hdd when booting up the system and insert bootable ubuntu os stick, with m.2 ssd connected internally. Then i've to choose "ERASE DISK AND INSTALL UBUNTU" and follow up. Then boot to Ubuntu and connect the hard drive. if i want to switch between them, pressing f12 while booting will lead to select one of the two. correct me if I'm wrong, thanks.

Are you sure that F12 is the correct key to choose Windows or Ubuntu?

I thought that it is F9 for Boot Device Options.

---

### Post by oldfred on 2020-07-01
Correct key varies by vendor. Many are f12.

UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

