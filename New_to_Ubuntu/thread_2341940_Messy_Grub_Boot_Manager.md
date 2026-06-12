---
title: "Messy Grub Boot Manager"
date: 2016-11-02
forum: New to Ubuntu
---

### Post by Nebelhom on 2016-11-02
Hi Folks,

I have just installed a ubuntu 16.04 LTS dual boot on my TravelMate P273-MG Laptop with Win8.1.

I had play around a bit with the BIOS (Changing boot order mostly, I installed under UEFI) until I could:

1. Install Ubuntu in LiveUSB and
2. Get grub to work so I could choose it

due to UEFI.

Everything is working fine, except that my grub manager looks very messy (see attached image).

Does anyone of you know how to clean that up? I am a bit afraid to touch it as it essentially works and it took me so long to get it to work ;)

Thanks a lot for all the help :)

---

### Post by &amp;KyT$0P# on 2016-11-02
I'm not sure I understand what you want to do.  Assuming you want to remove all those entries except Ubuntu related entries -

Open [FONT=Courier New]/etc/default/grub[/FONT] as root, in a text editor, and add this line -
```
GRUB_DISABLE_OS_PROBER=true
```

Then run this in a Terminal to save the changes to GRUB -
```
sudo update-grub
```
Reboot and the unwanted entries should be gone.

---

### Post by oldfred on 2016-11-02
With Windows 8 or later grub only boots working Windows. Best to keep Windows entry in UEFI or just use the UEFI entry.

I also turn off os-prober, but then add any entries I want to keep in 40_custom.
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

Best to backup current grub.cfg with all entries, before turning off os-prober.

 sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup 

Then you can manually copy any entries you do want from backup into 40_custom.

---

