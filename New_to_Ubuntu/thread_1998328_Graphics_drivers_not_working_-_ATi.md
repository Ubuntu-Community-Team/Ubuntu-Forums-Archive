---
title: "Graphics drivers not working - ATi"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by Bugsy_malone 666 on 2012-06-06
I feel like I am covering old ground with this one, but over the past week or so I have been messing about with my 8 year old PC that I use for linux stuff.

AMD semperon XP2500+
1.44gb of memory
250gb hard drive
Radeon 9800Pro graphics card
Creative labs sound card (I think its something like a SB32 or something)
1xDVDRW
1xDVD/CDRW

and a couple of UV lights for fun.

When I started using this machine as my 'test bed' I think I started with ubuntu 9.04(sure I have 8.04 somewhere too) and I seem to recall getting so far and not doing much else, Installed 10.04LTS and then at some point last year I upgraded to 10.10. 

Now I think at this stage the machine did work fine including with the radeon drivers as I am sure I could use stuff like wobbly windows and other enhanced visuals. Now at the same time I have a new machine that dates to the time period of 2009-10 which had a new graphics card from the HD4670 series and I posted on here about issues regarding getting the system to recognize the graphics card as this older machine was working fine, dont think a cure was ever found.

So I stopped using ubuntu for a while other than on my little X61s laptop which it ran ok on, installed 11.04/11.10 but wasnt keen and ended up with mint on that which I dont like either!

Fast forward to last month when I felt like playing with ubuntu again, with the release of 12.04!

I have a lenovo thinkstation and that doesnt like ubuntu as thats got an Nvidia card, so I came back to my old machine and started a fresh. well this screwed things up. 12.04 for some reason just would not install from CD and I ended up trying to format the machine with 12.04..11.10....11.04.....10.10 and finally got it to work with 10.04LTS again. Not sure why it didnt install with other versions. 

At this point the machine was entirely formatted, so any previous drivers settings or anything I was doing was gone, I then went through several laborious days on a slow net connection upgrading from 10.04 to 12.04, not noticing the fact there was something a miss with my graphics.

Ubuntu no longer saw and 'additional drivers' which is strange as the install before the big format had them working fine, now nothing. 

I had been trying to install the Tron Legacy themed desktop which is how I discovered the problem, so fed up at this stage with 12.04 and the way it functioned I headed back to 10.04lts and started over!

Spent a couple of weeks mucking about on and off trying to understand why it wouldnt work and today I spent almost the entire day (as its been raining all day) trying to solve the problem. I have tried following tons of tutorials people have written on this problem and there seems to be no solution as to why it wont work. I purged the drivers as per instructions, tried installing stuff and still it wouldnt work. I got to a point where I managed to make the machine black screen, that felt like about as productive as I have been all day! so went back to safe drivers for one sessions, went into synaptic package manager and installed all the ATi drivers I could find there.

so now I have lots of ATi drivers installed, the system still doesnt recognize the graphics card. I went into terminal and typed: sudo aticonfig --initial and it came back with: aticonfig: No supported adapters detected.

I am a bit of a loss now as I have spent all day looking on the internet and doesnt seem like there is any particular work round I can find, I even revisited my old threads on here to see if I could stumble across anything.

I'm still a linux noob as far as it goes but like to tinker, help would be much appreciated!

---

### Post by Mark Phelps on 2012-06-06
To make a long story short, ATI (now AMD) dropped restricted driver support for your graphics chip long time ago.  Last Ubuntu release that supported it was 8.10.

These days, the only drivers that will work are the default open-source radeon drivers -- which are installed by default.

If you're able to boot into a desktop, those drivers are already installed and working -- regardless of what anything else is telling you.

---

### Post by Bugsy_malone 666 on 2012-06-06
> **Mark Phelps said:**
> To make a long story short, ATI (now AMD) dropped restricted driver support for your graphics chip long time ago.  Last Ubuntu release that supported it was 8.10.

These days, the only drivers that will work are the default open-source radeon drivers -- which are installed by default.

If you're able to boot into a desktop, those drivers are already installed and working -- regardless of what anything else is telling you.

While this may be true, it doesnt fix the issue of enhance visuals, or explain why the drivers used to work and now dont.

