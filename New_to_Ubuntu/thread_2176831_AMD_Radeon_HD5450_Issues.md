---
title: "AMD Radeon HD5450 Issues"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by beben-alexander on 2013-09-26
I have just puchased a Dell Optiplex GX280 and installed an AMD Radeon HD5450 1GB graphics card, this is inserted in the PCI express slot.  I am currently experiencing significance graphics issues from boot into ubuntu with green horizontal lines present.  

Activating fglrx results in a total loss of screen resolution into a colorful mess which is unintelligible. After purging the fglrx drivers and re installing open source drivers I have managed to get a least some functionality back but the original issue still remains.  As this issue is concurring from boot, is this an issue with the graphics card or is it an Ubuntu issue?

Please help as I have run out of options from the visible threads.

---

### Post by centaurusa on 2013-09-26
My solution to a similar problem with an HD6450 video card was rather drastic - uninstall Ubuntu 12.04 and switch to Linux Mint 13 (Maya).  My situation was that Ubuntu 12.04 functioned correctly when booting from a live-USB memory stick but had all sorts of video issues when installed on the hard drive.  Switching to Mint solved all the problems.  This is rather surprising since Mint is essentially a version of Precise (12.04).

Personally, I don't like the Unity interface and have always installed Gnome Classic.  Mint, with the Mate interface, can be configured to look much like Gnome so the Mint distro is a good fit for my purposes.  The other key fact is that, because Mint is closely related to Ubuntu, most of the solutions to any problems with Ubuntu also apply to Mint.  

