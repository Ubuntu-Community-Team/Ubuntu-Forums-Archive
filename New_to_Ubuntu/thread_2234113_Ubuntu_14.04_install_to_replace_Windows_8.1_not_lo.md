---
title: "Ubuntu 14.04 install to replace Windows 8.1 not loading after restart"
date: 2014-07-12
forum: New to Ubuntu
---

### Post by Fordy110 on 2014-07-12
Hi guys,

I am new to this forum and need some help trying get my new laptop running again. Today I installed Ubuntu version 14.04 using a live linux usb stick but at the end of the install when it asks you to restart to complete the change I fet the following error upon restart - The system is running in low-graphics mode. Your screen, graphics card and input device settings could not be detected correctly. You will need to configure these yourself.  

Can anybody help me fix this and get my laptop back up and running again? 

Thanks in advance

Fordy110

---

### Post by Bucky Ball on 2014-07-12
Welcome.

Is the machine online? 
Does the machine freeze when you get that message or do you continue to a desktop in low-graphics mode?

---

### Post by oldrocker99 on 2014-07-12
What kind of video do you have? If you can get to a desktop, open a terminal and post the output of

```
lspci | grep VGA
```

---

### Post by Fordy110 on 2014-07-12
> **Bucky Ball said:**
> Welcome.

Is the machine online? 
Does the machine freeze when you get that message or do you continue to a desktop in low-graphics mode?

It does freeze no matter what I choose. The only thing I haven't touched is reconfigure the configure file. I cannot get the desktop to load up.

---

### Post by ajgreeny on 2014-07-12
If you have a nvidia graphic card you may need to add the appropriate nvidia-current package to your system, though if the machine freezes you will not be able to do this from your normal login.

You may, however, be able to do this from recovery mode which you can choose from the grub menu, or if Ctrl+Alt+F1 works to get you to a command-line tty, you could login and run ```
sudo apt-get install nvidia-current
```

---

### Post by Bucky Ball on 2014-07-12
> **ajgreeny said:**
> If you have a nvidia graphic card you may need to add the appropriate nvidia-current package to your system, though if the machine freezes you will not be able to do this from your normal login.

You may, however, be able to do this from recovery mode which you can choose from the grub menu, or if Ctrl+Alt+F1 works to get you to a command-line tty, you could login and run ```
sudo apt-get install nvidia-current
```

Best to find which graphic card before installing something not required. Could confuse the issue. ;)

If you can get to a tty using either method ajgreeny described, issue this command:

```
sudo lshw -C video
```

Take note of the line that looks like this:

```

product: RV710/M92 [Mobility Radeon HD 4530/4570/545v]
```

... beginning with 'product' and down near the bottom where it says something like:

```
driver=radeon
```

---

### Post by Fordy110 on 2014-07-13
I have tried to re - install Ubuntu but I don't get the option to run it in recovery mode either. I have a wiped hard drive of windows so can't even boot back up to that. I am at the end of my tether now. I just need a solution to get the linux distro working even if there is one I can download now with an updated version to bypass this graphics issue and at least load up to desktop.

---

### Post by Rob Sayer on 2014-07-13
First do the above suggestions.  You have to know what video card you have.  There's no magic solution without knowing what hardware you have.

---

### Post by Bucky Ball on 2014-07-13
> **Rob Sayer said:**
> First do the above suggestions.  You have to know what video card you have.  There's no magic solution without knowing what hardware you have.

+1. Help us help you. Please follow the advice given and provide the requested information please. ;)

---

### Post by Fordy110 on 2014-07-13
Here is the specs of the laptop I bought and Windows 8.1 is off now:

