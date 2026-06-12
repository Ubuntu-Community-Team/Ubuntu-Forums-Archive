---
title: "Boot order"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by Grapeheads on 2008-10-19
Hi. I have Ubuntu installed on a external hard drive. When I boot up and get passed the bios screen, I'm given the option to boot into Vista or Ubuntu. My question is how I control this screen. How do I make it so my system just boot into Windows, or Ubuntu and bypass this screen? I've tried setting my bios option to read first from my main 250 gb hard drive instead of my external, and vice versa but it still gives me the same screen. Thanks for the help. 

System Specs:

    * Intel® Pentium® Core™ 2 Duo processor T5550
      1.67 GHz | 2 MB L2 cache | 667 MHz FSB
    * 17-inch Ultrabright™ WXGA+ TFT display
    * Intel® PM965 chipset
    * NVIDIA® GeForce® 8800M GTS with 512 MB of GDDR3 Discrete Video Memory
    * HDMI
    * 1.3 Megapixel webcam
    * 3072 MB DDR2 memory
    * 250 GB SATA hard drive
    * 8X Multi-format Double Layer DVDRW 
    * 5-in-1 Memory card reader
    * 56K ITU V.92 ready Fax/Modem
    * 10/100/1000 Gigabit Ethernet LAN
    * 802.11n wireless LAN
    * Bluetooth
    * Windows Vista™ Home Premium

---

### Post by alzie on 2008-10-19
I'm assuming you're using Grub.

Install "start up manager " from the repositories and just select Vista to be the default.

I hope this helps

---

### Post by northern lights on 2008-10-19
From within Ubuntu, you can access the file that's behind the bootloader menu and it's behavior - /boot/grub/menu.lst

Make a backup```
cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```and edit it to your needs ```
gksu gedit /boot/grub/menu.lst
```

[GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html")

---

### Post by Grapeheads on 2008-10-19
I'll try it. Does start up manager work with other distros? Thanks alzie.

---

### Post by alzie on 2008-10-19
I'm not sure what you mean by "other distros". 

If you have several OS's that you want to organize then I think you'll end up having to edit your Grub.  If you mean the number of Ubuntu kernals you have showing in grub, yes you can limit the number.  Mine is set to show the 2 most recent with recovery mode and mem test available.

I hope that helps you.

---

### Post by northern lights on 2008-10-19
> **Grapeheads said:**
> I'll try it. Does start up manager work with other distros?
"StartUp Manager" or SUM is a GUI to alter grub, grub2, or usplash settings. It works with Debian-based distributions of which Ubuntu is one.
I'd prefer the unlimited control you get from manual editing, but as for a GUI option, this is the only one out there and works fairly smoothly under Ubuntu.

---

