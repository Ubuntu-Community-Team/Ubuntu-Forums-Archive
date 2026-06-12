---
title: "Cannot get wireless working"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Bujungo on 2008-11-02
I'm new to ubuntu and I have no idea what I'm doing. I have scoured the threads and can't quite find something that matches up to my problem. I have my wireless card installed, it lights up, and it picks up wireless networks, but it can't connect to any of them, secured (mine) or otherwise. It's a really old laptop that my dad was going to get rid of and I wanted to play around with. It's very temperamental to begin with, but the card and everything worked when XP was on it.

Here are the output of iwconfig and lspci

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:270 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:04.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
00:08.1 Communication controller: ESS Technology ESS Modem (rev 12)
01:01.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)
06:00.0 Network controller: Broadcom Corporation BCM43XG (rev 01)

---

### Post by stalker145 on 2008-11-03
I don't know if it's much help to you, but I found [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") on the Hardware Compatibility page.

If it works, great! If not, I'll check back here to see if I can help any further.

By the way, is this a prebuilt computer? If so, what make/model are we dealing with? It may be easier to find info if we search that way.

---

### Post by Bujungo on 2008-11-03
Yeah that's still a little confusing to me. But if it helps, its an old HP Pavilion N5420L 384MB RAM, Intel Celeron 800MHz, 10GB hard drive. The wireless card is a Linksys WPC300N.

---