while support may have been dropped, there must be a way to find old driver sources on the internet and patch them in, after all I had 10.04lts working on proprietary drivers before, so I dont understand what has changed for them to no longer work. I have noted that the Open GL doesnt work either which it used to, for instance the open GL matrix screen saver, it doesnt work anymore.

So really I am trying to understand why it isnt working like it did 12 months ago.

---

### Post by deadflowr on 2012-06-06
Mr Phelps is right.
So you can either read through this page

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

or dig through the net and find the ancient drivers that support your card.

I wish you good luck in either case.

---

### Post by Bugsy_malone 666 on 2012-06-08
Well after a little digging, ATi themselves have a Catalyst driver that supports most cards, and ubuntu 9.04. Its not 10.04lts but I did find a thread somewhere (on here I think) where people were managing to get the drivers to work on later versions too(I Think).

The problem that I have been suffering is the system doesnt recognise my card which is what I cant understand. It can read the chip and say its a R350 chip and its ID, but the catalyst driver just says no hardware found.

Trying to understand why it wont recognise the card and if perhaps there is something else blocking it, otherwise the older drivers may well install.

I did do a fresh install from 9.10 and upgraded to 10.04.3lts this time rather than a fresh install from 10.04lts I have on disc, still pretty much the same issues. I wondered if perhaps the graphics driver selector module maybe causing the fault as to why it wont recognise the card.

---

### Post by Mark Phelps on 2012-06-08
From what I had read, the last Ubuntu version that had ATI drivers for that chipset was 8.10, not 9.04.  And the problem using those drivers now, is that they are incompatible with X-server versions newer than the one included in Ubuntu 8.10.  That requires you to backport your X-server software -- which will lead to lots of OTHER problems.

---

### Post by QIII on 2012-06-08
I want to reiterate what Mark Phelps said, but perhaps from a different angle, or a clarification of his:  the issue is not with Ubuntu, but with ATI.  Although this is a good place to ask the question, the answer is still that ATI has not decided to maintain the driver for your card to keep up with the changing landscape of Linux (not just Ubuntu.) The driver is simply not finding supported hardware.  Thus, the message.  And even if you manage to install the legacy driver, it will not work with X server (for at least the last four years) and you will be worse off.  The open source driver will work, but with fewer features.

There really is nothing to understand here beyond that.

I hate to sound terse, but this question is just so often asked in terms of "What is wrong with Ubuntu?" or "What is wrong with the ATI driver?".  The answer to each question is "Nothing.  The card is no longer supported.". NVIDIA has similarly discontinued cards under Linux.

This is a very simple business decision for the OEMs.  They are companies that exist to make a profit.  They weigh cost/revenue considerations.  The cost of maintaining the driver for a card that old for a small segment like Linux makes no sense.  So they stopped maintaining the driver to keep up.  I don't blame them.

---

### Post by crcook84 on 2012-06-08
I am having the same problems this user is having with Ubuntu and my Radeon video card. I understand that support for the older cards has been dropped from Ubuntu after 9 or 10. However, I did find the legacy support on the AMD website. Is it possible to configure Ubuntu somehow to work with these Windows drivers? There is a program for Ubuntu already that allows for the use of Windows Wireless Drivers. As such, what about having a general purpose program that can use any kind of Windows driver for whatever the purpose of the driver is?

---

### Post by QIII on 2012-06-08
The legacy driver will simply not work with X server.  Unless you want to make potentially catastrophic changes and go back to an older X server, there is no way to make it work.  

This does not apply only to Ubuntu, but to all distros using versions of X server post 2008.

Open source developers have worked for peanuts and crusts late at night to make the open source driver available.  You would be best served by using that.  And throw those guys a bone.  They work very hard for very little recompense.

---

### Post by traditionalist on 2012-06-08
I tried all sorts of things for weeks to get the proprietary drivers working on my ATI Radeon cards. ( These are new cards).Even when you get the drivers installed correctly they don't work properly and may not even work at all.  The generic drivers in Ubuntu work OK and they work even better after updates on a fresh system.  I don't know why this is, as far as I can see nothing is changed on the drivers but the system somehow smooths out a few small problems. Or maybe the cards just get used to Ubuntu after a while?  :)

However this may be, you can't blame Ubuntu when some hardware drivers from various firms don't work.

---

