---
title: "Booting from USB on a Mac"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by sakraft1 on 2012-01-07
I know I can boot from my USB flash drive in windows by pressing f12 on startup, but is there a simple way of doing the same thing on a Mac? I have both and Intel MacBook Pro and a Mac G5. When I hold down option while starting up I can only see my OS X drive and boot from that.

---

### Post by 2F4U on 2012-01-07
In theory, you should be able to boot from a usb drive by holding down the alt key. However, on my MacBook that doesn't work. I can hold down the key as long as I wish but only get OSX. It works fine when a CD is in the drive but not when a usb drive is attached.

---

### Post by sakraft1 on 2012-01-07
Yeah, I've had the same experience. I've booted the MacBook from CD before but can't quite figure out USB (which is much faster on my PC).

---

### Post by jjex22 on 2012-01-07
how are you creating the USB's? unetbootin won't work for mac - did you create the sticks using the dd command from terminal? It does sometimes take a couple of goes to appear with pressing alt - I find it's best to restart once after dd'ing, mount the drive and restart the mac - hopefully it'll show up this time? 

Failing that try installing rEFIt first - I don't have much problem getting dd'ed stick to show up, so maybe it's rEFIt making it easier and you'll need it anyway - download and install the [dmg]("http://sourceforge.net/projects/refit/files/rEFIt/0.14/rEFIt-0.14.dmg/download") then try again pressing alt on boot?

sakraft1 - your powerPC is different - it uses open firmware instead of efi, it also doesn't have an intel chip, so you need a PPC version - I'd recommend using the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD#A32-bit_PowerPC.2A.2A") and doing a net install. 

Once you've got a PPC version dd'd to your usb disk, you need to get into openfirmware by holding down 

> 
cmd+opt+O+F


this should bring you into openfirmware - nothing like a bios, it should look like an inverse terminal. use the command
```

dev / ls

```
to find where your USB is connected, then you need to tell openfirmware to boot yaboot - the bootloader used for PPC linux (no GRUB) The format of this is
```

boot usb0/disk@1:2,\\yaboot

```

This should be able to boot linux for install. please note that you may have to change the numbers to find it - in the past this has taken me a while! start with usb0 and go up incrementally - if still not found try changing the partition number on the disk - 1:2 to 1:1 etc - it may take a few guesses/systematic searching but it will work - I use this method on my usb 1.1 g4 emac - not had any problems other than finding the yaboot loader!

Edit: Welcome to the forums!
Edit 2 - for the G5, maybe concide using 10.04 or 11.10 Lubuntu to get the best performance - for lubuntu install a base system then use the command
```

sudo apt-get install lubuntu-desktop

```

---

