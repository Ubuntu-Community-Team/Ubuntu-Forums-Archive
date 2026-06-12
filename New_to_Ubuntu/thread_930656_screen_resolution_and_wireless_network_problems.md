---
title: "screen resolution and wireless network problems"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by Kushika on 2008-09-26
**Problem 1: screen resolutions**

Firstly, I am unable to select a screen resolution greater than 800x600, and would like to be able to do this. 

I've tried to edit the X config file, but I was unable to save it. I've tried various command lines that I found on the net and nothing seemed to work. 


**problem 2: wireless network**

I can successfully connect via an ethernet cable, but cannot manage to connect to the WiFi network. It is not being displayed/detected in the network manager. In addition, even though I have switched the 'WIRELESS' button to on on my laptop, there is no green 'on' light like in vista. Could this be something to do with missing drivers? 


**Additional info**
I'm running Ubuntu on the same partition as Windows. 
I'm using the Vaio VGN-FW11 laptop. 


I would appreciate some support.

---

### Post by ashmew2 on 2008-09-26
> I'm running Ubuntu on the same partition as Windows. 

You must be running Ubuntu under Wubi then ?

---

### Post by Kushika on 2008-09-26
Yes, I installed it using Wubi.

---

### Post by SpenceMakesSense on 2008-09-26
If you ever try to edit something and it wont let you save you have to run the following code
```
sudo nautilus
``` then it will open up a file browser that lets you do anything. Which is a good and bad thing :)

---

### Post by shifty_powers on 2008-09-26
can you post the output of

```
lspci
```

---

### Post by SpenceMakesSense on 2008-09-26
> **Kushika said:**
> **Problem 1: screen resolutions**



**problem 2: wireless network**

I can successfully connect via an ethernet cable, but cannot manage to connect to the WiFi network. It is not being displayed/detected in the network manager. In addition, even though I have switched the 'WIRELESS' button to on on my laptop, there is no green 'on' light like in vista. Could this be something to do with missing drivers? 




And for this it does sound like you need to install your wireless drivers. Which can be easisly done with ndisgtk.

---

### Post by shifty_powers on 2008-09-26
we don't know that he needs nidswrapper yet, hence the lspci command.... :D

---

### Post by SpenceMakesSense on 2008-09-26
yes true...just going by my own experiences...im still pretty bad with linux myself

---

### Post by shifty_powers on 2008-09-26
well hopefully the lspci command will let us know which wireless chip he is using.

it might be as simple as enabling the driver in restricted hardware....

ndiswrapper can be a lifesaver, but if we can get it working natively all the better :D

---

### Post by Kushika on 2008-09-26
Ok, this is the result of lspci: 

> 
00:00.0 Host bridge: Intel Corporation Cantiga Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Cantiga PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
06:00.0 Network controller: Intel Corporation Unknown device 4232
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
0a:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)




So, what do I need to do now?

---

### Post by Tatty on 2008-09-26
> **SpenceMakesSense said:**
> If you ever try to edit something and it wont let you save you have to run the following code
```
sudo nautilus
``` then it will open up a file browser that lets you do anything. Which is a good and bad thing :)

Just to note that you should really use ```
gksu nautilus
```

sudo is usually best for command-line applications, however for grapical applications you should use gksu.

---

### Post by Kushika on 2008-09-26
Ok, so what's my next step? This is the first time I've used Linux, although I'm not totally new to command line interfaces in general, so please be sure to bear that in mind if you reply with advice. 

Thanks in advanced.

---

### Post by shifty_powers on 2008-09-26
i hate to say it, but support for that wireless card does not seem to be supported, even in ndiswrapper, unless you fancy recompiling the kernel, which not something for the fainthearted....

[http://ubuntuforums.org/showthread.php?p=5563828](http://ubuntuforums.org/showthread.php?p=5563828)

will give you some more info...

i'll do some more digging, but not looking good..

---

### Post by shifty_powers on 2008-09-26
can you post the output of

```
uname -r
```

please

---

### Post by Kushika on 2008-09-26
> **shifty_powers said:**
> can you post the output of

```
uname -r
```

please
2.6.24-19-generic


Arg! I can't believe my laptop isn't compatible! :(

How do I go about solving the screen resolution problem, also?

Thanks for all your help so far.

---

### Post by shifty_powers on 2008-09-26
yeah, afraid of that. unfortunately, support for your card has apparently been implemented into the 2.6.26 kernel onwards, which you won't see till intrepid.

an option for you to consider is to use the pre-release version of 8.10, which will have the 2.6.27 kernel and *should* work happily with your card. I have in fact been using kubuntu 8.10 for the last few weeks and have found it stable and generally a joy to use. you could always download the live-cd and soon find out if it will work...

as for the screen resolution, this might sound daft, but have you tried the really simple option of just going system>preferences>screen res (iirc, got used to kde now :D)?

edit: for the screen res, a thought. have you got the right video drivers installed? if it is just using the basic vesa drivers, it does have the habit of limiting the res in my experience... try going system>admin>restricted hardware (iirc) and see if the drivers are enabled. iirc, your laptop has ati, 3450 maybe? ati's driver support isn't as good as nvidia, i'm afraid, but there is no reason you can't get it working. you might want to check out [envyng](http://albertomilone.com/nvidia_scripts1.html) which is a package that will automatically check your video hardware and download and install the right drivers...

btw, check out this link about your wireless..

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256629](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256629)

looking at the last post it seems that your wireless card does indeed work in the latest intrepid kernels

---

### Post by gjoellee on 2008-09-26
You should get back normal resolution after running "xfix". Learn how here: [http://kshoster.net/node/18](http://kshoster.net/node/18)

---

### Post by GoldMark on 2008-10-29
I have the same problems mentioned from Kusika:

Problem 1: screen resolutions

Firstly, I am unable to select a screen resolution greater than 800x600, and would like to be able to do this.

I've tried to edit the X config file, but I was unable to save it. I've tried various command lines that I found on the net and nothing seemed to work.


problem 2: wireless network

I can successfully connect via an ethernet cable, but cannot manage to connect to the WiFi network. It is not being displayed/detected in the network manager. In addition, even though I have switched the 'WIRELESS' button to on on my laptop, there is no green 'on' light like in vista. Could this be something to do with missing drivers?

I Have installed Ubuntu 8.04.1 on my Hard-Disk.

Bernhard

---

### Post by qlimax on 2008-11-23
is the problem of the wireless/video card solved with the 8.10 version?
I want to buy vgn-fw11e laptop.... but I want be sure these modules work with THE O.S:KS

---