The string of problems - and attempts at fixing them with Ubuntu 12.04 and the Radeon HD6450 - are documented at [http://linuxnorth.wordpress.com/2013/06/28/a-hint-of-mint/](http://linuxnorth.wordpress.com/2013/06/28/a-hint-of-mint/).  Search on the keyword "HD6450" for quick access to the various posts.  

I should note that this post is not designed to "bash" Ubuntu.  I have used Ubuntu very successfully for a number of years, especially the 10.04 LTS release, and also ran 12.04 on one machine for a year without incident.  The issues were solely related to using 12.04 on a machine using an HD6450 video card.

---

### Post by verymadpip on 2013-09-26
Hi there.
I installed one of these cards in a rig running Xubuntu 13.04 64 bit this morning & it's all good.  I'm using the open source default driver.
It actually replaced another HD5450 which I gave to a friend when his older GPU stopped working.  His is also all good. I don't recall which OS he is running as he was thinking of trying out Mint for a while instead of Ubuntu.  (I imagine it would be current releases of either OS).  I don't know which driver he is using unfortunately.

It sounds like a bad card to me, but what do I know.
Maybe more detail about your rig would help.

---

### Post by DuckHook on 2013-09-26
Hi beben-alexander and welcome to the forums.

1. Which version of Ubuntu are you running?
2. Which fglrx driver did you install? Do you recall the version number?
3. How did you install it? Directly from the repositories or compiled on your own?
4. If you are dual booting, does the card run properly under another OS?
5. If so, what is that alternate OS?

I was only able to get my 7950 working properly with the latest (at the time, 9.012) fglrx. None of the repository options (8.96 versions) would work with full functionality. AMD is currently at version 10.10, so my version is now old, but it works so I'm sticking with it. I learned long ago not to mess with what works when it comes to video.

[Here]("http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=2.4.1.3.42%3b2.4.1.3.44&contentType=GPU+Download+Detail&ostype=Linux+x86_64&keywords=&items=20") is the link to AMD's site and a collection of their Linux drivers including the latest betas. **WARNING** compiling and running proprietary drivers is a risky undertaking for new users. However, since you have already recovered from one bad driver install, I am assuming that you know how to do it, and are not averse to doing so again.

---

### Post by beben-alexander on 2013-09-27
Hi Duck Hook

Thank you for the reply.  This is all very frustrating!

1. I am running a fresh install of 12.04 (32-bit).
2+3. Sorry I am not sure, but it was the most recent version (yesterday) identified in additional drivers, fglrx was installed directly from the repositories.
4+5. The computer is dual booting between Ubuntu 12.04 and Windows XP, the visual disturbance is present from boot, into Ubuntu and Windows.  I installed the drivers from the CD in XP and these did not seem to make any difference.

Could this be a power supply issue or a duff card as the fact it is present in bios and XP makes me think its not a driver issue but a card/hardware issue. Additional information on the PC: Dell Optiplex GX280, 3.2 Ghz Pentium 4, 3 Gb RAM, with a 280 watt psu and graphics card is (was as I am currently using on-board graphics) plugged into the PCI-Express port. 

I will try compiling the drivers and see what happens.  Never done it before, but can follow instructions and been 'fiddling' with Ubuntu since Hardy came out.  Would not say I was a pro, probably an upper beginner! 

Cheers

---

### Post by coffeecat on 2013-09-27
> **beben-alexander said:**
> 
4+5. The computer is dual booting between Ubuntu 12.04 and Windows XP, the visual disturbance is present from boot, into Ubuntu and Windows.

> **beben-alexander said:**
> Could this be a power supply issue or a duff card as the fact it is present in bios and XP makes me think its not a driver issue but a card/hardware issue.

I agree with you about the possibility of a bad card. I've used a Radeon HD5450 in Ubuntu 12.04 and I got perfectly acceptable performance with the default open source driver without any artefacts or distortion. I never bothered trying the fglrx driver. 

If you are seeing the same artefacts in Windows, this would indicate a problem with the card rather than the driver and I suggest not wasting time compiling the proprietary driver. Do you see these visual artefacts at the POST screen?

Some other things to look into. Check that the video cable is OK. Try another one if you have a spare. Is the monitor OK used on another computer if you have access to one?

---

### Post by Mark Phelps on 2013-09-27
Is it a Dell monitor? Asking because I had a Dell monitor that started displaying vertical wide red lines -- and shortly after that, it went out.

You should try connecting another monitor to the Dell to rule out monitor hardware problems.

---

### Post by beben-alexander on 2013-09-27
Thanks for all the responses.

I do not think it is the monitor or display as both work well when I remove the card and use the internal graphics card.  I have also used my laptop with the cable and monitor to double check.  The artifacts are present when I plug the pc into my tv with the hd I cable also.  To answer your question coffee cat - artifacts are present on every screen from boot - bios, Ubuntu, windows XP (which now will not even start up with the card) and during shutdown, Not seen a normal screen with this card!

---

### Post by DuckHook on 2013-09-27
I think the problem is clearly with the card. It is extremely unlikely that two very different OSes would create the same symptoms if it were a driver issue. You have taken all the steps needed to isolate your problem, and everything points to getting a new card (or exchanging if it is still under warranty).

---

### Post by deadflowr on 2013-09-27
Trying blowing out the pcie slot.

Sometimes dust or particulates can cause the contact points to not connect well.

I've the same card, and have used both radeon(preferred) and fglrx(simply to see if I could) without issues.

after cleaning the slot and the card, if problems persist, then you can consider it a card problem.
or the slot is bunk.
it would help to find out which, if you had access to another machine you could throw the card in.
If it works in another machine then it's the slot and if the problem remains, then it's the card.

---

### Post by GH12 on 2013-10-17
I had some problems getting Ubuntu 13.04 to work properly when upgrading from 12.10 with an AMD HD5450 graphics card. A clean, new installation of Ubuntu 13.04 and then installation of the October 8, 2013 beta release of the AMD driver available at: [[SIZE=2]support.amd.com/en-us/download[/SIZE]]("http://<font size=&quot;2&quot;>support.amd.com/en-us/download</font>")[SIZE=2] solved everything. It seems to work flawlessly now. I am getting a frame rate of about 3200 FPS with glxgears[/SIZE]

---

