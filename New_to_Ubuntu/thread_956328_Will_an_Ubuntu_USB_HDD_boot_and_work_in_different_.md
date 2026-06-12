---
title: "Will an Ubuntu USB HDD boot and work in different computers?"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by peril62 on 2008-10-23
I have installed Ubuntu 8.04 in an external USB HDD and after modifying the menu.lst entry (hd1,0) for (hd0,0), it boots and works perfectly leaving my DDimension 8300 hard disk with XP ubsolutely untouched. My question is: can I plug my Ubuntu USB HDD in different XP computers (assuming they can boot from USB) and get them working with Ubuntu so their XP hard disks remain untouched but I get full mobility for my desktop and files? I have read something about possible problem with graphic card drivers; can´t I use a standard driver for all cards (assuming just basic usage, no games or extensive graphic programs)?
Thank you.

---

### Post by DrMelon on 2008-10-23
You would probably have to install GRUB on their machine.

---

### Post by Crandom on 2008-10-23
Of course you can! I do this all the time with a usb drive. You do not need to install grub on their machines, just boot from the usb hdd at bios instead of the primary hdd. Things that need propriortory drivers like graphics cards and ndiswrapper won't work if you want to keep it mobile. You should have grub installed on your usb hdd.

Ubuntu is all about hijacking other people pc's and then looking at the shock on their faces :)

---

### Post by Hexagoon on 2008-10-23
Yeah it would work, on similar machines, ubuntu will automagically load the correct modules to fit the machine.

If you have grub installed on the usb-disk(?), it could cause some problems, but in that case it's just to reconfigure it directly inside grub.

---

### Post by beanco on 2008-10-23
I really like this idea...

Just how long does take to boot up this way?

I mean... I teach in a HS where the administration is unwilling to convert to linux out of fear.. the IT guys do not want to have to deal with a bunch of teachers running down crying that they cannot use linux...

so I coudl get a nice sized external, usb hdd and just boot up ubuntu any old time? 


robi

---

### Post by Hexagoon on 2008-10-23
With a usb 2 compatible hdd and usb 2 controller you will get almost the same speed as with a standard drive. I don't see that the boot-up time should be longer, but file copy speed can take a little more time...

If it is a usb 1 HDD OR controller, it will get pretty slow :P

---

### Post by djbushido on 2008-10-23
Just to let you know, I run my ubuntu entirely off USB-HDD. When installing, I unplugged all my hard drives, installed to what the installer said was a SCSI disk, and i haven't had to change anything on mine or anybody else's computer to get it to boot fine.

It should work to run entirely off of USB-in my experience, you wouldn't need to do anything with any other drives.

---

### Post by timbim on 2008-10-23
Probably wouldn't be able to connect to the network, so you'd be left without internet, server files etc, so may not be ideal!

---

### Post by Hexagoon on 2008-10-23
> **timbim said:**
> Probably wouldn't be able to connect to the network, so you'd be left without internet, server files etc, so may not be ideal!

Uh, how come? Just think of it like a live cd, you always get network :)

---

### Post by peril62 on 2008-10-23
I use an old SATA 60Gb USB HDD taken from an obsolete Toshiba laptop and installed in an external box. I connect it to my XP Dell through USB 2.0. To boot my Dell I press F12 at startup and from the appearing menu select boot from USB drive and get inmediately the Ubuntu start menu. To get to the username menu approximately the same time than when booting Windows from the HD. From the username menu to full functional Ubuntu desktop much quicker than in Windows. I have maintained my Windows Dell absolutely unchanged so if I do no press F12 at startup, it boots Windows in the internal HD as usual with no notice of the Ubuntu USB.

---

