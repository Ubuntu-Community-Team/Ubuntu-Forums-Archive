---
title: "Which Ubuntu version recommended for ASUS Eee PC 1015 Netbook?"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by swarup on 2011-10-14
Just got a netbook, and want to put Ubuntu on it. Here are the details of the machine:

ASUS Eee PC 1015PEB-BK603 Refurbished Netbook - Intel Atom N450 1.66GHz, 1GB DDR2, 160GB HDD, 6-Cell, 10.1" SVGA, Windows 7 Starter, Black.

I want to give this to a friend of mine who lives in a rural part of India-- so I want to make sure Ubuntu is working very well on it. This is why I ask-- should I put the latest Ubuntu version on it, or perhaps on earlier one like the LTS 10.04?

---

### Post by RememberWhenItRained on 2011-10-14
With older computers, i would generally stick with the LTS version. Depending on the performance and speed, you might also consider Xubuntu, though i don't see why Ubuntu wouldn't work perfectly fine.

---

### Post by swarup on 2011-10-14
How well are the newer versions working on the netbooks-- for example 11.04, or I see that 11.10 is also out now. Might the netbook version of those also work quite smoothly?

Also-- on the Ubuntu download page, where it gives the option for running it "with Windows" (Wubi), does that mean running Ubuntu as a virtual window within the Windows OS?

---

### Post by stalkingwolf on 2011-10-14
I have super os 10.10 and ubunt 11.04 dual booted on my EEE1005AH.
both work fine.

---

### Post by Nytram on 2011-10-14
I've got an eee 1005 with similar specs to yours, and everything runs fine. I'd suggest trying the latest version, download the ISO onto a USB stick and test it out.

---

### Post by kolinab on 2011-10-14
+1 for 'go for it' with the latest version. We have a small Samsung netbook with a teeny weeny Atom processor and it runs 11.04 very nicely - I plan to upgrade it to 11.10 in the coming days.

---

### Post by vajorie on 2011-10-14
> **swarup said:**
> Netbook - Intel Atom N450 1.66GHz, 1GB DDR2, 160GB HDD, 6-Cell, 10.1" SVGA, Windows 7 Starter, Black.

I have an Acer netbook with similar specs; 11.04 runs fine with it with unity3d, so should 11.10. Also have an 10 years old laptop on which 11.04 runs fine (it switches to 2d by itself because of my graphics card, which is very convenient). Go for the last release.

---

### Post by AlmightyHeretic on 2011-10-14
I've got an Asus 1015PN and I run Ubuntu 11.04 on it with minimal problems. 10.04 does not work well for my system at all. I can't vouch for 11.10 yet since my upgrade failed on me. Upgrading never seems to work for me. I am currently in the process of doing a clean install. I would try the latest version and see how it works for you. You'll have to install it to get a good idea though. The liveCD always runs cleaner than the actual install so it can't really be trusted. And stay away from Wubi! Netbooks don't like it. Especially single-core Atoms. :P

---

### Post by swarup on 2011-10-14
Thanks for the encouragement, folks! I've just downloaded 11.10 and will try installing it this evening. 

One question-- I have to put the distro onto a USB stick. Here are the Ubuntu website instructions for how to do that:

>    1. Insert a USB stick with at least 2GB of free space
   2. Open the dash and search for Startup Disk Creator
   3. Select the Startup Disk Creator to launch the app
   4. Click 'Other' to choose the downloaded ISO file
   5. Select the file and click 'Open'
   5. Select the USB stick in the bottom box and click 'Make Startup Disk'
   6. That's it! When the process completes, you'll be ready to restart your computer and begin installing Ubuntu.

I'll be doing this work on a laptop with Ubuntu 9.04, and I don't think there is any such thing in it as a "dash", or a "Startup Disk Creator". So what should I use to put the iso on my flash drive? I assume you can't just paste it there. 

Usually when installing a distro on a laptop, I'll use the Brasero Disc Burner to burn the iso to a CD. Can I do that same thing, and just burn the iso to a USB stick instead? Or would I have to follow some different procedure?

---

