---
title: "Geforce 6600 not working"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by sdlyr8 on 2008-05-17
I just bought a new Geforce 6600 for my 3 year old HP box. I'm running Ubuntu 7.10 on it. I installed the card and whenever i try to boot, it beeps after about 5 seconds and nothing else happens. I started trying to download the driver but it couldn't find the headers during the installation. But then i started wondering if it was even Ubuntu related or if it was just not compatible or something. Any ideas or suggestions?

---

### Post by shadow-of-sin on 2008-05-17
The fact that it doesn't even show the POST screen on startup and only beeps shows that your problem is not related to Ubuntu at all. I suspect that the GeForce card you are trying to install is broken, have you tested it on any other computers?

---

### Post by nicedude on 2008-05-17
FIRST DOES YOUR CARD HAVE A CONNECTOR FOR A POWER CABLE TO BE PLUGGED UP, if so it wont work until you plug in a drive power source :-)

If thats not it A few things to try for starters before you judge the card defective

1. if it won't show video at post it is not OS related, but did you switch the cable from your on board video to the new card ? I have actually done that one before and took a sec to figure out how stupid I was.

2. check in your PC bios and see if you have a setting for what video device it will be using and if you find it set it to add on card so the system wont be trying to use your on board instead.

3. Since you say its 3 yr old PC I guess card is AGP interface, you caould make sure your cards AGP speed is supported by yuor PC's AGP slot i.e. 2x 4x etc and if not check your PC manufacturers support website for BIOS updates that increase support for AGP bus speeds with your Mobo.

4. If possible try the videos card in another computer than this one and see if it posts to the bios screen.

Also if none of that works try removing the card and cleaning the contacts where it plugs in the AGP bus with a pencil eraser then wipe any eraser left over bits off with a clean cloth "gently" and reinsert back in PC taking note of whether it seems to fit into the bus slot correctly.

I have installed over 100 AGP & PCI Express cards over the years so PM me if you still have trouble and I can defiantly help you figure out whats up.

---

