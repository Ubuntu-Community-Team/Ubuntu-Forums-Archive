---
title: "The last push - i need this webcam sorted out"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by gottabeandrew on 2008-05-02
EDIT: Because this went on for 4 pages, i decided to make a new, clean version of this thread [here]("http://ubuntuforums.org/showthread.php?p=4877815#post4877815").


I was very optimistic about giving ubuntu a go and even thought i might be able to stay on here most of the time (i'd be back on windows to play games though). I have 1 problem though - my webcam doesn't work. It's a logitech quickcam sphere MP. I've spent literally **ALL** day (over 10 hours) googling things and asking around on here for what to do and being directed from page to page and then being given useless crap to install then being given rubbish instructions on how to do certain things etc. I can't do this anymore, i'm fed up with it completely. Ubuntu is a nice idea but windows works and i use my webcam all the time on there. If i can't use my webcam on ubuntu then that means i can't really use it because if i'm switching over to windows 50% of the time to use my webcam and back to ubuntu for when i'm not, it's just a huge hassle and not worth it so i'll give up on ubuntu and just stay with windows.

I really want to get ubuntu to work with this though because it's my only problem and once i can get this fixed, it'll be great.

So, i need your help. Can you please try and find me a way to get my Logitech Quickcam Sphere MP webcam working on ubuntu 8.04. Please provide clear instructions for me which is understandable to somebody who has never used ubuntu before.

Thanks.

---

### Post by gottabeandrew on 2008-05-02
Bumped because this is important.

---

### Post by thenes on 2008-05-02
What applications are you trying to use your cam in?

---

### Post by kwacka on 2008-05-02
Is [http://www.quickcamteam.net/](http://www.quickcamteam.net/)   any use?

---

### Post by sjprice on 2008-05-02
After a quick search, it looks like lucview or UVC Video should support it. Sorry if you have tried these in the last 10 hrs :)

[https://bugs.launchpad.net/ubuntu/+bug/104194](https://bugs.launchpad.net/ubuntu/+bug/104194) and [https://bugs.launchpad.net/ubuntu/+source/camorama/+bug/86754](https://bugs.launchpad.net/ubuntu/+source/camorama/+bug/86754)

I have a Microsoft webcam, so I didnt even try to get it working in ubuntu and loaded XP in a virtualbox and use it there with no issues.

---

### Post by gottabeandrew on 2008-05-02
Those two webpages are very confusing. I've been on the first one a few times but got confused every time. Can somebody give me a link to what i need to download for both of them and instructions on what i need to do next? (remember - don't assume that i know anything)

---

### Post by Michl on 2008-05-02
Did you check help.ubuntu.com, specifically:

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

and:

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)

According to Logitech, this webcam is compatible with
Linux:

