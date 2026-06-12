---
title: "how to install windows apps..."
date: 2007-07-20
forum: Other OS Talk
---

### Post by hockey97 on 2007-07-20
I am trying to install windows apps on my ubuntu 7.04 desktop. I had windows xp, but now want to be able to install my programs that ran on windows xp , to be on ubuntu.

---

### Post by scxtt on 2007-07-20
you do understand that you're comparing apples to oranges -- that you're basically expecting oranges to grow on apple trees, right?

at the very least, you should check into wine {winehq.com} -- you CANNOT just install a windows .exe in *nix - completely different animals ... and it goes both ways, you can't install *nix programs on windows ...

---

### Post by hockey97 on 2007-07-20
well isn't their a way to convert oranges into apples, by dna alteration.

well  I have wine on ubuntu already, this is on my sister computer, and she had windows xp but not unitl she got a nasty virus, so now she got ubuntu becuse I suggested it, but she has all programs that only work on windows platforums.

their are people that I see on google that claim they have done such a think that they used wine and also VMware and got to install windows apps onto ubuntu.

---

### Post by scxtt on 2007-07-20
you can **run** some windows apps on your desktop, but this uses tools like wine and vmware - there is no installation of windows programs into the unix filesystem ... i know it's splitting hairs, and after your second post it's more clear on what you want to do, but going off the title of this thread and your opening post, you seemed to be after something that's not possible ...

you should list the programs that you want to run on ubuntu (via wine or vmware) and see if there are linux equivalents or how practical it is to use wine/vmware ...

---

### Post by hockey97 on 2007-07-20
well, I am trying to install scanner and a camera from sony,  are their linux versions for it or any support??

---

### Post by scxtt on 2007-07-20
not sure, since i don't use either one myself - there very well could be - they could work out of the box, w/ a little config, or there could be packages available ...

for things like that (my windows smartphone, for example) a windows VM is the perfect solution ... i've never really used wine, it may be good for this as well - but w/ vmware i've got a base windows install i can connect to anytime i need a "windows only" app ...

---

### Post by igknighted on 2007-07-20
> **hockey97 said:**
> well, I am trying to install scanner and a camera from sony,  are their linux versions for it or any support??

For the camera, you should be able to simply plug it in and get your photos off of it like any disk drive.  If you want a special app to do it for you, look at FSpot, Digikam or Google's Picassa.  As for the scanner, the program you want is called XSANE.  However, there are no guarantees that it will be supported.  You could try running a windows VM and connecting the scanner that way, but the issue is drivers and it might not work at all if there are no linux drivers.  Scanners are probably the worst supported peripherals there are (windows or linux... my first scanner wasn't supported by windows XP but was by linux!), so good luck.

---

### Post by SunnyRabbiera on 2007-07-20
Please understand that linux and windows are two different operating systems, and what might work in windows might not work in linux.
linux may not work for every little piece of hardware you have, this is no fault of linux as most of your hardware and software out there is designed for, you guessed it... windows
you can try vitrual machine software, you can try wine or even crossover but please keep in mind the only real way to make things work exactly like they do in windows is to use windows itself.

---

### Post by kingof1981 on 2007-07-21
why have you changed to linux...
if you want to run win apps go back to win xp...
but i see now you maybe doesn't want to go back to winXP because you've seen how fast and good looking linux is...
there are many ways to install windows apps....
-wine
-vmware
-winedoors
-xcrossover
-virtualbox 

