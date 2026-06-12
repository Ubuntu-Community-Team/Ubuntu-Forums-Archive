---
title: "Ubuntu 12.10 is lagging badly"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by MorrisonHotel on 2013-02-03
Hi
I have just installed ubuntu 12.10 (after a long use of Windows XP), I downloaded and installed the updates but my problem is that I have serious lags, the mouse is not moving smoothly, it take about 5-7 seconds for a folder/app to open, windows are not closing smoothly and generally everything works very slow and laggy. 
Details about my pc (according to the settings of ubuntu): 
Memory: 938 MB
Processor: Intel Core 2 CPU 4400 @ 2.00 GHz x 2
Graphics: Unknown
OS Type: 32-bit
I'm a total noob to ubuntu so please help me to fix it. What can I do to make it run smooth without lags? 
Thanks alot.

---

### Post by CDR Services on 2013-02-03
Check settings for additional drivers sometimes graphics drivers play a huge role also I have had better luck with 12.04 lts seems to be more compatible with older machines also make sure to do updates!!

---

### Post by Roskow on 2013-02-03
I'm a noobie and had trouble making a VM with 12.10

I switched to 12.04 LTS (Long Term Support) which I imagine is much more stable.  

The most recent release of any OS is uncertain territory. I'm still hearing from people complaining about Windows 8.

---

### Post by mikewhatever on 2013-02-03
Ubuntu 12.10 will be quite slow on an oldish PC, because of the graphics requirements. Can you open a terminal window (ctrl-alt-t), type **lspci**, hit Enter, and then copy/paste the output here. It should show the GPU model.

---

### Post by deadflowr on 2013-02-03
Sounds like a graphics card issue.

Follow the advice in the wiki:

[https://help.ubuntu.com/community/BinaryDriverHowto]("https://help.ubuntu.com/community/BinaryDriverHowto")

Use the command line outputs provided there and then when determined go to the provided sublink for whichever type of card you have for a more in-depth look at how to get it installed.

A quick thing to try though, is to go to the top right corner of the screen, and press the cog-like symbol to open the menu listing. From there go to system settings and open it up. 
At the bottom area of system setting, click on software sources. (this might take a minute, but a window will open up.
Go to additional drivers, and see if any drivers are listed.

---

### Post by MorrisonHotel on 2013-02-03
> **mikewhatever said:**
> Ubuntu 12.10 will be quite slow on an oldish PC, because of the graphics requirements. Can you open a terminal window (ctrl-alt-t), type **lspci**, hit Enter, and then copy/paste the output here. It should show the GPU model.
Will installing ubuntu 12.04 LTS fix my problem?
and here is the output of lspci:
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8237/8251 Ultra VLINK Controller
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
03:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
80:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)



> **deadflowr said:**
> Sounds like a graphics card issue.

Follow the advice in the wiki:

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Use the command line outputs provided there and then when determined go to the provided sublink for whichever type of card you have for a more in-depth look at how to get it installed.

A quick thing to try though, is to go to the top right corner of the screen, and press the cog-like symbol to open the menu listing. From there go to system settings and open it up. 
At the bottom area of system setting, click on software sources. (this might take a minute, but a window will open up.
Go to additional drivers, and see if any drivers are listed.
thanks I'll try this.
Edit: the editional drivers tab is empty.

---

### Post by deadflowr on 2013-02-03
Is that the whole lspci output?

You seem to be missing the output for the graphics card.

You can try this:

```
lspci | grep VGA
```

---

### Post by MorrisonHotel on 2013-02-03
> **deadflowr said:**
> Is that the whole lspci output?

You seem to be missing the output for the graphics card.

You can try this:

```
lspci | grep VGA
```
yeah it's not all sorry, here's the graphic card:
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)

Edit: I have downgraded to ubuntu 12.04 LTS and it's better now though not as smooth and fast as it was in Windows XP.

---

### Post by mikewhatever on 2013-02-03
Unfortunately, VIA graphics is not a good choice for Linux. I'd recommend either investing in a cheep second hand Nvidia card, or switching to Xubuntu 12.04. There are also quite a few light weight distros outside of the *buntu family.

---

