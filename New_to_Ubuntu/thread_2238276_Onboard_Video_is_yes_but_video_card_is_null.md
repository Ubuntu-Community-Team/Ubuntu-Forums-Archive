---
title: "Onboard Video is yes but video card is null"
date: 2014-08-07
forum: New to Ubuntu
---

### Post by cmo999 on 2014-08-07
Any advice would be greatly appreciated!

I have a Certified Digital desktop computer, that came loaded with Windows 8.  I want to have a dual boot on it for WIndows 8 and Ubuntu 14.04.  I installed an extra 500GB hard drive in the computer, and installed Ubuntu 14.04 onto that hard drive.  It's all good, I can boot into Ubuntu and so on, but only the onboard display works! The monitors plugged into the video card is blank!

I have 4 screens in total, the motherboard has an onboard VGA and HDMI output which are working, and the video card has an HDMI and high definition video adapter port (can't remember what they're called off the top of my head, the one that is basically HDMI but without audio).  On Windows 8, all 4 monitors work.  But on my new Ubuntu installation, only the 2 onboard video outputs work! :(

I tried installing ATI Radeon open source video driver, since the video card is an ATI, but that didn't do anything other than make the onboard HDMI fit properly.

Please advise!


p.s. along with installing the ATI Radeon driver, I also did update and upgrade all the newest updates, but to no avail.

---

### Post by farrinux on 2014-08-09
Try going into "System Settings" folder and click on "Displays".  This will allow you to see if the other monitors are listed and if they are set to be used.  Also would not hurt to check your driver settings out.  Not familiar with the Radeon video cards.  But for Nvidia, the nonfree drivers have a GUI you can use to set things. Hope this helps.

---

### Post by cmo999 on 2014-08-22
> **farrinux said:**
> Try going into "System Settings" folder and click on "Displays".  This will allow you to see if the other monitors are listed and if they are set to be used.  Also would not hurt to check your driver settings out.  Not familiar with the Radeon video cards.  But for Nvidia, the nonfree drivers have a GUI you can use to set things. Hope this helps.


Hello!

I am fairly certain that it is not the video card that is the culptit, but the monitor itself actually.

The reason why I think this is because, the other monitor that I have plugged into the video card in my computer DOES show up in Ubuntu! The video card has an HDMI output and a DVI output.  The HDMI output goes to a TV and it works great! The DVI output goes to an ASUS monitor, and it stays blank :(

Has anyone had this problem recently? I have Ubuntu working great on my new computer now, and I'm excited about immersing myself into it!  The only thing I'm missing is getting to work on the ASUS monitor, which is my primary monitor!

Any suggestions would be greatly appreciated!

In the meantime I will also be researching my ASUS monitor's model (don't have it on hand but will soon) and how it works with Ubuntu.


Thanks a bunch! :-D

---

### Post by sandyd on 2014-08-22
Hi, can you post the output of
```

lspci
```
That will give us more information on your system and allow us to assist you better.

---

### Post by cmo999 on 2014-08-23
> **sandyd said:**
> Hi, can you post the output of
```

lspci
```
That will give us more information on your system and allow us to assist you better.

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7660D]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 1)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde XT [Radeon HD 7770/8760 / R7 250X]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
02:05.0 Network controller: Qualcomm Atheros AR922X Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)

---

### Post by cmo999 on 2014-08-25
I'm coming up dry :(

Any ideas or suggestions would be greatly appreciated!

---

### Post by dave131 on 2014-08-26
Have you checked additional drivers to see if perhaps the 2nd card needs 1 in ubuntu?

---

### Post by dave131 on 2014-08-26
Also, I'm not familiar with using more than 1 monitor, let alone 2 video cards and more monitors.  I wonder if you need to create some entries for the xorg.conf file or whatever the new x11 config file(s) might be.  Maybe you need to define multiple controllers and multiple screens.

---

### Post by cmo999 on 2014-08-26
> **dave131 said:**
> Also, I'm not familiar with using more than 1 monitor, let alone 2 video cards and more monitors.  I wonder if you need to create some entries for the xorg.conf file or whatever the new x11 config file(s) might be.  Maybe you need to define multiple controllers and multiple screens.


I've come to realize that the problem is not about multiple monitors, or multiple video cards: It is with the monitor itself.  The video card works, I can plug a different monitor into the video card and it will work.  It's this particular ASUS monitor, which happens to be my main monitor, that for some reason Ubuntu will not acknowledge.

It used to!  I mean, a while back I had an older version of Ubuntu installed and I remember the monitor working with it.  

I just don't know! I wish I could make this monitor work!

---

### Post by dave131 on 2014-08-27
I wouldn't know how to help, but perhaps if you posted the make (like you did already - ASUS) and also the model, then describe exactly what happens - i.e., nothing shows on the monitor from boot on up, but if I swap out to another monitor it works fine.   Maybe someone will know the answer to that question.

Also - if no other monitors are plugged in, and you start with the built-in video and work out to the other video adapter, can you get anything on the ASUS monitor?  If nothing shows at all with power up then I wouldn't have any clue.  If it does show, perhaps that monitor, for whatever reason, needs to be the first monitor found.  Then I would configure it through the System Settings/Video set up.  I think it would need to be found there before it might work elsewhere.  If you can get it working with both adapters in the PC and only using this monitor, then I would add 1 at a time and work through any problems each time.

Now, this is coming from a newbie, and it sounds like you have far more experience with this than I probably ever will have, so forgive me if I'm giving dumb "advice" ;)

---