with the last one you even can install a winXP OS(or other OS's) that almost work stable...
normally you don't need any of this...
Linux has many different applications for everything you want to do...

thinklinux

---

### Post by Extreme Coder on 2007-07-21
If you could give the exact model name of the scanner and camera, we might be able to help you easier.
And is there any other windows software you need to use?

---

### Post by serdas on 2007-09-07
i have a similar problem
just yesterday i installed Ubuntu, looks great and fast but i need to install my wireless card (Belkin, Wireless G Desktop Card, F5D7000) the CD that i had did not work
i could not install the sofware .
what could i do to solve this issue?
Thanks

---

### Post by dca on 2007-09-07
Bottom line:
 
You can use "Wine" which makes apps like MS Office and Acrobat run using the 'not an emulator' Windows API but again it's a crap shoot'.  You have to investigate to see if the application actually works on other forums or ask before you do it.
 
You can virtualize the entire Windows OS inside Linux using 'vmware', 'virtual box', 'Xen', etc.
 
Or, you can dual-boot using GRUB as the decider for which OS you'll boot into for that session (Linux or Windows).

---

### Post by serdas on 2007-09-07
it seems like the best option is to use wine
but i am looking at the web site there is nothing to download.
i have no internet at home yet o the machine. how would i download wine?
thanks again

---

### Post by karellen on 2007-09-07
if you need windows apps so badly why don't you stick with windows? or at least dual-boot. there is no feasible workaround for the native software ecosystem of windows

---

### Post by mips on 2007-09-07
> **serdas said:**
> it seems like the best option is to use wine
but i am looking at the web site there is nothing to download.
i have no internet at home yet o the machine. how would i download wine?
thanks again

It's in the repositories. Without internet you are screwed.

---

### Post by scxtt on 2007-09-08
> **serdas said:**
> i have a similar problem
just yesterday i installed Ubuntu, looks great and fast but i need to install my wireless card (Belkin, Wireless G Desktop Card, F5D7000) the CD that i had did not work
i could not install the sofware .
what could i do to solve this issue?
Thanksyou don't need the software, per se - you need the driver ... lots of wireless cards work in linux OotB, if yours doesn't you should check into ndiswrapper (to use the windows driver) - the only wireless card i have is in my laptop and luckily it's an intel based machine, it all works :)

---

### Post by igknighted on 2007-09-09
> **serdas said:**
> i have a similar problem
just yesterday i installed Ubuntu, looks great and fast but i need to install my wireless card (Belkin, Wireless G Desktop Card, F5D7000) the CD that i had did not work
i could not install the sofware .
what could i do to solve this issue?
Thanks

Create a thread in the beginners or the networking forum, this isn't really a support forum.  In that thread post the results of the command "lspci" (run in the terminal).  Make sure your card is plugged in at this time.  This will tell what the chipset is (there are several that could be in that card).  Chances are, it will work right out of the box.  If it doesn't, you may need to browse the windows driver CD and pull a few files off, then use a program called ndiswrapper to adapt the windows files into files Ubuntu can use.  There are how-to's around, just use the forum search function.

---

### Post by Midwest-Linux on 2007-09-14
Re: How to install windows apps ....Try React OS

I tried React OS, I tried installing a number of Windows apps on React OS. But Juice for Windows did install. Unfortunately React OS is not ready for primetime, but it seems promising. It uses a Windows like interface and even has the install  interface like Windows does.

 However I did not get a chance to see how well Juice worked on React OS...see React OS could not get me on the internet because it could not find a driver for my Ethernet card when in fact every linux variant I did try out on that computer DID find the card and driver effortlessly. Did I mention that ReactOS couldn't  find a driver for my video card either...even though I had a video display?

 Try React OS, just realize it is still in development yet and not yet finalized. When I have more time, I think I will re-install it again to test it out further, even trying to find a driver for the ethernet (to put on a CD to install it in React OS ) so I can see how well Juice for Windows works with React OS.

Its worth mentioning here, that you can buy computers on E-Bay with no OS and install the various linux vaiants on them. You can buy PIII 500 Mhz machines with 128 Ram and 10 gig hard drives for like $20 and not including shipping.

---

### Post by BruisedQuasar07 on 2007-09-22
hockey97,

Please do not be turned off by invitations to "go back to windows" 

It is this narrow enthusiast gusto that has prevented Linux from already being a major desktop OS, instead of the inferior, monopolistic, overpriced MS Windows. 

When Personal Computers first appeared in the 1970s, a lot had to be figured out. As much as Apple, Commodore, Timex,
Tandy, and a few other early PC makers went after the mass  market. they had too many macho enthusiasts, too
few enthusiasts and professionals who were good communicators, who understood that the average user, many of whom are quite skilled and talented people in fields other than computers, sees a PC as a tool, not a career or hobby. Before Internet, my friends and I invested
hours into figuring out how to connect online. When we finally got connected, all we had was a BBS blinking cursor. (BBS: Bulletin Board Service--a pre-Internet hobby thing in which home PCs were connected by phone modems & special software into into a global network.)

If running windows applications in Linux were a stupid thing to want to do, talented Unix\Linux project groups would not
work so hard trying to develop the ultimate program that can run windows apps.

Don't let anyone leave you feeling goofy or dense for wanting to know how to do it. If I were you I would read up on WINE, VMware, Winedoors, and Virtualbox, at wikipedia... Just
search one at a time. You will get a well written history and explanation and links for each one. You can better decide from that, which one you want to try. One of them, Virtualbox, I think, is a project that seeks to allow any program run on Linux, Windows, or BSD. 

What I advise Newbies to do is to first check [ osalt.com ] & find out what quality Linux alternatives (they are free) there are for Windows programs. 

The programs you cannot replace with a Linux alternative, can be purchased as commercial Linux apps (at a much cheaper price than Windows Apps). 

3) You can look into using WINE to run programs in Linux 
(Check [appdb.winehq.org/browse_by_rating_php] to find out which programs run well, etc.

4) You can consider running windows in a Virtual Machine. The favorite for doing that lately is the free Virtualbox, which is a general full virtualizer for x86 apps. Virtualbox can be installed and run from Linux OR Windows. 

