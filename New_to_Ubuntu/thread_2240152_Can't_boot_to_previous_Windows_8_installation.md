---
title: "Can't boot to previous Windows 8 installation"
date: 2014-08-18
forum: New to Ubuntu
---

### Post by enemyviolent on 2014-08-18
Ever since my install of Ubuntu Gnome 14.04, I haven't been able to boot into Windows 8 no matter what I do. I've tried to use the Startup Repair option of my Windows 8 disk, use the command line therein to fix the MBR, and use the Boot Repair app inside of Ubuntu to fix it, which got GRUB going but didn't give me an option to boot Windows 8.

Here's the URL that Startup Repair gave me: [http://paste.ubuntu.com/8079471/](http://paste.ubuntu.com/8079471/)

I plan on using Ubuntu as my primary OS but I still need Windows for a few small things now and then. I would be grateful for any help I could get with this problem.

---

### Post by Gordonbp531 on 2014-08-18
If you activate the Boot menu on startup, does it show an entry for Windows 8? If so, try that.
You'll need to consult the documentation for your particular make of computer to find out how to do that.
(That's what I use on my Lenovo U410....)

---

### Post by enemyviolent on 2014-08-18
It shows an entry for my solid state, and one for my regular hard disk, but both lead to Ubuntu.

---

### Post by Mark Phelps on 2014-08-18
The report shows no Windows loader files on sdb -- and without those, it can not boot.

You need to do the following:
1) Disconnect all but your Windows drive
2) Boot with the Windows drive connected but from the Win8 optical disk
3) Run Startup Repair three times -- that's right, three times

When done and you reboot, you should go straight into Windows.

---

### Post by enemyviolent on 2014-08-19
After the first Startup Repair, I get "Startup Repair couldn't repair your PC". At first I thought it was because I was using a USB, but I've found my DVD and it still does this.

---

### Post by oldfred on 2014-08-20
You have what looks like a BIOS install of Windows, but it does not have the typical 100MB boot partition with bootmgr & BCD. And the Windows drive now is showing it is gpt partitioned.

Windows only boots from gpt with UEFI, but then would need an efi partition and a msftres unformatted partition just before the NTFS boot partition. Not sure how drive could have been converted to gpt. But it needs to be MBR(msdos) for Windows to boot in BIOS mode.

If you installed Windows on the hard drive when the SSD was still the boot drive in BIOS, then the now missing 100MB boot partition was on the SSD. Your LVM install of Ubuntu is always a full drive install, so even if the 100MB partition was there it was overwritten. Using Something else with manual partitions probably would have shown you another partition.

You can convert gpt back to MBR and then create the BCD in your Windows install to fix it. Or the autofix three times should then work.

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

### Post by enemyviolent on 2014-08-20
gdisk says "Found invalid GPT and valid MBR; converting MBR to GPT format in memory." Tells me to exit if I don't want to convert MBR partitions to GPT. I think that's the opposite of what I want, so I exited.

I've now got it to the point where GRUB2 recognizes the Windows install, but trying to boot to it says "The Boot Configuration Data for your PC is missing or contains errors."

---

### Post by oldfred on 2014-08-20
The gdisk is for gpt partitioned drives. And starts or assumes you want gpt.
You have to follow the instructions in the conversion link.

[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

Be sure to backup partition table first.

While grub may see Windows as long as you have gpt, Windows will not work. Windows does work with just the backup gpt partition table as when Windows converts a drive from gpt to MBR, it always leaves the backup gpt table and then Linux does not work.

---