### Post by AlmightyHeretic on 2011-10-14
You should be able to burn it to disc just the same and use an external cd drive to install. I use unetbootin to put all of my installs on flash drive and I haven't had any problems yet. Good luck!

---

### Post by swarup on 2011-10-14
I don't have an external cd drive. What is the procedure for putting the iso onto a USB stick?

---

### Post by AlmightyHeretic on 2011-10-14
With unetbootin it's pretty easy. You can either choose a distribution to download from within the program or select an iso you've already downloaded. It's as simple as plugging in a flash drive and clicking the mouse a few times.

unetbootin.sourceforge.net/

---

### Post by dFlyer on 2011-10-14
> **swarup said:**
> just got a netbook, and want to put ubuntu on it. Here are the details of the machine:

Asus eee pc 1015peb-bk603 refurbished netbook - intel atom n450 1.66ghz, 1gb ddr2, 160gb hdd, 6-cell, 10.1" svga, windows 7 starter, black.

I want to give this to a friend of mine who lives in a rural part of india-- so i want to make sure ubuntu is working very well on it. This is why i ask-- should i put the latest ubuntu version on it, or perhaps on earlier one like the lts 10.04?

lts 10.04.

---

### Post by swarup on 2011-10-14
> **AlmightyHeretic said:**
> With unetbootin it's pretty easy. You can either choose a distribution to download from within the program or select an iso you've already downloaded. It's as simple as plugging in a flash drive and clicking the mouse a few times.

unetbootin.sourceforge.net/

Looks perfect. I downloaded the utility you mention here, and according to the instructions on the site, went to properties -> permissions and checked "executable". Upon doing so, as I understand it is supposed to run when I double click on it right? But when I do so, nothing happens. What do I need to do to run this?

---

### Post by AlmightyHeretic on 2011-10-14
Are you trying to run the program on linux or windows? There are different versions for different platforms so you need to make sure you've downloaded the appropriate one.

---

### Post by swarup on 2011-10-14
Yes, there are separate downloads for Win, Linux, and Mac. I downloaded the one for Linux, and am trying to run it in Ubuntu 9.04 on my Laptop.

---

### Post by AlmightyHeretic on 2011-10-14
I've always installed the program to Ubuntu. I can't remember the last time I used 9.04 and the only time I've run it from desktop was in windows.

sudo add-apt-repository ppa:gezakovacs/ppa
and then,
sudo apt-get update
sudo apt-get install unetbootin

I just figured out how to copy and paste on my phone. :P

---

### Post by swarup on 2011-10-14
Thanks so much for writing all that in your phone :)
As 9.04 is no longer supported, it has no access to the repositories as far as I know. I tried it anyway, but it wouldn't do it. 
But the file which I downloaded should have worked. I'd think putting this iso on the pendrive should be a piece of cake. Well, I'll keep trying. If you get any more ideas, please do let me know.

---

### Post by Gene_J on 2011-10-15
I have tried Ubuntu 10.04 and 11.04 on my ASUS and both work fine. I personally prefer Xubuntu 11.04, as I feel it runs a bit faster and seems to be easier to understand for the 10 year-old who is the main user. Your mileage may vary...

---

### Post by AlmightyHeretic on 2011-10-18
Sorry it took so long for me to reply. I haven't been on my computer lately. Ubuntu should have a Live USB creator built in by default. I read that it comes preinstalled on 8.04 up to 10.10. It should be under System> Administration> USB Startup Disk Creator. I think it runs about the same as unetbootin but specific to Ubuntu iso's. I've never used it so I'm not too sure. Let me know if it works for you.

---

### Post by WhitePearl on 2011-10-19
> **Nytram said:**
> I've got an eee 1005 with similar specs to yours, and everything runs fine. I'd suggest trying the latest version, download the ISO onto a USB stick and test it out.

I have an 1005ha aswell. 1G memory & 1,6ghz IntelA.

I installed the 11.10 yesterday, now its so slow as to be useless, especially the internet, so I now on my gf´s windows...

First time it went into hibernation, the mousepad ceased to work afterwords. 2nd time the screen went dark?

Looks good though.

How do you make it work?

Thanks for any answer!

---

