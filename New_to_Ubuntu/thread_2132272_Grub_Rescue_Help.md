---
title: "Grub Rescue Help"
date: 2013-04-04
forum: New to Ubuntu
---

### Post by TehTripleB on 2013-04-04
I have a Toshiba Laptop. A while back I was dual booting Ubuntu 12.04 and Windows 7, although recently I wasn't using Ubuntu for anything so I decided to delete the Partition and forgot to change the bootloader. My computer ran fine until I had to restart it. Then grub rescue. 
I've tried looking up various commands and it gives me the Unknown command notification. I've also tried booting from cd but that gave me no results. I looked in the bios and it didn't even give me an option to boot from cd. It does have a boot from usb one so I tried putting Ubuntu onto a flashdrive, but it told me to remove all discs and other media when it was the only thing plugged into my computer. 
Any other help would be appreciated.

---

### Post by Cheesemill on 2013-04-04
You need to boot from your Windows 7 DVD, this will let you repair the Windows boot loader.

If you can't boot from a DVD for any reason, it's possible to create a bootable USB from your Windows installation media to use instead.

---

### Post by AndyOpie150 on 2013-04-04
oldfred saved me from the very same situation with this:
[ Boot-Repair Disk]("http://sourceforge.net/p/boot-repair-cd/home/Home/')

You will need to use an alternate computer to download and burn to a cd. Then load into tray. Pick the popup option that "will fix the most common errors".

---

### Post by TehTripleB on 2013-04-04
> **Cheesemill said:**
> You need to boot from your Windows 7 DVD, this will let you repair the Windows boot loader.

If you can't boot from a DVD for any reason, it's possible to create a bootable USB from your Windows installation media to use instead.

I don't have a windows 7 DVD. My laptop had it pre-installed.

---

### Post by Cheesemill on 2013-04-04
If you have a Ubuntu Live CD you can boot from you can fix your bootloader with the following commands...
```
sudo apt-get update
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by TehTripleB on 2013-04-10
Late reply from me, woo! Sudo is an unknown command. Is there another command for Grub Rescue that does the same thing?

---

### Post by Cheesemill on 2013-04-11
You cant fix your machine from the grub prompt. You need to boot from a Ubuntu Live CD and *then* run the commands I gave you.

---

### Post by TehTripleB on 2013-04-11
I believe I have said that I tried a live cd? It was the first thing I tried, and no response. I've tried changing the boot order as well, there is no option for cd.

---

### Post by oldfred on 2013-04-11
Best to boot a flash drive or DVD. Some systems get so locked up that you need a total cold boot, including removing battery and dissipate capacitors.

 Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

      
 Laptop full power reset. post #4 hold power on switch
[http://ubuntuforums.org/showthread.php?p=12401315](http://ubuntuforums.org/showthread.php?p=12401315)

---

### Post by TehTripleB on 2013-04-11
> **Cheesemill said:**
> If you have a Ubuntu Live CD you can boot from you can fix your bootloader with the following commands...
```
sudo apt-get update
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Play around with boot options and it booted to cd. Trying this now. Will there be anything further I have to do after the codes? I can I go back on my merry way with windows 7?

---

