---
title: "Updating Drivers in Linux"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by adobrakic on 2008-06-20
I wanted to update my graphics, but the manufacturer's website doesn't have it. Is there some alternative I can do? Also i downloaded the driver for my audio device, but i'm not sure if it's installed.

I have a s3 prosavage ddr graphics card 
(and i tried going here for the driver - [link]("http://www.s3graphics.com/en/resources/drivers/legacy/software_archive.jsp#id_420drv"))

and a realtek ac'97 audio card
(got the driver here - [linky]("http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false")) -- there was an install file in there, but when i opened it, some alsa folders just appeared, so i'm not sure if it's installed or not. any help?

---

### Post by sdennie on 2008-06-20
Is there a reason you feel you need updated drivers?  With few exceptions, Windows drivers aren't at all useful under linux which would explain why you can't install those two things.

---

### Post by cariboo on 2008-06-20
For all intents and puposes the savage driver included in this distribution is probably newer that the one on the manufacturers web site.

I would say the same thing about your sound card, you're using windows terminology as far as the type of sound card you've got, it would be better if you gave use what the output of **lspci** is, so we could better help you.

In my experience Realtek is really well supported in linux, and every one of their products has been very easy to set up.

What problems have you been having with your video and audio cards, that you need a driver update?

Jim

---

### Post by adobrakic on 2008-06-20
> 
What problems have you been having with your video and audio cards, that you need a driver update?


I recently tried playing a game, and it said that i need at least 12mb of available video memory. I'm absolutely positive that i have more than that. :x

lspci:
```

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

```

---

