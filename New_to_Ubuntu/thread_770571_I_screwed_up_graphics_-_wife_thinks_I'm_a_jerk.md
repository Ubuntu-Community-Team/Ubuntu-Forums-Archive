---
title: "I screwed up graphics - wife thinks I'm a jerk"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by drrwhistle3 on 2008-04-27
OK, I was trying to make my screen cool as I have been reading (not necessarily understanding) about compiz and Beryl.  Anyway, in my desperate effort to abandon M$ windows I tried to change my video driver.  When I install 7.10 it defaulted to a generic driver and I believe I have a better card.  So I picked the one I thought i had and hit the test button and not much cahnged so I said "OK" and restarted.  When it came back on it wet to safe mode and the screen resolution is 800x600 and is now using vesa - generic.  I have a Dell Vostro 200.  I can't figure out which video card I have.  can you help me get back to where I was at least if not even to put the cool graphics on.  
I am very good with XP but not tying to learn all I can about Ubuntu (I want to be a free thinker) but I need help learning how.
Please tell me what info you need and I will try to get it.  
Thanks!!!!:confused:

---

### Post by gunbladeiv on 2008-04-27
try to list all your pci card.  to list all your pci card, run this command on terminal:
```
lspci
```
And after that, you must look for any graphic card listed there. Usually you will see something being recognize as Graphic Card on the list.  If you have no idea of what the output will look like, then this is mine:
```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
0a:00.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0a:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0a:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```
As what is listed on my list, there is VGA controller which is my graphic controller.  So it's my graphic card.  All I need to do is find a tutorial on how to install my graphic card driver.  
If in case you are using ATI, then you could look for tutorial on the ubuntu wiki.

---

### Post by WoodyMahan on 2008-04-27
If MS is still available to you on that machine, you can boot into windows, go to Device Manager and look at the video card in MS.  This will give you the information you need to look up which video driver you need to install.

---

### Post by Ub1476 on 2008-04-27
The output of the command below will display your graphic card/controller:

```
lspci | grep VGA
```

I suggest you upgrade to Ubuntu 8.04, Hardy Heron, for a better Compiz-Fusion experience as well;)

---

### Post by Michael.Godawski on 2008-04-27
First check in the Restricted Driver Manager if there are drivers for you card available and perhaps not active.
System > Administration > Restricted Driver Manager

If you have a running internet connection just activate the missing driver there.

If you still encounter graphical issues, boot into the Recovery Mode and run 
```
sudo dpkg -reconfigure xserver-xorg -phigh
```

---

### Post by southernman on 2008-04-27
Looks like your in good hands with the graphics issue, now....

Sorry, but I LOL'ed when I read your thread title about what the wifey thinks of ya.

FYI, You will find that happening a LOTTTTTTTTTTT. Just grin and bare it. The most important phrase you'll do well to remember is:

I'm sorry honey, your right and I am wrrrr wrr wrrrrrong. (that last part is still tough to say)

---

### Post by drrwhistle3 on 2008-04-27
This is what I found is my card, I think.  I tried the SYS>ADMIN>RESTRICTED DRI...  showed my ethernet card there.  

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)


Any idea the driver to install?  and if this will co the cool graphics?

---

### Post by dokdoom on 2008-04-27
Unless there is a new driver for intel cards with Hardy you probably would use i810 or intel.

Edit your /etc/X11/xorg.conf file and in the "Device" Section, make sure it looks like this.

Driver    "intel"

or 

Driver    "i810"

---

### Post by drrwhistle3 on 2008-04-27
If I were to upgrade to 8.04 - Hardy - would this fix the problem or would I still have to tell it how to fix?

---

### Post by Ub1476 on 2008-04-27
Intel provides open-source drivers, so the driver for you Intel controller is already installed inside the Linux kernel.

I'm not exactly sure which driver to use, but it's probably the "intel" or "i810" driver.

And well, it's not super powerful, but it should handle Compiz-Fusion quite easy. 

Suggest you read [here]("http://wiki.compiz-fusion.org/Hardware/Intel") if you want to set up your intel controller with Compiz-Fusion (visual effects).

If you're curious whether to use AIGXL or XGL (as described in the wiki), use AIGXL.

EDIT:

Upgrading to Hardy might fix it, but it's a relative easy problem anyway. I suggest you to upgrade anyway (better performance, easier to use, more powerful effects, hopefully more stable ++)

---

### Post by Jimmy9pints on 2008-04-27
Ha ha. Sorry I can't help you with the graphics thing. But totally sympathise about the situation with the wife. My gf thinks I am nuts for switching to Ubuntu/Linux

---

### Post by drrwhistle3 on 2008-04-27
I tried to change the driver in the System>Admin>Screens and graphics  it keeps going back to the vesa driver at low res.  I don't understand the instructions about change /etc/..... in the "device" section.  I am truly not a moron.  I used to think I was good at this stuff.  Perhaps it is M$'s goal to make everyone computer dumb.  I am sure feeling that way now!

---