[http://www.quickcamteam.net/hcl/linux/logitech-webcams](http://www.quickcamteam.net/hcl/linux/logitech-webcams)

but there are two qualifications in the notes and a FAQ.
One thing I noticed that ubuntu and Logitech list different
drivers.

I don't have a webcam so I can't give specific help, but
I know the space you're in right now very well.  It usually
helps if you state exactly what you tried doing, what exactly
did not work, and so on.

---

### Post by gottabeandrew on 2008-05-02
I googled and looked around uselessly for a while. I tried downloading drivers and patches and all sorts and they either didn't work or didn't have clear instructions. There was a lot of confusing links too. All i need is a direct link to a driver (not whordes of pages to click through) and clear instructions on how to install it.

---

### Post by gottabeandrew on 2008-05-02
I'm bumping this because it needs to be solved. Thanks. :-)

---

### Post by fatality_uk on 2008-05-02
> I'm bumping this because it needs to be solved - Ubuntu is a nice idea but windows works and i use my webcam all the time on there

Im sure!!! Dual booting works for a lot of people. Perhaps try using Windows and have a small Ubuntu "test" partition and work on your web cam problem there!

Anyway, look here. It's a generic pspca driver for a lot of webcams, especially Logitech [http://mxhaard.free.fr/](http://mxhaard.free.fr/)

I notice you haven't answered which applications you have tried your web cam with. Have you considered that it might be working, just not with the application you are using?

---

### Post by gottabeandrew on 2008-05-02
I've tried it with Easycam 2 and Firefox (stickam.com). On easycam it isn't detected at all and on stickam it shows up as black (which i think also means it isn't detected).

---

### Post by halitech on 2008-05-02
can you post the output of
```
lspci
```
and
```
lsusb
```

so we can see if ubuntu is even seeing the cam

---

### Post by tashmooclam on 2008-05-02
I think there should be a warning somewhere that Linux and Webcams do not get along much.
gOS is working with making drivers for webcams made by ezonics. Maybe soon they'll have it available. 
I have heard some logitech ones work, but I'm too cheap to do an experiment.

---

### Post by gottabeandrew on 2008-05-02
> **halitech said:**
> can you post the output of
```
lspci
```
and
```
lsusb
```

so we can see if ubuntu is even seeing the cam

lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 10)
05:01.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:01.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:01.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
05:01.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

lsusb:

```
Bus 005 Device 002: ID 046d:08cc Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by halitech on 2008-05-02
I hate to be the bearer of bad news but it doesn't look like ubuntu is even seeing the cam. was it plugged in when you ran those commands?

---

### Post by loell on 2008-05-02
```
046d:08cc
```

it probably uses the uvc driver, which won't work on flash based webcam applications,

try **camorama** if it show some images then you'll need to compile 

[http://www.swift-tools.net/Flashcam/]("http://www.swift-tools.net/Flashcam/")

to use it on flash.

yeah, the howto may  not be easy for a beginner.

---

### Post by gottabeandrew on 2008-05-02
> **fatality_uk said:**
> Im sure!!! Dual booting works for a lot of people. Perhaps try using Windows and have a small Ubuntu "test" partition and work on your web cam problem there!

Anyway, look here. It's a generic pspca driver for a lot of webcams, especially Logitech [http://mxhaard.free.fr/](http://mxhaard.free.fr/)

I notice you haven't answered which applications you have tried your web cam with. Have you considered that it might be working, just not with the application you are using?

Ok, i've downloaded this. I'm looking through the instructions now but they make absolutely no sense. Here's the first bit. Can anybody form some clear instructions from this please (remember, don't assume i know anything about ubuntu).

> Compiling it
============
The driver module can be built without modifying your kernel source tree.

Before trying to compile the driver, ensure that you've configured your
kernel, and updated the dependencies:
'make [config|menuconfig|xconfig]; make dep'.

Make sure, when compiling the driver, you use the same version of compiler as
was used to compile your kernel. Not doing so can create incompatible binaries.

as root
goes to gspcav1 directory and run:
./gspca_build 

if all goes right the module is compiled and load in memory
if not, errors messages can be found in kgspca.err You should post this file to the maintainer
or in the sourceforge project bugs report. <http://sourceforge.net/projects/spca50x/>.

EDIT: I'm seeing "Compile" everywhere. What does that mean and how do i do that?

---

### Post by halitech on 2008-05-02
compile basically means you take the raw code and run it to get things where they need to be for your system. Normally its a matter of opening a terminal (Applications - accessories - terminal) and then run the commands as listed.

when it says do it as root, you would run

```
sudo ./gspca_build
```

---

### Post by gottabeandrew on 2008-05-02
> **halitech said:**
> compile basically means you take the raw code and run it to get things where they need to be for your system. Normally its a matter of opening a terminal (Applications - accessories - terminal) and then run the commands as listed.

when it says do it as root, you would run

```
sudo ./gspca_build
```

Ok, thanks. So for what i posted, what exactly do i need to do (including every line i need to put in the terminal (and just incase you know, i saved the extracted folder to the desktop)).

---

### Post by loell on 2008-05-02
gspa driver is already installed in ubuntu by default, no need of compiling it, imho.

---

### Post by gottabeandrew on 2008-05-03
> **loell said:**
> gspa driver is already installed in ubuntu by default, no need of compiling it, imho.

Ok, so looking at the instructions given to me (which i copy and pasted above and below), what exactly do i need to do? Those instructions just assume i would  understand stuff which just sounds very confusing to me such as "Make sure, when compiling the driver, you use the same version of compiler as was used to compile your kernel. Not doing so can create incompatible binaries."

Anyway, here's the code in full:

> Compiling it
============
The driver module can be built without modifying your kernel source tree.

Before trying to compile the driver, ensure that you've configured your
kernel, and updated the dependencies:
'make [config|menuconfig|xconfig]; make dep'.

Make sure, when compiling the driver, you use the same version of compiler as
was used to compile your kernel. Not doing so can create incompatible binaries.

as root
goes to gspcav1 directory and run:
./gspca_build

if all goes right the module is compiled and load in memory
if not, errors messages can be found in kgspca.err You should post this file to the maintainer
or in the sourceforge project bugs report. <http://sourceforge.net/projects/spca50x/>. 

Also, what's a gspa driver?

---

### Post by loell on 2008-05-03
i suggest that you forget the compiling phase, gspca is a driver needed for quite a large range of webcams. you don't need to compile it, because its already there.

but looking at your usb code that you gave, your webcam doesn't use gspca driver , it uses uvc driver which is also installed in ubuntu by default.

now install **luvcview** in command line by  typing or copy/pasting ```
sudo apt-get install luvcview
```

after installing the above, plug your webcam and execute

**luvcview** in the command line, try if you see images in your webcam.

---

### Post by crabclaw on 2008-05-03
Andrew: I'm ubuntly challenged too and just got my webcam to work by downloading camorama webcam viewer with the add/remove applications manager... I'd gone nuts with all of it and now it works perfectly. Am operating in Hardy Heron maybe that makes a differance. If you keep it up it'll be well worth it. I don't use my XP partition side for anything these days.

---

### Post by Michl on 2008-05-03
> **loell said:**
> i suggest that you forget the compiling phase, gspca is a driver needed for quite a large range of webcams. you don't need to compile it, because its already there.

but looking at your usb code that you gave, your webcam doesn't use gspca driver , it uses uvc driver which is also installed in ubuntu by default.

now install **luvcview** in command line by  typing or copy/pasting ```
sudo apt-get install luvcview
```

after installing the above, plug your webcam and execute

**luvcview** in the command line, try if you see images in your webcam.

This seems right to me.  I think the search for other drivers to
compile is a deadend in this case.

If you have the patience, my own strategy would be to do a fresh install of Hardy with the webcam plugged in.

Another maybe stupid piece of advice.  Do you have webcam
checked in System -> Preferences -> Removable Drives and Media?
with the webcam plugged in

---

### Post by gottabeandrew on 2008-05-03
> **loell said:**
> i suggest that you forget the compiling phase, gspca is a driver needed for quite a large range of webcams. you don't need to compile it, because its already there.

but looking at your usb code that you gave, your webcam doesn't use gspca driver , it uses uvc driver which is also installed in ubuntu by default.

now install **luvcview** in command line by  typing or copy/pasting ```
sudo apt-get install luvcview
```

after installing the above, plug your webcam and execute

**luvcview** in the command line, try if you see images in your webcam.

Ok, i typed that code in and it said this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lucview
```

What do i do now?

---

### Post by halitech on 2008-05-03
try typing it in correctly? 

it's ```
sudo apt-get install luvcview
```

not ```
sudo apt-get install lucview
```

---

### Post by Michl on 2008-05-03
That's happened to me so often, especially at first,
where the problem is a simple typo.

The other thing that occurred to me is that I'm
wondering if you started with a search on synaptic
with "webcam" or "webcams".  Alot of resources
show-up, including luvcview.  Searching synaptic is
one of the first things I do when something doesn't 
work or I need ubuntu to do something it doesn't.

---

### Post by gottabeandrew on 2008-05-03
> **halitech said:**
> try typing it in correctly? 

it's ```
sudo apt-get install luvcview
```

not ```
sudo apt-get install lucview
```

Oops! Ok, i've done that now and hurray, my webcam works! It shows my face in the box on the screen just like it should. I tried it with camorama webcam viewer and it said "Could not connect to video device (/dev/video0). Please check connection.

I then tried it with EasyCam2. It says "No camera, or no compatible camera found".

I then tried it on stickam and it showed the video as off. The only video option in the settings was called "UVC Camera (046d:08cc)".

---

### Post by gottabeandrew on 2008-05-03
I'm just bumping this because i'm almost finished this process of getting it to work and it'd be a shame if i couldn't get it to work after all this time.

---

### Post by gottabeandrew on 2008-05-03
Camorama easycam and stickam are still having the same issues as before but i tried it with aMSN and it works. Why does it work with some programs but not with others?

---

### Post by DMK62 on 2008-05-03
When it comes to linux and webcams its often hit and miss. I bought a top of the line logitech cam and it turns out logitech actually uses two different chipsets on the same model. One works out of the box and the other refuses to work no matter what you do. I returned it for a logitech quickcam communicate stx. Two of the standards used by webcams in linux are v4l and v4l2. Some webcam programs will work with both standards and some will only work with the older v4l.

The best programs that I have found for v4l are gyachi and kopete. I believe kopete can work with both v4l and v4l2.

Hopefully loell will be able to assist you further. He is definitely an expert in this area.

Dale

---

### Post by gottabeandrew on 2008-05-04
I've started a new, clean topic about this [here]("http://ubuntuforums.org/showthread.php?p=4877815#post4877815").

---