HP Pavilion 15-n274sa Laptop-/+
Supported Operating Systems
Operating system
Windows 8.1 64
Processor
Chipset
AMD A76M FCH
Processor family
AMD Quad-Core A-Series processor
Processor
AMD Quad-Core A10-4655M APU with Radeon HD 7620G Graphics (2 GHz, 4 MB cache)
Appearance
Product color
Midnight black, anodized silver cover
Memory
Memory, standard
8 GB 1600 MHz DDR3L SDRAM (1 x 4 GB, 1 x 4 GB)
Memory slots
2 user-accessible
Drives
Hard drive description
1 TB 5400 rpm SATA
Optical drive
SuperMulti DVD burner
Display Specifications
Display size (diagonal)
39.6 cm (15.6")
Display
39.6 cm (15.6") diagonal HD BrightView LED-backlit (1366 x 768)
Graphic Subsystem
Graphics
AMD Radeon HD 7620G/8670M Dual GPU (2 GB DDR3 dedicated)
Multimedia
Audio features
DTS Sound+ with 2 speakers
Webcam
HP TrueVision HD Webcam (front-facing) with integrated dual array digital microphone
Input devices
Keyboard
Full-size island-style with numeric keypad
Pointing device
Touchpad with multi-touch gesture support
Connectivity and Communications
Network interface
Integrated 10/100 BASE-T Ethernet LAN
Wireless
802.11b/g/n (1x1)
Ports
1 HDMI
1 headphone/microphone combo
1 USB 2.0
2 USB 3.0
1 RJ-45
Expansion slots
1 multi-format SD media card reader
Battery and Power
Battery type
4-cell (41 WHr) Li-ion
Power supply type
90 W AC power adapter

---

### Post by Mark Phelps on 2014-07-13
> AMD Radeon HD 7620G/8670M Dual GPU (2 GB DDR3 dedicated)

This indicates you have "dual graphics" and while the AMD drivers would ordinarily help with either of these, I believe the ones from AMD don't handle dual graphics on the Linux side  But I don't have actual experience with AMD dual graphics, so I could be wrong in this.

---

### Post by Fordy110 on 2014-07-13
I can enter the terminal is there any commands I can use to resolve this?

---

### Post by JeQhdMD on 2014-07-14
Pls see this linki:  [http://xpressrazor.wordpress.com/2013/01/13/how-to-setup-amdintel-hybrid-graphics-cards-in-linux-ubuntu/](http://xpressrazor.wordpress.com/2013/01/13/how-to-setup-amdintel-hybrid-graphics-cards-in-linux-ubuntu/)

Perhaps step 5 will remove/purge the amd video drivers, and you may be able to use the Intel stock driver.   Read the article  . . . perhaps the commands in step 5 are worth a try, given you have such new hardware that isn't supported "out of the box" **yet** in Ubuntu.

---

### Post by Fordy110 on 2014-07-14
> **JeQhdMD said:**
> Pls see this linki:  [http://xpressrazor.wordpress.com/2013/01/13/how-to-setup-amdintel-hybrid-graphics-cards-in-linux-ubuntu/](http://xpressrazor.wordpress.com/2013/01/13/how-to-setup-amdintel-hybrid-graphics-cards-in-linux-ubuntu/)

Perhaps step 5 will remove/purge the amd video drivers, and you may be able to use the Intel stock driver.   Read the article  . . . perhaps the commands in step 5 are worth a try, given you have such new hardware that isn't supported "out of the box" **yet** in Ubuntu.

I have done the step 5 twice on that link you gave me to try and I still have the same issue. I can only access Ubuntu through recovery mode only after running dpkg first after that I resume normal boot and it boots up to the log in page.

Any ideas? Is it possible for me to switch to Linux Mint from this version of Ubuntu?

---

### Post by Bucky Ball on 2014-07-14
> **Fordy110 said:**
> Is it possible for me to switch to Linux Mint from this version of Ubuntu?

No (have never heard of a way, that is), and be aware that Linux Mint is not supported in the main support sub-forums here. If you need help with that you are welcome to post a new thread in 'Other OS/Distro support', although Linux Mint has a vibrant and active community so you might be better off posting on their forum also.

Have you tried removing 'fglrx' and 'fglrx-amdcccle' and rebooting?

---

### Post by Rob Sayer on 2014-07-18
Linux Mint is based on ubuntu but they use an older kernel ... say about 6 months.  So it is *extremely* unlikely ... probability somewhere between zero and sweet **** all ... that installing mint will solve this.  Because the hardware recognition in ubuntu is going to be better.  It's better than pretty much any other linux distro's anyway.

Besides, mint tech support on their forum is pretty useless.  I think Mint is OK for users who really know what they're doing but for noobs ubuntu is the ONLY distro I'd recommend unless you have some very, very old hardware that won't run modern DEs.

I've distro hopped in the past but this is NOT a good reason to do it.

---

### Post by at_first_light on 2014-07-18
You have AMD hybrid graphics like me (though not the same model). I'm not sure if drivers for your card are included, but for mine the fglrx-updates package works. These are the proprietary drivers.

_**Steps:**_
1. Install the graphics drivers package:
```
sudo apt-get install fglrx-updates
```

2. Initialize it:
```
sudo amdconfig --initial
```

3. Restart your computer.

4. Enable both your graphics cards:
```
sudo amdconfig --adapter=all --initial
```

5. Restart your computer again. You now have drivers installed and configured. Use the Catalyst Control Center to change your graphics settings.

_**Notes:**_
- You can change your graphics settings using the Catalyst Control Center, but the admin shortcut may not work. I had this problem on Lubuntu 13.10; I haven't tried with Ubuntu 14.04 yet. You can get past this problem by launching it with root priviledges from the terminal.

1. Install Gksu:
```

sudo apt-get install gksu

```

2. Launch the Catalyst Control Center In Admin Mode:
```

gksu amdcccle

```

_**Sources:**_
- [http://postbin.per.red/pages/article31/page.php](http://postbin.per.red/pages/article31/page.php)

---

