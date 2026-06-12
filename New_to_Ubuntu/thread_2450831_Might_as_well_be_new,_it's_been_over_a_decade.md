---
title: "Might as well be new, it's been over a decade"
date: 2020-09-21
forum: New to Ubuntu
---

### Post by caztastrophe on 2020-09-21
Hi y'all,

As the title says, last time I played with Linux at all was probably 11 or 12 years ago. There were some years in there where I didn't have a computer at all, and some when I had a laptop I was too afraid to do something wrong and lose use of it.

Now I have a 1 TB SSD on the way to pop into my desktop, planning an Ubuntu install on it. Going to leave Windows on the current hard drive as a just-in-case (I tend to have rough luck when building/installing things for myself, though I can help others without much issue somehow).

Mostly just saying hello at this point - but any generally useful advice is welcome.

---

### Post by oldfred on 2020-09-21
Is system newer UEFI or older BIOS?
If new UEFI bit more complicated as UEFI has more flexibility. Read as install options and configuration, making it seem difficult, but not really much more if you research it first.

Lots, perhaps too much as not all applies, in link below in my signature.

What brand/model system? What video card/chip?
Is UEFI/BIOS most current? And have you updated SSD firmware to most recent.

With separate drive you need to partition in advance and use newer gpt whether UEFI or BIOS system. If UEFI you need an ESP - efi system partition and if BIOS a bios_grub partition.
Ubuntu's Ubiquity installer only installs grub2 boot loader to first drive's ESP. That can work, but many suggest disconnecting or in UEFI change Windows drive to disabled, temporarily.
Otherwise a work around on install or reinstall of grub to Ubuntu drive, if you want SSD totally separate from Windows drive. 

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive.

---

### Post by TheFu on 2020-09-22
Physically disconnect the current drive if you have bad luck doing installs.  It is really easy to make a bad choice and wipe MS-Windows.  There are some difficulties this method would cause for making switching between both OSes, but it will be safer.

OTOH, that wouldn't be too bad. These days Linux has good-to-excellent solutions for pretty much everything for which people used to claim they needed Windows.  Windows just isn't necessary anymore for 98% of us.  

I still use Windows for 3 things. There are replacements for those on Linux, but I'm less than thrilled by the options and a little stubborn. ;)  More flexible people can switch 100%.

1TB for Linux?  Wow. That's overkill for the OS and applications. 
```
$ df -Th
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   17G  9.0G  6.9G  57% /
/dev/mapper/vgubuntu--mate-home ext4   12G  6.0G  5.3G  54% /home
```
I'm using ... less than 40G total on my desktop. I keep media files on a network server. From the information above, 
the OS is using 6.9G and my data is using 5.3G.  This is an OS I've migrated from 10.04 --> 12.04 --> 14.04 --> 16.04 --> 20.04. It was 32-bit until June of this year. With 20.04, I converted to 64-bit. I skipped 18.04.

---

### Post by Paddy Landau on 2020-09-22
I purchased a new computer, because my old one broke.

I installed Ubuntu, not Windows. I created a virtual machine (on Virtual Box) running Windows, using the license from my old and now-defunct machine.

That way, I have a functioning Ubuntu box, with Windows for the rare occasion when I need it.

---

