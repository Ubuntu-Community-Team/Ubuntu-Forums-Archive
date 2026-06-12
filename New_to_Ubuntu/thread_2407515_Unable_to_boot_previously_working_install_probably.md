---
title: "Unable to boot previously working install probably due to firmware bug"
date: 2018-12-05
forum: New to Ubuntu
---

### Post by phitolo on 2018-12-05
I'm pretty much a newbie to Ubuntu and got a pretty strange bug, which prevents me from booting my machine. Here is the short story: I had Kubuntu installed as the only OS on my machine (it wasn't me who installed it). Everything worked fine until I decided I wanted to disable some unneeded boot devices (boot from CD, USB, network ...) in the UEFI firmware of my MSI motherbord. I'm not really sure what the problem was, though I presume a bug in the firmware, but after only changing the booting order of the devices and disabling the unneeded ones (CD, USB, network), keeping only booting from hard drives (both UEFI and legacy), the machine refused to boot at restart. I changed everything back as before but still no boot (blinking underscore appears each time). I run boot-repair-disk from a live USB but the recommended repair didn't work with the error message: "Please close all your package managers (software center, update manager, synaptic, ...). Then try again." I don't understand what it wants since I don't think I have any of those open so I just run the diagnostics and here is the pastebin:
[http://paste.ubuntu.com/p/YzjvGQ7pwH/](http://paste.ubuntu.com/p/YzjvGQ7pwH/)
If anyone has any idea of what is wrong and any suggestions on how to get my machine back up and running it will be greatly appreciated. Thanks!

---

### Post by oldrocker99 on 2018-12-05
Looks pretty hosed. Someone else might be able to give more help, but from where I sit, your best bet is to backup what you can, and do a new installation.

---

### Post by oldfred on 2018-12-05
I do not know LVM installs.
And script has not been updated to fully show details on NVMe drives.

But you are not showing any ubuntu entry in your UEFI?

I would try using Boot-Repair's advanced mode and totally reinstall grub to get grub to reinstall UEFI boot entries. You normally have two, one shim for Secure boot (which also works with Secure boot off, and grub which is only for UEFI Secure boot off.
Make sure you LVM partitions are mounted before running updates with Boot-Repair. If not encrypted it should mount them, automatically.

---

### Post by phitolo on 2018-12-05
Thanks for your reply.
I guess there is no Ubuntu entry in the UEFI because the firmware utility doesn't recognize right know any UEFI hard disks, it only recognizes the hard disks in legacy mode. 
The LVM partitions were indeed not mounted when I did the pastebin but they were when I retried (I changed the booting order in the firmware from the normal hard disk first to the SSD first, maybe that helped). I also checked and everything is still there on all the partitions (including the LVM) so I really hope I can get everything back up and running. I hope it is just missing UEFI boot entries.
I tried rerunning Boot Repair in advanced mode but I got the error message again: "Please close all your package managers (software center, update manager, synaptic, ...). Then try again."
Any ideas how to solve this?
Also in advanced mode should I check/uncheck any other options compared to the suggested repair of Boot Repair?
Thanks again.

---

### Post by oldfred on 2018-12-05
Are you running Boot-Repair from Ubuntu live installer?
Update manager should not be running?
What brand/model system?

Did you update UEFI and firmware for SSD?
And UEFI udpates reset everything to defaults and you have to go back thru and redo any changes.
With BIOS I had to take screen shots as I can 7 or 8 settings, but aony some are required and others optional. 
My new UEFI system gives me a list of changes and lets me save screens, so easier to keep track of UEFI setting changes.

---

### Post by phitolo on 2018-12-05
> **oldfred said:**
> Are you running Boot-Repair from Ubuntu live installer?
Update manager should not be running?

I run Boot-Repair from a live USB key (boot-repair-disk) so I do not understand either the error message regarding the update manager.

> 
What brand/model system?

The motherboard is an MSI X299.

> 
Did you update UEFI and firmware for SSD?

I didn't install the system and OS myself so I don't know but everything was running fine until recently so I assume the firmware was configured correctly for SSD. I did not do any update of the firmware nor a reset to defaults, the only thing I changed, which triggered the boot problem, was changing in the firmware setup utility the booting order and disabling booting from unneeded devices (CD/DVD, network...). I really didn't think this would cause any problems so I didn't take any screenshots of the changes but I think I changed everything back as it was and it still didn't work. I don't remember whether before the changes there was an active UEFI hard disk in the firmware setup utility (I assume yes since it was able to boot before) but right now the setup utility does not detect any UEFI hard disks.

---

### Post by oldfred on 2018-12-05
You may get a UEFI update from Linux.
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

Not sure if that is just their laptops or motherboards.
One user posted that it updated UEFI, without his knowledge. And that would reset some UEFI settings.

---

### Post by phitolo on 2018-12-06
Thanks for the feedback. Let me see if I understand the issue correctly.

Since the firmware setup utility does not detect the hard disks in UEFI mode (only in legacy mode) could it be that there is an issue with Grub and a reinstallation of Grub could solve it or is it necessarily a firmware configuration issue and I should rather look into changes to the firmware configuration to make the UEFI hard disks appear back? If there is no way the non appearing UEFI hard disks in the firmware can be solved by Grub reinstall and reconfigure I will then focus on the firmware configuration.

---

### Post by oldfred on 2018-12-06
It may just be settings in UEFI, new UEFI settings also have settings to turn on/off hard drives, also drives must be in AHCI mode unless you are running RAID 0.

---

### Post by oldrocker99 on 2018-12-06
My own personal experience is that, if you choose Legacy over UEFI, the installation will go a lot better. What had happened to me was that the installation went fine, and then grub, which is absolutely required to boot the system, failed to install, leaving an unbootable PC.

For me, if you choose UEFI, the USB boot screen is hi-res, and nice-looking. The Legacy screen is low-res, but it is the one that works.

---

### Post by phitolo on 2018-12-08
OK so I still didn't find the solution to the problem yet. First let me say I would really like to avoid having to reinstall Ubuntu, as I didn't do it in the first place and I will have quite some trouble setting everything up as it was.
Again everything worked fine until the firmware bug, so I still hope a small change again will be able to solve this. I looked into all of the firmware setup options and everything seems to be set up fine, SATA is set in AHCI mode. Also both hard drives (the SSD and the regular one) appear in the firmware, they just don't appear as UEFI drives. Also after starting on the Boot repair live disk I am able to mount all of the partitions including the LVM ones and they seem fine. The EFI system partition is also there, though I am not expert enough to tell whether all the booting files are there where they should. 

As a next step I will probably try and reset default firmware setting (after taking screenshots of the current ones) and moving back step by step. 

If anyone knowledgeable with LVM installs has any other suggestions based on the initial pastebin I'll greatly appreciate. Thanks.

---

### Post by angisky on 2018-12-08
I personally have never had an issues with this but when in doubt go legacy mode. I would definitely reinstall grub. Usually the scripts for it auto-detect your OS's so it really shouldn't even be difficult to do. If you wanna get creative while your at it there different things you can do to make grub look nicer (or you could make it not appear at all at boot).

---

### Post by phitolo on 2018-12-12
Restoring firmware default settings did not solve the problem. Since boot repair gives an error message when asked to repair ("Please close all your package managers (software center, update manager, synaptic, ...). Then try again.") I would like to attempt a manual reinstall of Grub.

Could someone (oldfred maybe?) please check the commands below and the boot info pastebin here [http://paste.ubuntu.com/p/YzjvGQ7pwH/](http://paste.ubuntu.com/p/YzjvGQ7pwH/) , see if the following way of reinstalling Grub on this system appears correct (I have a big doubt (see question marks below) regarding the device name I need to provide when calling grub-install):

```
sudo apt-get update
sudo apt-get install lvm2

sudo mount /dev/mapper/vg00-lv00_root /mnt
sudo mount /dev/nvme0n1p2 /mnt/boot
sudo mount /dev/nvme0n1p1 /mnt/boot/efi
sudo chroot /mnt

apt-get install grub-efi-amd64
grub-install --efi-directory=/mnt/boot/efi --boot-directory=/mnt/boot /dev/nvme0n1??????????????

update-grub

exit

sudo umount /mnt/boot/efi
sudo umount /mnt/boot
sudo umount /mnt
```

---

### Post by oldfred on 2018-12-12
Do not really know LVM. Is it also encrypted? You need that driver & mount with passphase.

Since you have separate /var I would also mount it. 

        chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

---

### Post by phitolo on 2018-12-12
There is no encryption present.

Can I have your opinion on whether /dev/nvme0n1 (the SSD drive) is the correct device name for grub-install? Thanks.

---

### Post by oldfred on 2018-12-12
Whether old BIOS/legacy or newer UEFI, you always specify a drive.

But with UEFI, Ubuntu's grub only installs to first ESP, normally sda (with my systems). But it knows NVMe drives & will install UEFI boot files into the ESP on the NVMe drive.
With my system every test or second install to sdb or external drive, always installs to sda's ESP and overwrites my main working install's /EFI/ubuntu folder. Quickly learned to backup ESP. But real difference is only one line in /EFI/ubuntu/grub.cfg with UUID & drive/partition of full grub.cfg in the install, so now I normally just edit that back to main working install's partition.

---

### Post by phitolo on 2018-12-14
OK, so thanks everyone who tried to help. I tried the manual install of grub which didn't work. I than managed to have boot-repair work, which told me in the end that it was able to repair the system but I could still not boot the system. In the end I chose to do a clear CMOS (before I just did a restore to default values) and by magic that solved the problem, I was able to see the UEFI hard disk in the firmware again and select it as default boot device, and eveything booted fine form there on.
I'm still not sure what the problem was the lesson I learned is that, while old BIOS may have had some limitations they had almost no bugs, while new firmwares have more features but also more bugs.

---

