---
title: "need help getting smart bro to work under 10.04 pls"
date: 2010-07-17
forum: Philippine Team
---

### Post by joey129 on 2010-07-17
Just bought a smartbro broadband kit. its all black and says model:WM66A at the back..

I tried this: [http://ubuntuforums.org/showthread.php?t=1506375&highlight=smartbro+zte+mf627](http://ubuntuforums.org/showthread.php?t=1506375&highlight=smartbro+zte+mf627) not sure if mine is a zte627 but it didnt work

then i tried this one (see post 18 ): [http://ubuntuforums.org/showthread.php?t=1506375&highlight=smartbro+zte+mf627](http://ubuntuforums.org/showthread.php?t=1506375&highlight=smartbro+zte+mf627) but instead i got my usb-modeswitch from synaptic because it was a newer version.. this didn't work either..

i noticed that after installing usb-modeswitch, the cd icon labeled "SmartBRO" which used to appear when i plugged in the usb no longer shows up

this is the lsusb output:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 1c9e:f000  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

thanks. i hope you guys can help me get this thing to work :/

---

### Post by jepong on 2010-07-18
try mo from a no power state (naka-off) plug your broadband device then power on you PC/Laptop.

---

### Post by stormsurge on 2010-07-21
You can try this. This worked fine with me and take note, I did not change any settings in my Ubuntu. I tried using a Smart Buddy SIM in my Smart Bro Plug-it and it automatically worked.

---

### Post by joey129 on 2010-07-21
thanks guys, i'll try those suggestions out..
re: the smart buddy sim, you ultimately end up paying the same for surfing in the end, right? as in, the smart bro sim doesn't have any special attributes that makes surfing cheaper or anything, right?

---

### Post by stormsurge on 2010-07-21
> **joey129 said:**
> thanks guys, i'll try those suggestions out..
re: the smart buddy sim, you ultimately end up paying the same for surfing in the end, right? as in, the smart bro sim doesn't have any special attributes that makes surfing cheaper or anything, right?

You are right! Same rate. P10/30mins.

---

### Post by kstella on 2010-07-21
I have the same usb modem, model:WM66A. Eto yung bago na all-black, di ba? The instructions you linked to are for the old one with the orange piping.

Nasubukan ko nang mag-smartbro gamit ang black and orange modem at gumana naman. Pero hindi rin gumagana sa akin ang bagong all-black modem. :/

When I tried following the same instructions, the prompt did not recognize the device; "Any" imbis sa "ZTE..." yung lumabas. Paano ba malalaman ang model niya, kung zte or huawei ba siya?

---

### Post by kstella on 2010-07-21
Okay, with a little googling, nalaman ko na Longcheer WM66A ang model ng bagong modem. ([http://www.tipidpc.com/viewtopic.php?tid=220129&page=1](http://www.tipidpc.com/viewtopic.php?tid=220129&page=1))

Turns out that someone posted instructions for getting a Longcheer modem to work back in 2008 ([http://ubuntuforums.org/showthread.php?t=976435](http://ubuntuforums.org/showthread.php?t=976435)), but the thread died in 2009, BEFORE this current modem was released. I'm not sure if these instructions will still work. :/ Tuloy ang google search para sigurado....

---

### Post by joey129 on 2010-07-24
Thanks again for the help.
Yea, mine is the all black one. I think we're using the same model..

Well, trying it from a powered off state didn't work. I'll try the smart bro sim thing soon.
And I'll try longcheer instructions as well
I'll keep you guys posted. I only get to log onto the internet like 1-2 times a week though :p haha

---

### Post by Arnold Martin on 2010-09-11
just use wvdial and put these entries to your wvdial.conf;

[Dialer Defaults]
Phone = *99#
Username =  your login username
Password = your login password
Stupid Mode = 1
Dial Command = ATDT

[Dialer hsdpa]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem

Just guess if  your modem is /dev/ttyUSB0 or /dev/ttyUSB1 and so on, when you dial, dial as root in the terminal these; wvdial hsdpa.

---

### Post by apolloltiujr on 2010-09-15
Sun, Smart, or Globe Broadband on Ubuntu 10.04


If  you are using Sun Broadband Wireless (tested on Huawei E1550) and want  it to work on Ubuntu 10.04 (Lucid Lynx), just install the  linux-backports-modules-headers-lucid-generic package and the  usb-modeswitch package.view plainprint?   


$ sudo apt-get install linux-backports-modules-headers-lucid-generic usb-modeswitch


After installing, reboot.


Plug  in the Sun Broadband. Then, a notification “New Mobile Broadband  Connection” should appear. Follow the wizard dialog (you can just click  next since the default values should be alright). Then, you should be  connected now.


Connection Name: Digitel (Sun Cellular) Connection


Mobile: *99#
Username:
Password:


Advance 
APN: fbband
Network:
Pin:&#65279;

---

### Post by nfaustin on 2010-10-25
Any update on this?
Someone please update, I'm having WM66A model which can't be detected by ubuntu 10.

---

### Post by aljoriz on 2010-10-26
go to terminal: 

enter this code:
sudo apt-get install usb-modeswitch

(enter your password and just say YES)

now go to the connection manager (yung icon na dalawang PC or a slanted line na broke.  

mouse over ka sa icon and do a right click dapat naka on yung mobile broadband.. i check mo yang box and follow everything except when entering your APN dapat smartbro gagamitin mo

---

### Post by aljoriz on 2010-10-26
oppps double post my bad

---

### Post by nfaustin on 2010-10-26
> **aljoriz said:**
> go to terminal: 

enter this code:
sudo apt-get install usb-modeswitch

(enter your password and just say YES)

now go to the connection manager (yung icon na dalawang PC or a slanted line na broke.  

mouse over ka sa icon and do a right click dapat naka on yung mobile broadband.. i check mo yang box and follow everything except when entering your APN dapat smartbro gagamitin mo

Aljoriz,  I already install the necessary packages but still it can't detect. My usb is WM66A white color. When use lsusb, it display Bus 001 Device 05: ID 1c9e:f000. On network manager, it says ANY on mobile broadband. We have the same problem with the TS. Please help.

---

### Post by aljoriz on 2010-10-26
you mean wm660A..  I heard talks that particular modem does not work on ubuntu.  I have not tried that modem in 10.10 *kasi walang akong ganyang modem*.  I only have ZTE and the huawei modems; these modems work out of the box in 10.10 ubuntu

---

### Post by aljoriz on 2010-10-26
as a last resort try [http://www.sakis3g.org/](http://www.sakis3g.org/) download their script and try it; I can't vouch for it though but its worth the try.

---

### Post by nfaustin on 2010-10-26
Thanks, aljoriz.
Your link is big help, although I hard to configure it at first but now I able to connect it. I'm using ubunto 10.10 on aspire one with SmartBro WM66A white color(WM66A listed at the back).

Thanks you very much.

---

### Post by aljoriz on 2010-10-26
No problemo, senyor.  I was glad to have helped kindly mark your thread as SOLVED.

---

### Post by nfaustin on 2010-10-27
By the way, this is not my thread. I believe your solution is only a workaround. I just keep monitor this thread until the original solution is solve.

BTW, 
thanks a lot. It really a big help.

---

### Post by xxxlam on 2010-10-30
> **nfaustin said:**
> By the way, this is not my thread. I believe your solution is only a workaround. I just keep monitor this thread until the original solution is solve.

BTW, 
thanks a lot. It really a big help.
And oh, we have the same problem. I tried Emailing this time the SmartBro team (but no answers yet). I visited sakis3g.org and downloaded the zipped file for i386 (because I'm using Intel processor). Finally, the device is detected and it appears in the selection of the wizard... ... ...

but still, no connection... I do not know why, well in fact, it was already detected. What must be the probable cause?

Thanks in advance. j3j3j3

---

### Post by aljoriz on 2010-10-30
Plug your smartbro 
Go to 
     System > Preference > Network connections click the Mobile broadband    Tab PRESS ADD.  

your modem name should be indicated press FORWARD select Philippines and your appropriate provider (smart) next next next

pag natapos na yan bumalik ka sa network connections mobile broadband then click on the setting you have created and edit the properties dapat

APN: smartbro

among the PPP settings tab then the CONFIGURE METHOD TAB.  
Make sure PAP is the only setting checked.  

PRESS OK and connect using the smartbro setting you have created.

---

### Post by jbluzb86 on 2010-10-31
same problem mu modem WM66A is also not detected,

---

### Post by aljoriz on 2010-11-01
^kindly read page2 of this thread I believe I posted the workaround solution.

---

### Post by xxxlam on 2010-11-05
> **aljoriz said:**
> Plug your smartbro 
Go to 
     System > Preference > Network connections click the Mobile broadband    Tab PRESS ADD.  

your modem name should be indicated press FORWARD select Philippines and your appropriate provider (smart) next next next

pag natapos na yan bumalik ka sa network connections mobile broadband then click on the setting you have created and edit the properties dapat

APN: smartbro

among the PPP settings tab then the CONFIGURE METHOD TAB.  
Make sure PAP is the only setting checked.  

PRESS OK and connect using the smartbro setting you have created.
WHAT UP!!!!!!!!!!!!!!!!!

SUCCESS!!!!!!!!!!!!!!!!!!

Thanks, this is solved now. But my connection is pretty slow... 

(Posting this using Ubuntu with WM66A...

Anyway, a BIG BIG Thanks to you guys. aljoriz :)

---

### Post by aljoriz on 2010-11-05
You are welcome. Mabuhay ang Linux!  Mabuhay ang ubuntu!

---

### Post by Jechem on 2011-05-15
Hi all,

I know this is an old thread but would you happen to know how to use the globe visibility/tattoo menu? I have installed the USB tattoo stick with the help of usb-modeswitch but I would like to use the feature of the menu to choose between GPRS and 3G/HSDPA signals.

---

### Post by tech-hero on 2011-05-15
It depends on your modem. btw, what modem are you using?

---

### Post by Jechem on 2011-05-16
> **tech-hero said:**
> It depends on your modem. btw, what modem are you using?
I am using the ZTE MF627 modem. I have installed it using usb-modeswitch. I have read somewhere that you would need to set it to 3G only using a Windows computer but I don't want to keep on switching to Windows7 in case the signal is different. I can set it to 3G preferred but there are times when the 3G signal is lost and the connection would also be cut-off.

---

### Post by Script Warlock on 2011-05-16
meron na bang menu ang globe tatoo? sa smartbro wala, yung umtsmon lang ginamit ko para lang makatext lang..

---

### Post by tech-hero on 2011-05-16
> **Jechem said:**
> I am using the ZTE MF627 modem. I have installed it using usb-modeswitch. I have read somewhere that you would need to set it to 3G only using a Windows computer but I don't want to keep on switching to Windows7 in case the signal is different. I can set it to 3G preferred but there are times when the 3G signal is lost and the connection would also be cut-off.
I used ZTE MF627 for my sun broadband before and i found it a little buggy for Ubuntu. I used modem-cmd on terminal to be able to set it to "WDCMA only" connection.

---

### Post by Jechem on 2011-05-17
> **tech-hero said:**
> I used ZTE MF627 for my sun broadband before and i found it a little buggy for Ubuntu. I used modem-cmd on terminal to be able to set it to "WDCMA only" connection.

Thank you.

---

