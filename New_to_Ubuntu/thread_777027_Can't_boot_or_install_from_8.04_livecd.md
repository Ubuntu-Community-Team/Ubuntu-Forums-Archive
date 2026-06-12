---
title: "Can't boot or install from 8.04 livecd"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by aberry5555 on 2008-05-01
Hi there people. I have a little bit of a problem with trying to get linux to work on my pc, at the moment I'm entirely stuck and don't know where to go next :S. Basically I started off by burning myself a copy of the 64 bit live cd (the disk verified on burn) and rebooting my pc with the CD in the drive. The Ubuntu options menu comes up fine, I choose a language and then get to the main screen. OK, so I know I want to install it, not really boot it, and I have a completely blank HDD in my computer at the ready. I choose install and, after a few minutes of the cd drive whirring and the Ubuntu splash screen bouncing around and then starting to load, it hangs. The loading bar stops just short of the end, the HDD access light flashes a couple of times and then the CD drive spins down.. 

So I look in to it a little further and change the boot options, removing the

```
quiet splash --
```

options and trying to boot up from there. After doing this I find out that my pc loads all the way up to "Starting hardware abstraction layer HALD" and then hangs... I've tried it in both normal, non-install mode and in install mode and it doesn't seem to make the slightest bit of difference. Also, on occasion after displaying "starting hald", it will display something like "ata3 hot unplug error, read error" but not just with ata3, I've had the same error with "ata5" and "ata7" so far and I can assure that I've not been unplugging anything. Just to test this theory, though, I disabled what I thought was one of these ata devices (my PATA hard-disk) but that didn't help. I also tried using the -noacpi and -nolacpi options with no luck with both/either.

As well as this problem I have tried to install using wubi, on to a windows partition and have had problems too, probably the same problem I think. When I installed with wubi it wasn't with the same disk, it was with the image mounted within windows. On both 32 and 64 bit versions of 8.04 I manage to install it from windows, reboot and choose to start Ubuntu, get in to the GUI but then the computer freezes when it says "Checking disks" or something similar... I have a feeling that this is probably the same issue, but I have no idea how to get any further than this. I think, although I'm not sure, that the last version of Ubuntu was booting into livecd OK so I really don't know whats happening with this.

I'm not by my PC atm but I can give you some brief specs of my PC: I'm using an AMD3800+ CPU, an ati X800 pro graphics card, 1 GB of memory, 3 sata hard-drives and a PATA hard-drive. Off the top of my head I can't remember exactly what kind of motherboard I have, though safe to say it's not exactly a top of the range one.. I think it's made by a company called "Winfast" which is a subsidiary of foxconn and it's a fairly bog standard board. It's running an nvidia chipset, can be used for sli, has a 300mb/s sata controller on-board and that's all I could tell you till I got back to my pc.

Any thoughts on this would be greatly appreciated, thanks in advance

Alex.

---

### Post by zvacet on 2008-05-01
Check [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") and check disc integrity (it is option when you boot CD).If you find any errors and you still have iso image download same version with torrent and point download to te folder with your isoimage.Torrent will just check your iso for corrupted files and replace them ( if any) with good ones.Check md5sum again,burn at lower possible speed,check disc integrity and if everything is O.K.go for install.

---

### Post by aberry5555 on 2008-05-01
I'm almost certain the disk image is ok, as I've downloaded two images (not torrents, bog standard http downloads), one 32bit and one 64bit version, and have that same wubi problem using both while the images are mounted on my pc, rather than burnt. I also verfied the disk when I burnt it, but I havn't used the disk check option in Ubuntu yet.. I'll check this when I get back to be sure and I'll let you know. In the meantime does anyone have any other ideas?

---

### Post by aberry5555 on 2008-05-02
Anyone have any ideas?

---

### Post by Michael.Godawski on 2008-05-02
Did you try to install via the alternate CD. It uses the text based installation and it never failed for me when I was fighting with the Live CD. 

Here is a guide:
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by Xiong Chiamiov on 2008-05-02
As a side note, it seems to me that you're *less* likely to get a corrupted iso through bittorrent, since it hashes every chunk as you go...

---

### Post by powerjim on 2008-06-01
I'm having the same damn Freeze on * Loading Hardware Abstraction Layer Hal either from booting a Live CD or Booting after install with the Alternate.

I have tried Hardy, Hardy alternate, Gusty and even Suse with no luck. Fedora booted but... I don't like Fedora...

My hardware configuration is :
Motherboard : MSI 975X Platinum
CPU : Intel Core2 Duo
HD Drives : 1xIDE(250GB) + 2xSATA(500GB)... want to Raid that! :)
Video : Geforce 7600GT

I'm trying Mint this afternoon... If nothing works i'll be back to Windows... :(

---

### Post by sayakb on 2008-06-01
Press F4 on LiveCD choice screen and select Text mode install/Safe graphics mode.

---

### Post by chriszuma on 2008-09-24
I'm having this exact same problem installing Hardy on a MSI Fuzzy 945GME1 board with Intel Core 2 Duo T7200, 1gb RAM, and Samsung 80gb SATA drive. 

I tried the text-based installer, and it installs fine but I get the same "Starting Hardware Abstraction Layer hald" freeze when I try to boot from the hard disk.

And here's a stumper: I successfully installed Dapper and it works perfectly fine.


Does ANYBODY have an idea how to solve this?

Thanks,
  ~Chris Hammond

---

### Post by sneeks on 2008-09-24
please dont quote me on this but after having the same sort of probs on some dell base units i found a thread that i can no longer find that said to change the hard drive config in the bios,eg change it from the raid config.
i will try to find the thread and post it as soon as i can.

---

### Post by sneeks on 2008-09-24
> **sneeks said:**
> please dont quote me on this but after having the same sort of probs on some dell base units i found a thread that i can no longer find that said to change the hard drive config in the bios,eg change it from the raid config.
i will try to find the thread and post it as soon as i can.

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Desktop_Wont_Boot](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Desktop_Wont_Boot)

---

### Post by chriszuma on 2008-09-24
I solved it!

I went through toggling random BIOS options, and when I changed "APIC" to Disabled, it booted perfectly!

Apparently it's some multiprocessor interrupt optimization thing, but for some reason Hardy just really doesn't like it. Turned it off and I'm good to go.

I hope this helps someone in the future, because this was a really frustrating problem.

  ~Chris Hammond

---

