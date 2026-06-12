---
title: "Desktop effects with all in wonder 128 pro?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by tbma2008 on 2008-06-25
Has anyone had any luck with any desktop effects with this card?  I get the "desktop effects could not be enabled" when changing to normal.  I know some cards are not compatible but is there anyone out there with this card and has had luck?

---

### Post by overdrank on 2008-06-26
> **tbma2008 said:**
> Has anyone had any luck with any desktop effects with this card?  I get the "desktop effects could not be enabled" when changing to normal.  I know some cards are not compatible but is there anyone out there with this card and has had luck?

Hi and welcome, please do not make multiple threads on the same subject. I had a similar  card and could not enable the desktop effect so I would believe on that model would be the same. Could you post the output of the command ```
lspci 
```to verify the model of the graphics card. Look for VGA in the output of that command.

---

### Post by tbma2008 on 2008-06-26
i apologize.... i wasnt sure if i should post twice being that it might fit both categories.  But thanks for the reply... here is the results


```
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:05.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
00:06.0 Communication controller: Agere Systems 56k WinModem (rev 01)
00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0b.0 USB Controller: NEC Corporation USB (rev 41)
00:0b.1 USB Controller: NEC Corporation USB (rev 41)
00:0b.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:0c.0 RAID bus controller: Promise Technology, Inc. PDC20276 (MBFastTrak133 Lite) (rev 01)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
```

---

### Post by Canis familiaris on 2008-06-26
> Pre-radeon - Cards older than the original Radeon 7000 (such as the Rage cards) have no 3d acceleration available.

Source: [https://help.ubuntu.com/community/RestrictedDrivers/ATI](https://help.ubuntu.com/community/RestrictedDrivers/ATI)

---

### Post by philinux on 2008-06-26
I had one of these, the 128 rage and although under win me I could play pc games games glxgears only gave about 50 fps. I know this is not a real benchmark. 

There is no way you'll get desktop effects with this card.

My old machine was a 1999 pentium 3 and it ran ubuntu well for internet and mail but for anything else very slow.

New machine runs great.

---

### Post by tbma2008 on 2008-06-26
thank you i finally have my answer

---

### Post by Rocket2DMn on 2008-06-26
Here are two links that may interest you:
enabling CF on open source "ati" cards: [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
compiz-check script: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

