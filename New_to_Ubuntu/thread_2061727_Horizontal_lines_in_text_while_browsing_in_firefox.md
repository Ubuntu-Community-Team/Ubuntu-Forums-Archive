---
title: "Horizontal lines in text while browsing in firefox and Ubuntu Software center"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by krishna.988 on 2012-09-23
HI,

I can see the Horizontal black lines in text while scrolling in Firefox only some times see attached screen-shot 

Is it something related font rendering or display issue..?

I also see this in Ubuntu Software center when it is showing the "Installing" text but only when scrolling up and down..

My details. See the output of command lspci

```

$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

---

### Post by krishna.988 on 2012-09-24
Please can any of you help..I have also removed Windows as I could'nt boot into it..? 

If not again I'll have to format to remove ubuntu and install Windows 7!!!!

---

### Post by krishna.988 on 2012-09-24
Nobody in the community can help me out!!! Is my thread visible???

---

### Post by carl4926 on 2012-09-24
I get this on my netbook
Particularly so when using subpixel hinting

---

### Post by krishna.988 on 2012-09-25
> **carl4926 said:**
> I get this on my netbook
Particularly so when using subpixel hinting


So what is the solution for this? and why does this happen Is it a Firefox bug or Ubuntu bug??

---

### Post by zandman on 2012-09-25
good morning,

Your post is very visible, the fact that you get answers is proof of that.
"otherwise i have to install Win7" - you are always free to do that.
- How bad is the problem: do you see the lines and then they stay, obscuring the text or do they disappear when you scroll further up and down?
- To find whether it's a firefox or general problem check whether you have the same effect in other programs (OpenOffice Writer, Gimp etc.).
- If you see it coming up in other programs also then it's a general problem
- If you only experience it in firefox, then it's most likely a firefox problem
- try to run a video-hardware test: "Checkbox/System Test"
- is it directly after starting the PC that it happens or does it take time to get there?

All the above are steps to eliminate possible causes and to find possible reasons.
While searching for similar problems i found these posts:
[http://support.mozilla.org/en-US/kb/websites-look-wrong-or-appear-differently](http://support.mozilla.org/en-US/kb/websites-look-wrong-or-appear-differently)
[https://support.mozilla.org/en-US/questions/933665](https://support.mozilla.org/en-US/questions/933665)

---

### Post by krishna.988 on 2012-09-25
I think it is only firefox related with chrome it is ok... But I like firefox as default...

When I googled, I doubt it is something to do with Sub-pixel hinting and firefox..Let me check on that..

Also tell me more about Sub-pixel hinting..I have an LCD screen

---

### Post by zandman on 2012-09-25
"Also tell me more about Sub-pixel hinting..I have an LCD screen"

[https://www.google.com/search?client=ubuntu&channel=fs&q=Sub-pixel+hinting&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=Sub-pixel+hinting&ie=utf-8&oe=utf-8)
Take the 4th entry called "subpixel hinting"
Also: [http://www.grc.com/ctwhat.htm](http://www.grc.com/ctwhat.htm)

---

### Post by black veils on 2012-09-25
in Firefox preferences, go to the advanced tab, find the setting for hardware acceleration and disable it. there may be a conflict with your graphics driver.

---

### Post by krishna.988 on 2012-09-25
> **black veils said:**
> in Firefox preferences, go to the advanced tab, find the setting for hardware acceleration and disable it. there may be a conflict with your graphics driver.


I tried that there is no change...

---

### Post by krishna.988 on 2012-09-25
For now I see disabling smooth scrolling seemed the issue didn’t repeat.

But again I'll have to wait and see..and also I have disabled hinting completely..as it worsens the display in LCD..

I don't know what good is this hinting feature in gnome??

---

### Post by krishna.988 on 2012-09-25
It reoccurred again!!.. I don't know what is this issue with Firefox..I'm currently using Google chrome.. works good!! I also heard flash updates will be there for Chrome.. So decided to use Chrome...

Bye Firefox):P Welcome Chrome:p

And also after the updates to Software center.. that issue too vanished

---

### Post by krishna.988 on 2012-10-08
I have to agree that it is an issue with display driver..I feel Windows Intel driver is far better:p

---

### Post by timrichardson on 2012-11-24
See this launchpad report. Comment 24 has a fix which works for me.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/782855](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/782855)

---

### Post by krishna.988 on 2012-11-25
Thanks for the reply..I have completely switched to Windows 8...as my hardware is better compatible with Windows 8 and also I have purchased some Adobe suites..

---

