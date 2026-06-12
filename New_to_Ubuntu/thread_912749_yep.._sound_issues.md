---
title: "yep.. sound issues"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by adobrakic on 2008-09-07
alright, well I followed [these](http://ubuntuforums.org/showthread.php?t=776739) instructions to make sound work in more than one app. now, sound doesn't work in any apps. yay! When i go to prefs > sound and try to test something, i get these error:

[img]http://img182.imageshack.us/img182/1488/screenshotgnomesoundprogc6.png[/img]

---

### Post by Crafty Kisses on 2008-09-07
Post the results of this command: ```
lspci
```

---

### Post by adobrakic on 2008-09-07
```
ado@ado-desktop ~ $ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
ado@ado-desktop ~ $ 

```

---