I hope this helps get you started.

--Bruised

---

### Post by wolfen69 on 2007-09-22
> **BruisedQuasar07 said:**
> hockey97,

Please do not be turned off by invitations to "go back to windows" 

It is this narrow enthusiast gusto that has prevented Linux from already being a major desktop OS, instead of the inferior, monopolistic, overpriced MS Windows. 

When Personal Computers first appeared in the 1970s, a lot had to be figured out. As much as Apple, Commodore, Timex,
Tandy, and a few other early PC makers went after the mass  market. they had too many macho enthusiasts, too
few enthusiasts and professionals who were good communicators, who understood that the average user, many of whom are quite skilled and talented people in fields other than computers, sees a PC as a tool, not a career or hobby. Before Internet, my friends and I invested
hours into figuring out how to connect online. When we finally got connected, all we had was a BBS blinking cursor. (BBS: Bulletin Board Service--a pre-Internet hobby thing in which home PCs were connected by phone modems & special software into into a global network.)

If running windows applications in Linux were a stupid thing to want to do, talented Unix\Linux project groups would not
work so hard trying to develop the ultimate program that can run windows apps.

Don't let anyone leave you feeling goofy or dense for wanting to know how to do it. If I were you I would read up on WINE, VMware, Winedoors, and Virtualbox, at wikipedia... Just
search one at a time. You will get a well written history and explanation and links for each one. You can better decide from that, which one you want to try. One of them, Virtualbox, I think, is a project that seeks to allow any program run on Linux, Windows, or BSD. 

What I advise Newbies to do is to first check [ osalt.com ] & find out what quality Linux alternatives (they are free) there are for Windows programs. 

The programs you cannot replace with a Linux alternative, can be purchased as commercial Linux apps (at a much cheaper price than Windows Apps). 

3) You can look into using WINE to run programs in Linux 
(Check [appdb.winehq.org/browse_by_rating_php] to find out which programs run well, etc.

4) You can consider running windows in a Virtual Machine. The favorite for doing that lately is the free Virtualbox, which is a general full virtualizer for x86 apps. Virtualbox can be installed and run from Linux OR Windows. 

I hope this helps get you started.

--Bruised
BruisedQuasar07 has spoken! So it is written, so it shall be done. jk.

---

