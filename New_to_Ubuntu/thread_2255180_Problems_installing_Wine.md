---
title: "Problems installing Wine"
date: 2014-12-02
forum: New to Ubuntu
---

### Post by nick70 on 2014-12-02
Hello everyone. I'll try to make this as short as I can because it's such a long story.

So, I'm trying to install Wine to be able to install my network drivers for my NETGEAR A6200 Wifi adapter so I can connect to the internet. I was going to do it on the Windows I have installed, but for some reason that won't boot (it just goes back to GRUB when I click on windows), so I figured I might as well get my network up and running and get the drivers on Ubuntu, and maybe get Boot Repair as well (since for some reason it isn't included with my version of Ubuntu and a live-USB doesn't ever work for me).

So, I download Wine and the first thing that comes up when I try to install (by running first ./configure --enable-win64) is 

configure: error: no suitable flex found. Please install the 'flex' package

So, I go through all the steps to install m4, and then flex. Flex is installed at /usr/local/flex/(bin/flex).

I run the ./configure command again and it comes up with the same thing. I also tried adding flex to my path variable, but that didn't change anything.

Does Wine look for flex in a certain place that it isn't finding it in? If so where should I move it?

Thanks for your help,

-Nick

---

### Post by QIII on 2014-12-02
Hello!

Have you considered installing the appropriate driver for Linux?

---

### Post by nick70 on 2014-12-02
I'm sorry,the appropriate driver for what? Wine or Flex?

And I would install the drivers, but I am not connected to the internet so any packages I get must be downloaded from source from my laptop and transferred via USB, then manually compiled.

---

### Post by QIII on 2014-12-02
The driver for your wifi adapter.

---

### Post by nick70 on 2014-12-02
That's what I'm trying to do; the install CD doesn't come with a Linux driver (as far as I know), so I'm trying to install the Windows one by using Wine.

---

### Post by grahammechanical on 2014-12-02
Why are you not installing wine through the software centre? I have installed wine a few times. I have installed it through the Ubuntu Software Centre. And I have also installed the beta version through the wine PPA (Personal Package Archive) but I have never had the trouble that you are having. Are you compiling the wine source code?

I am not sure that it is possible to use wine to install Windows drivers in Ubuntu. In fact I will say that what you are trying to do will not work.

Boot Repair is not part of the default set of applications in Ubuntu. Boot Repair is an example of an excellent utility crafted by community developers.

What version of Ubuntu are you using? What version of Windows do you have installed? If it is Windows 8, then did you note the advice given here?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by nick70 on 2014-12-02
I have Windows 7. I'm not using the Software center because I don't have internet!

---

### Post by QIII on 2014-12-02
+1 re: driver and Wine.  That will be a no-go.

The Windows driver will work when you are booted to Windows, Linux driver when booted to Linux.  There are sometimes kludges that will allow the Windows driver on Linux, but they are iffy.

Does your machine have an ethernet jack?

---

### Post by nick70 on 2014-12-02
It does, but I do not own an ethernet cable. Also, my computer is located upstairs (router downstairs) and I have no desire to a. move my computer or b. run a 60 foot ethernet cable down the house to get internet. Sorry :(

---

### Post by QIII on 2014-12-02
Did you have a wifi connection when you were installing Ubuntu from your installation media?

---

### Post by nick70 on 2014-12-02
I did not.

---

### Post by Mark Phelps on 2014-12-02
> I have no desire to a. move my computer

Understand, as I have been in the same situation.  But ... Trying to build anything from source is going to hit one dependency after another.  You could easily spend HOURS hitting and resolving each dependency.

So, as a short-term solution to get the WiFi drivers installed and working, you should seriously consider (1) moving your computer near the router and (2) connecting the two with a networking cable.

Once you've built and installed the WiFi drivers, you can move computer back and dispense with the network cable.

It's a few minutes of effort versus hours of frustration -- your call.

---

### Post by nick70 on 2014-12-02
Good advice. I'll see if I can get access to an ethernet cable.

---

### Post by Bucky Ball on 2014-12-02
> **nick70 said:**
> Good advice. I'll see if I can get access to an ethernet cable.

Good plan. Will save time and headaches and it is a one-off procedure. Once the wireless is set up, that's it. ;)

---

### Post by monkeybrain20122 on 2014-12-02
Or get a cheap USB wifi card.

---

