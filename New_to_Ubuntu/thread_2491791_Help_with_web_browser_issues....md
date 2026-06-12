---
title: "Help with web browser issues..."
date: 2023-10-20
forum: New to Ubuntu
---

### Post by seven59889 on 2023-10-20
Hi,

I've recently just installed ubuntu on my Toshiba Qosmio x505 laptop after having issues with speed using upgraded version of windows 10 from windows 7 the came with the laptop so I thought I'd give ubuntu a try

The installation was smooth and the software seems to run smooth and fast, until I use a web browser I start to get jagged random glitch pixelation all over the screen

I don't know my way around the software, but can follow directions

any help would be appreciated :)

Thanks,
Steven

---

### Post by readableauthor on 2023-10-20
Go to Settings -> About. Post info about OS Name, Processor, Graphics here.

---

### Post by #&amp;thj^% on 2023-10-20
Or just show us:
```
inxi -SxxxGxxxCD

```

---

### Post by seven59889 on 2023-10-20
thanks, so I've attached a snap shot of it

---

### Post by seven59889 on 2023-10-20
Here's the inxi...

---

### Post by #&amp;thj^% on 2023-10-20
Are you opposed to install the nVidia driver? also might not hurt to login as an X11 session as well.
Wayland still has some maturing to do, especially with nVidia chips.

---

### Post by seven59889 on 2023-10-20
I tried installing many times and versions I keep getting this message

is there more to installing than just double clicking on the file?

---

### Post by Holger_Gehrke on 2023-10-21
Don't try to download and install the driver from NVidia's website. That package is basically for all distributions of Linux and therefore needs quite a bit of knowledge to use and install (you need to mark it as executable and run it from the shell / a terminal). In addition it basically needs to be reinstalled every time the kernel gets updated. 

There's a simpler way. Go into the 'Software & Updates' application. It has a tab 'Additional Drivers'. It should offer a driver for download and installation that will install with less trouble and will be kept up to date.

Holger

---

### Post by TheFu on 2023-10-21
> **seven59889 said:**
> I tried installing many times and versions I keep getting this message

is there more to installing than just double clicking on the file?

Please don't post images of text.  Copy/paste the text and post that instead, wrapped in "code-tags", which are available in the forum **Advanced Editor** '#' button.  It works just like bold/italics, but columns are retained, so ZERO other formatting is needed.  We are used to looking at text here.  1000 characters vs 250KB for the image. No comparison.  Plus people trying to help you can easily copy the text and highlight things or perform their own searches if text is provided.

Text is much easier to work with on Linux and in these forums, unless the issue is specifically about a GUI and the image shows that specific issue.

I'll go away now.

---

### Post by seven59889 on 2023-10-27
this is the system details:

# System Details Report
---


## Report details
- **Date generated:**                              2023-10-26 21:36:06


## Hardware Information:
- **Hardware Model:**                              TOSHIBA Qosmio X505
- **Memory:**                                      6.0 GiB
- **Processor:**                                   Intel® Core™ i7 Q 720  × 8
- **Graphics:**                                    NVA3
- **Disk Capacity:**                               500.1 GB


## Software Information:
- **Firmware Version:**                            V2.90   
- **OS Name:**                                     Ubuntu 23.10
- **OS Build:**                                    (null)
- **OS Type:**                                     64-bit
- **GNOME Version:**                               45.0
- **Windowing System:**                            Wayland
- **Kernel Version:**                              Linux 6.5.0-9-generic


someone advised me to get rid of this laptop and buy a new one already, so I thought I'd give linux a try and see what happenes

learning slowly....

so things seem to be running smoothly and system loads fast, but for some reason when I use either firefox or brave I get those random pixillation glitches across the screen and when I play a youtube video seems to be running smoothly even the previews but then it freezes and can't do anything other than doing a hard shut down

I thought nvidia needed updating but nothing shows up under Additional Drivers

don't know what else to do, does the system detail shows a flow or something i'm not aware of is it strong enough to run the system or should I get a new laptop?

---

### Post by kinddolphin8827 on 2023-10-30
[QUOTE=
learning slowly....
/QUOTE]

The slow and steady approach has always been the best way to learn bot a new operating system or any thing new in life in general.

I can still remember all of the long and frustrating hours of debugging my own errors in my own Linux infancy  and yes I'd try to post on Forums including this one expecting some one to come along and read my mind. Although that was never even rottenly close to what really actually happened I took the advice of those around me whom had even as much as just a year or two more experience then I did at that point.   With several more frustrating hours of late nights when i should have been in bed sleeping especially on school nights. I steadily gained the knowledge that I didn't poses when I started my Linux journey I basked int the light of others around me whom had been using Linux much longer than a relative "newbie" such as myself.

This  isn't to say that my first foray into Linux was normal I started in a very atypical way. I dove straight into the deep end of the pool and started out by setting up a Debian file and print server for my families Local area network.    I worked backwards to the desktop side of things.

---

### Post by Holger_Gehrke on 2023-10-31
NVidia and Wayland don't always play well with each other. Try selecting an X11 based session when logging in (the cog-icon on the login screen should offer the various types of sessions available on your system) and checking whether this solves your problem. Wayland and X11 are two separate basic layers for the stack of software that makes up the GUI. X11 is a lot older - and probably on the way out - but the newer Wayland stack still has its problems.

 Also you've got 23.10 installed, which is a brand new short term release. Ubuntu is released on a six-month schedule; every fourth release - the one released in April of an even numbered year - is a long term release, meaning it will be supported for five years. All other releases are only supported for nine month. Unless you like living on the bleeding edge - and there's a reason they call it 'bleeding' - or have very new hardware that isn't supported well on a long term support release, you should really use an LTS. The last LTS was 22.04, the next will be 24.04. Using an LTS means you won't have to do a full OS version upgrade every six month and the probability of problems you encounter being known and therefore solvable is higher.

Holger

---

### Post by MAFoElffen on 2023-11-01
When it first boots up to the Graphical Login screen, when you first select your name and the password box appears, there will be a Gear Icon that appears i the lower right hand corner. If you select that Gear Icon with your mouse, it will bring up a dropdown selection box with different Desktop Options, which will include Ubuntu on Wayland & Ubuntu on Xorg > Select Ubutu On Xorg.

Select the Icon on the upper Left corner to brig up the chooser panel. Start typing "Software & Updates". Select that Icon. > Go to the Additional Drivers Tab > Install the nvidia-driver-390 driver.

---