### Post by vajorie on 2011-10-19
> **WhitePearl said:**
> 
I installed the 11.10 yesterday, now its so slow as to be useless, especially the internet, so I now on my gf´s windows...

Something else is going on there. I'd check the graphics card driver in use and if others report similar issues with your graphics card. And have a look at your wireless card as well while you're at it (sometimes some wifi cards perform better with specific options passed to them). And finally, try it with unity-2d and see if things go smoother. 

Edit: more stuff

Use htop to see if something is hogging the system; try using chromium-browser and see if it helps; take a look at the System Monitor to see if memory is an issue (it shouldn't be); disconnect the wireless and connect with a ethernet cable to see if wireless card is having issues. 

> 
First time it went into hibernation, the mousepad ceased to work afterwords. 2nd time the screen went dark?

Ehue, I got so used to expecting hibernation not to work with any equipment I have, I forgot it existed. I now just use the sleep mode or just shut down the system. Much easier that way...

PS. I found this with a quick google search, you might find even more stuff. Edit: forgot the link [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus_Eee_PC_1005HA](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus_Eee_PC_1005HA)

---

### Post by Paqman on 2011-10-19
> **vajorie said:**
> And finally, try it with unity-2d and see if things go smoother. 


Tbh,I would try this first. Unity-2D works really well on these machines, I wouldn't even bother with trying to run Compiz.

I'd also suggest installing [Jupiter Applet]("http://www.jupiterapplet.org/") and the [jupiter-support-eee](apt:jupiter-support-eee) package to get all the Eee-specific features up and running.

---

### Post by vajorie on 2011-10-19
> **Paqman said:**
> Tbh,I would try this first. Unity-2D works really well on these machines, I wouldn't even bother with trying to run Compiz.

Indeed I would too, but I didn't suggest it as a priority because I couldn't figure out for myself how to make the icons (in the launcher thingy) smaller. It would prove to be a problem on a netbook (with those huge toy-like icons) if there really is no way to make them smaller :)

---

### Post by swarup on 2011-10-19
> **AlmightyHeretic said:**
> Sorry it took so long for me to reply. I haven't been on my computer lately. Ubuntu should have a Live USB creator built in by default. I read that it comes preinstalled on 8.04 up to 10.10. It should be under System> Administration> USB Startup Disk Creator. I think it runs about the same as unetbootin but specific to Ubuntu iso's. I've never used it so I'm not too sure. Let me know if it works for you.

Yes, you are right! It is there where you say, on 9.04. I've already made mine and got 11.10 installed (runs great!). But thanks for the tip!

---

### Post by Paqman on 2011-10-19
> **vajorie said:**
> Indeed I would too, but I didn't suggest it as a priority because I couldn't figure out for myself how to make the icons (in the launcher thingy) smaller. It would prove to be a problem on a netbook (with those huge toy-like icons) if there really is no way to make them smaller :)

Not at all, on a small screen the icons are a nice size. The launcher hides anyway, so the only time they're on screen is when you need them anyway.

---

### Post by fuduntu on 2011-10-19
My primary is a 1015PEM, compiz and other 3d enabled tools work fine.  It's missing the more advanced features, so the humble bundle games etc don't work but otherwise it's a very 3d capable netbook.

It gets even better with the latest xorg 1.11 and Intel driver (I don't think that's available in Ubuntu though).

---

### Post by Nytram on 2011-10-20
> **WhitePearl said:**
> I have an 1005ha aswell. 1G memory & 1,6ghz IntelA.

I installed the 11.10 yesterday, now its so slow as to be useless, especially the internet, so I now on my gf´s windows...

First time it went into hibernation, the mousepad ceased to work afterwords. 2nd time the screen went dark?

Looks good though.

How do you make it work?

Thanks for any answer!

WhitePearl, I'm actually running Gnome Shell as I prefer it to Unity. I recommend you give it a try, as it works really well on my 1005ha. (I've upgraded the memory to 2gb but I don't think this should be an issue.)

---

### Post by WhitePearl on 2011-10-20
Thanks all of you, alot!
Lots of info there.

There wouldnt be any sense in installing any of the old UNR or UNE versions would there?

Sorry about silly questions!

---

