---
title: "Overclocking Your Nvidia Graphics Card"
date: 2007-03-17
forum: Outdated Tutorials &amp; Tips
---

### Post by fatsheep on 2007-03-17
[SIZE="5"]**Overclocking Your Nvidia Graphics Card**[/SIZE]

Overclocking your Nvidia graphics card doesn't have to be difficult.  Nvidia's proprietary drivers actually include a nice little overclocking tool by default called "coolbits".  In this guide, I show you how to enable coolbits, use it to overclock, and have your overclocking settings applied when your computer starts up for convienance.

Before we begin, note that you should already have the Nvidia proprietary drivers installed. Also remember that the *nvidia-settings* tool that I will refer to later in the guide is usually available in a shortcut located under the *Applications > System Tools* menu.  If it isn't, just run the command *nvidia-settings* in the terminal to access it.

[SIZE="3"]_**Enabling Coolbits**_[/SIZE]

Coolbits will provide an easy to use overclocking utility inside nvidia-settings (typically you can access this through Applications > System Tools > NVIDIA Settings). Here's how to install it:

We are going to edit your /etc/X11/xorg.conf file so the first thing I would do would be to back it up with a command like this (which would create a backup called "xorg.conf.bak" in the /etc/X11 directory):
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg_backup.conf
```

If we have any problems after editing the file, we can just revert to our backup with this command:

```
sudo cp /etc/X11/xorg_backup.conf /etc/X11/xorg.conf 
```

Now for the actual editing:

```
gksudo gedit /etc/X11/xorg.conf 
```

This will open up your xorg.conf file in gedit.  Search for a section of text that begins with Section "Device"

Mine looks like this:

> 
Section "Device"
Identifier "NVIDIA Corporation NV43 [GeForce 6600 GT]"
Driver "nvidia"
EndSection 

Your's may look different depending on what graphics card you have.  We need to add the following text to enable coolbits:

> Option "Coolbits" "1" 

For reference, here's what my section looks like after I have enabled coolbits:

> Section "Device"
Identifier "NVIDIA Corporation NV43 [GeForce 6600 GT]"
Driver "nvidia"
Option "Coolbits" "1"
EndSection 

Now save the file and open up nvidia-settings.  There should now be a clock frequency tab.

[IMG]http://img72.imageshack.us/img72/3455/screenshotnvidiaxserverns0.png[/IMG]

_**[SIZE="3"]Overclocking With Coolbits[/SIZE]**_

Using coolbits to overclock is straightforward.  Just configure your frequencies, hit apply and you're done.  The "Auto Detect" button can be very helpful for finding a good overclock.  The frequencies it gives you are usually a bit high so you might want to decrease them a bit especially if you are noticing any artifacting.

One problem is that your frequency settings are restored to the hardware defaults after you restart the computer.  Reconfiguring the settings everytime I bootup is a pain so I found a command that will do this automatically for us:

```
nvidia-settings -a GPUOverclockingState=1 -a GPU2DClockFreqs=<2dGPU>,<2dMEM> -a GPU3DClockFreqs=<3dGPU>,<3dMEM>
```

You need to replace the bold type with your actual settings.  So I would replace <2dGPU> with my 2d core frequency (in megahertz).  I would replace <3dMEM> with my 3d memory frequency (in megahertz).  On a side note, I'd recommend leaving the 2d settings at their default values (unless you want to play pong at 5000 fps :-p).  3d settings are what you want to increase for gaming performance and such.  Just for reference here is my script:

```
nvidia-settings -a GPUOverclockingState=1 -a GPU2DClockFreqs=300,1000 -a GPU3DClockFreqs=550,1100.  
```

Replace my settings with your settings in whatever text editor you prefer.  Now we are going to make this command run every time we start up the computer.  Go to *System>Preferences>Sessions*.  Select the Startup Programs tab.  

Now simply select the Add button (top right) and paste your command into the text box.  Then hit OK.  From now on your overclocking settings will be conveniently applied when you login.

[img]http://img253.imageshack.us/img253/2820/screenshotsessionspw6.png[/img]

---

### Post by fatsheep on 2007-03-21
Did anyone find this helpful?  Does anyone here use an alternative method to overclock their Nvidia GPU?

---

### Post by hikaricore on 2007-03-21
You might want to mention to any PCI Nvidia users that
Overclocking your gpu/memory too much higher than the
speed of your [FSB]("http://en.wikipedia.org/wiki/Front_side_bus").  **Will** cause artifacts and *may*
possibly lock up your entire system.  APG/PCIE users don't
have to worry about this quite as much, but I thought it was
worth pointing out.

---

### Post by fatsheep on 2007-03-23
> **hikaricore said:**
> You might want to mention to any PCI Nvidia users that
Overclocking your gpu/memory too much higher than the
speed of your [FSB]("http://en.wikipedia.org/wiki/Front_side_bus").  **Will** cause artifacts and *may*
possibly lock up your entire system.  APG/PCIE users don't
have to worry about this quite as much, but I thought it was
worth pointing out.

That's interesting.  Do PCI graphics cards share the frequency of the FSB?

---

### Post by hikaricore on 2007-03-23
> **fatsheep said:**
> That's interesting.  Do PCI graphics cards share the frequency of the FSB?

If I'm not mistaken yes, I believe that PCI cards are limit capped by the FSB.

So you can technically make the card go much much faster, the system
bus just can't handle anything more than it's designed for.  So you get
video corruption and eventually a crash.  (the effect of shoving paper money
into a coin slot comes to mind, sure it works but it doesn't do much damn good)

Example my FSB is 400mhz.  If I try and OC my card's memory any higher than 400 (defaults 350ish) the system locks.  If I try and OC the GPU (defaults 285) above 375 or so, I get graphical corruption, GPU above 400 locks the system as well.

I tweaked around a little with it and about the best I can get while staying stable is:

350gpu/400mem

Unless I'm misunderstanding the workings of the whole mess.  :)

I have a crap motherboard and OCing the FSB is out of the question without
some serious hacking, the bios in these HP computers is absolute trash.

I remember having more frequency control on a gateway lol.

---

### Post by techno-mole on 2007-05-24
i found this guide after alot of messing around trying to find a way to easily over clock my 7600gs, and ive managed to get coolbits active and i now have access to the gpu and memory for my crd, but the auto detect function doesnt work, that is to say that it is greyed out and you cant click on it, so do you have to do something else to enable the auto detect function ?
im using fiesty, with an nvidia 7600gs agp card (latest drivers installed with envy)
cheers.

---

### Post by JoshuaJamZ on 2007-05-26
> **techno-mole said:**
> i found this guide after alot of messing around trying to find a way to easily over clock my 7600gs, and ive managed to get coolbits active and i now have access to the gpu and memory for my crd, but the auto detect function doesnt work, that is to say that it is greyed out and you cant click on it, so do you have to do something else to enable the auto detect function ?
im using fiesty, with an nvidia 7600gs agp card (latest drivers installed with envy)
cheers.

Same problem here with the auto-detect button being greyed out. Any idea's?

---

### Post by smithman89 on 2007-06-04
Ok, for me, the auto detect only works for the 3d Clock frequencies.  But i have a question, if you go into the nvidia-settings, and look at the video card, even though mine is a GeForce 6600 AGP 256mb, it says pci card under the bus type.  I am confused, also, anyone know a good speed to OC to?  My defaults according to the settings are gpu=300mhz, ram=500mhz.

---

### Post by jacc1234 on 2007-06-04
Thanks for the guide, i have the coolbits option now but it wont save any of my frequency changes and I also dont have autodetect. I am running feisty and using the 9755 amd64 nvidia-glx-new drivers.

Thanks,
Jacc123

---

### Post by fatsheep on 2007-06-12
@ smithman89: You have to experiment with overclocking.  I'd work first on your core frequency and then on your memory frequency.  Raise the core frequency and run benchmarks, then raise it again and run more benchmarks and watch out for graphical glitches like artifacting.  If you see any glitches then lower the core frequencies.  You might want to monitor your temperature as well but unfortunately I don't know of any good temperature monitors under Linux (I used rivatuner on Windows).  Look online for some video overclocking articles, they should help you out.  Good luck, and don't fry anything! ;)

> **jacc1234 said:**
> Thanks for the guide, i have the coolbits option now but it wont save any of my frequency changes and I also dont have autodetect. I am running feisty and using the 9755 amd64 nvidia-glx-new drivers.

Thanks,
Jacc123

It's greyed out for me as well now, it never used to be...  That's strange.  

> **techno-mole said:**
> i found this guide after alot of messing around trying to find a way to easily over clock my 7600gs, and ive managed to get coolbits active and i now have access to the gpu and memory for my crd, but the auto detect function doesnt work, that is to say that it is greyed out and you cant click on it, so do you have to do something else to enable the auto detect function ?
im using fiesty, with an nvidia 7600gs agp card (latest drivers installed with envy)
cheers.

I didn't anything else to enable auto detect before but it no longer works.  I have the same problem as you do.

---

### Post by asymmetric on 2007-06-12
@fastsheep

don't know if you don't consider them good, but both nvidia-settings and nvclock have temperature monitors :)

also, i can't edit speeds.. when i click apply after a change, the speed is automatically brought back to its previous value!

asy

---

### Post by smithman89 on 2007-06-12
> **fatsheep said:**
> Good luck, and don't fry anything! ;)

I'll try not to, i have to be careful with OCing, mostly because my card doesnt have a temp monitor, even more so, my CPU is a P4 Prescott, so my case is already pretty hot.  Im thinking about building a new computer soon, so once i do, i will mess around with the old one, hopefully learns some good tips about overclocking.

---

### Post by Megatog615 on 2007-09-23
Anybody have an update on why the auto-detect button is grayed-out?

---

### Post by Posterus on 2008-05-11
ok this is weird and I hope this happend to someone else but everytime i try to change the clock settings in the OC menu I click apply and it goes right back to the default settings....anyone have any suggestions?

**EDIT**

sorry for posting this question alot lol i didnt read the last couple posts

**2ndEDIT** lol

to anyone who has the OC issues where the frequencies wont stick or the auto detect button is grayed out...
Do you have the Go series? or any mobile series unit? because if you read the "help" it says that the OC options are limited to the FX series and newer non-mobile units.... =\

Kudo's to anyone who can find a way passed this =]

---

### Post by atlas95 on 2008-05-13
How to underclock?

---

### Post by spadewarrior on 2008-06-01
The 'Auto Detect' button is grayed out for me until I select '3D Clock Frequencies'. I have an nVidia GeForce 7600gt. 

I have now done everything in the tutorial, but after restarting/logging out and back in, the nvidia-settings revert back to their original state. I'm using xubuntu, so instead of 'sessions' I added the command to 'Auto Started Applications'. Could this be the reason or is there something else I've not done?

EDIT: sorted it out. It was because I left the '<' and '>' symbols in the command, causing a syntax error. All worky now! Thanks!

---

### Post by jasontu on 2008-06-04
Will Coolbits help me stop the issue of the fan ramping up to full blast (full noisy too) if the GPU gets hotter than 40C which it always does?

---

### Post by nurfimus on 2008-06-27
> **spadewarrior said:**
> The 'Auto Detect' button is grayed out for me until I select '3D Clock Frequencies'. I have an nVidia GeForce 7600gt.

I am using a GeForce 8600M GT with driver version 169.12. I am on Ubuntu 8.04. I did everything in the Tutorial. My 'Auto Detect' is still grayed out even after selecting '3D Clock Frequencies'. I also have an issue where after I set the new clock frequencies and click 'Apply', the settings and slider bars revert to the previous setting (default setting). Adding the line of code to my startup up sessions did not work either. For some reason, NVIDIA X Server Settings is not letting me change the clock frequencies at all.

Any ideas?

Thanks

---

### Post by nurfimus on 2008-06-28
Ok.. so I have a new problem now (likely due to my own noob-stupidity)...

I tried updating the NVIDIA driver from 169.12 to 173.14.05. Had some issues closing out of X11 and doing it at root level, but I was able to install it. I updated the driver, but for some reason after I rebooted my display is stick at 640x480. The NVIDIA driver is not showing up in System>Administration>Hardware Drivers, and it won't let me resize the resolution in System>Preferences>Screen Resolution.

Does anyone know how I can resolve the resolution issue?

Thanks in advance!

---

### Post by nurfimus on 2008-06-28
I just fixed the above issue regarding screen resolution. I'm now running 173.14.05 driver, but I still have the same original issue where I can't get my clock frequency chances to apply. I click the button and frequencies revert to initial setting.

Think I'm about to give up on this one for now... but if anyone has a suggestion, I would greatly appreciate it.

---

### Post by clarknova on 2008-07-14
I'm running driver version 173.14.09 from nvidia.com and after enabling coolbits, the overclocking in nvidia-settings works as expected. You can see in this screen shot that I have my 8600GT underclocked at the moment.

db

---

### Post by drew.woods on 2008-08-10
I'm having a problem overclocking my 8400GS.  When I set a new clock frequency, my pc instantly crashes and just presents me with a white screen.

I thought this might have been since I'm clocking it too high, but the same thing happens if I set the frequencies to their factory settings.

I'm using the 177.3 Beta drivers on Hardy, has anyone else experienced a similar issue?

---

### Post by mastergunner on 2008-09-10
.....

---

### Post by bobbob1016 on 2008-09-10
> **drew.woods said:**
> I'm using the 177.3 Beta drivers on Hardy, has anyone else experienced a similar issue?

Could they be beta for a reason?  (Sorry for the rudeness, but a lot of people go bleeding edge for no reason, beta video card drivers are bleeding edge)

---

### Post by Doonak on 2009-06-10
Hey guys, I'm about 3 weeks into Ubuntu 9.04/Linux (Newbie), but I'm a L337 experienced windows user (ugh). Anyway, I got through a ton of posts and advice, and these forums in particular are an amazing resource, but I haven't been able to find any resolution to the issues I'm having, and it's really starting to bother me.

I've got an Asus X83V Laptop.

It runs:

Intel Centrino Dual Core 2.0ghz processor.
4 gigs of DDR2 ram.
Nvidia 9300m GS 512 DDR3 dedicated graphics.
I'm using Nvidia Accelerated Graphics Driver 180 (recommended)
Dual Boot with Vista 64 bit/Ubuntu 64 bit.


I've activated Coolbits, I've installed the script that runs at boot and reconfigures my nvidia settings, I've tried setting the script to OC my card during boot, ALL HAVE BEEN EPIC FAILS... I noticed a small post earlier (in this thread) that said that the (newish) Nvidia Mobile graphics cards are not OC-able. I was also informed through online research that is seems that my processor isn't OC-able, via the BIOS. Can anyone confirm or deny either of these claims for me?

I'd be extremely greatful if someone could tell me a way around all of this, because my system could turn way up, and even running WOW with the graphics all the way up only gets it to 42C (Nvidia Settings says the slowdown point is around 102C). So OCing my system would be extremely beneficial, and plausible.

Anyone got any ideas, or am I just a sad case of capitolism and stupid people burning out to many laptops? Any help would be great, so thanks in advance!

---

### Post by louie123 on 2010-12-29
how can i over clock my ati raeon graphics card

---

### Post by Ya'lachim on 2011-02-27
> **jasontu said:**
> Will Coolbits help me stop the issue of the fan ramping up to full blast (full noisy too) if the GPU gets hotter than 40C which it always does?
Just installed 10.4 (64bit) on Asus x83v rather comfortably. Also had the full blast fan issue. Seems i got it  solved by changing settings in the BIOS (press ESC-key at startup) contradictionary to their title and value - disabling sth like thermal ... (don't have the laptop here right now). Also disabled a value related to Screen while i was in there. This solved a brightness issue, was rather dim before - now showing a more "normal" appearance -, without interfering with sound (read about issues where adjusting brightness caused sound problems...). Hope you are still checking your posts from time to time and find this; and off course that my method helps. Cheers, Achim

---

