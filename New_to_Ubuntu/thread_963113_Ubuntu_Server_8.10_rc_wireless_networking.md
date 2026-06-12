---
title: "Ubuntu Server 8.10 rc wireless networking"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by TechWraith on 2008-10-29
Hi there, I'm trying to set up an office server for my web design business. Something I can use to test out my clients website, and something that I can use as a development server for ruby on rails.

I've installed Ubuntu Server 8.10 with LAMP and samba, but I need some help connecting to my wireless network. Unfortunately, the box that I'm using for a server is a few years old and doesn't have an ethernet port. All that I have is the wireless card.

I'm brand new to linux, so a really dumbed down tutorial would be very much appreciated.

Thanks,
TechWraith

---

### Post by igknighted on 2008-10-29
could you run the command 'lspci' (no quotes) and post the results so we can see exactly what type of wireless card you have?

---

### Post by TechWraith on 2008-10-29
> **igknighted said:**
> could you run the command 'lspci' (no quotes) and post the results so we can see exactly what type of wireless card you have?

```

00:00.0 Host bridge: Intel Corp. 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corp 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corp 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corp 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corp 82801BA IDE U100 Controller #1 (rev 05)
00:1f.2 USB controller: Intel corp 82801BA/BAM USB controller #1 (rev 05)
00:1f.3 SMBus: Intel corp 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 USB controller: intel corp 82801BA/BAM USB controller #1 (rev 05)
00:1f.5 Mutimedia audio controller: Intel Corp 82801BA/BAM AC'97 Audio Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV5m64 [RIVA TNT2 Model 64/Model 64 pro] (rev 15)
02:0a.o Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless Lan Controller (rev 20)
02:0b.0 Communication controller: realtek Semiconductor co., ltd. RTL-8139/8139c/8139c+ (rev 10)
02:0e.0 FireWire (ieee 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)

```

There ya go, any help is appreciated!

---

### Post by TechWraith on 2008-10-30
Just thought I'd check to see if anyone could help. I hate asking so frequently, but I really need to get this up and running by the morning...

As always, any help is appreciated!

---

### Post by brandoncolorado on 2008-10-30
So you want the server to act as a wireless access point as well?

You did this with LAMP:
[http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html)

I am blocked from this link on my computer here at home, but I think this should help with the wireless access point bit.
[http://tips.linux.com/article.pl?sid=06/07/10/1729226&tid=100&tid=35](http://tips.linux.com/article.pl?sid=06/07/10/1729226&tid=100&tid=35)

and this may point you in the right direction
[https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)

---

### Post by TechWraith on 2008-10-30
nope, I just want to access my wireless network from my ubuntu server. I don't know the commands to connect...

---

### Post by brandoncolorado on 2008-10-30
Ohh, well hopefully this helps.  If you have the basic setup:
[https://help.ubuntu.com/8.04/internet/C/wireless-connecting.html](https://help.ubuntu.com/8.04/internet/C/wireless-connecting.html)

If you want to use the terminal:
[https://help.ubuntu.com/8.04/internet/C/troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html)

Hope that helps some.

---

### Post by TechWraith on 2008-10-30
Well darn, just a little bit too late... I'm installing the full ubuntu install right now and configuring it to work like a server. I think this will work.

Thank you all for the help!

---

### Post by TechWraith on 2008-10-30
Well darn, just a little bit too late... I'm installing the full ubuntu install right now and configuring it to work like a server. I think this will work.

Thank you all for the help!

---

### Post by TechWraith on 2008-10-30
> **TechWraith said:**
> Well darn, just a little bit too late... I'm installing the full ubuntu install right now and configuring it to work like a server. I think this will work.

Thank you all for the help!

DOH! Sorry for the double post!

---

