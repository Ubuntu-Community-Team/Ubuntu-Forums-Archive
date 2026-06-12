---
title: "Video Drivers aren't working (ATI 4250)"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by rex_dante on 2012-12-27
Hello all!
I'm here because I'm having terrible time while installing drivers for my 'ATI HD 4250' GPU. I've tried the 'additional drivers' (both ones; post-released etc.) and only one have worked but the results are same; I got a hell lot of 'choppy performance'.](*,)
I've also tried installing via .run packges and broke them to .deb files. I also removed and re-installed the "fglrx" drivers via terminal but no luck. By the way, I managed to install the ATI Catalyst 12.10 drivers but they gave me a very terrible performance too. :\ Currently I've installed the ATI Legacy 12.6 drivers. It seems that the installation went successfully. I rebooted my pc too. I can access the 'configuration' window of the ATI i.e. 'amdcccle'. But It seems that the driver isn't even working. :'(

I don't know WHY, WHY I run into issues ONLY when it comes to install the drivers in UBUNTU while I'm practicing Pentesting on Ubuntu. :\

I've attached the copy of my 'Xorg.0.log' to the thread. Check that for assistance and PLEASE...DO respond sooner. I hope I'll get it fixed ASAP as I'm on the best Linux forum ever. :D
Thanks in advanced.:)

---

### Post by superDave972 on 2012-12-27
In my limited experience, sometimes on old hardware, it is nearly impossible to find drivers for the latest Ubuntu version to use.

---

### Post by rex_dante on 2012-12-27
> **superDave972 said:**
> In my limited experience, sometimes on old hardware, it is nearly impossible to find drivers for the latest Ubuntu version to use.

Hey! don't say that man. I recently upgraded from my old rig to this one-
CPU: AMD FX-4100 Bulldozer Quad-core 3.6 Ghz
MOBO: GA-880GM-D2h

Previous rig-
CPU: Pentium 4 Hyper Threading 3.6Ghz
MOBO: Asus (don't remember full name but it had Intel 865 64mb graphic)

---

### Post by verymadpip on 2012-12-27
I think AMD have dropped to legacy only drivers for 2x, 3x & 4x series cards.  I also seem to recall there being an issue with legacy drivers & 12.10.  New Xorg or something.

Post #3
[http://ubuntuforums.org/showthread.php?t=2094792&highlight=quantal+ATI+drivers](http://ubuntuforums.org/showthread.php?t=2094792&highlight=quantal+ATI+drivers)

---

### Post by ZombieApocalypse on 2012-12-27
It seems AMD have dropped support for the 4000 series and below, so these cards are unsupported in by xorg 1.13, which comes with ubuntu 12.10. So you'll need use the legacy driver and either downgrade to xorg 1.12 or go back 12.04. See [**_here_**]("http://ubuntuxtreme.com/howto/how-to-fix-your-amd-graphics-in-ubuntu-12-10/#") for more info.

My laptop uses a 4250 and I choose to go back to 12.04.

---

### Post by QIII on 2012-12-27
I recommend very VERY strongly AGAINST following any instructions to downgrade X Server.  How it will affect subsequent upgrades of Ubuntu versions cannot be determined.  You essentially break Quantal.

It would be better to move forward with a 5 year LTS in Precise than a broken Quantal.

This is not a failure on the part of Canonical.  No distro that uses X Server 1.13 or beyond will work with the legacy driver because ATi does not support X Server 1.13, not the other way around.

---

### Post by rex_dante on 2012-12-28
> **ZombieApocalypse said:**
> It seems AMD have dropped support for the 4000 series and below, so these cards are unsupported in by xorg 1.13, which comes with ubuntu 12.10. So you'll need use the legacy driver and either downgrade to xorg 1.12 or go back 12.04. See [**_here_**]("http://ubuntuxtreme.com/howto/how-to-fix-your-amd-graphics-in-ubuntu-12-10/#") for more info.

My laptop uses a 4250 and I choose to go back to 12.04.

Okay, I got it. But I get to know about this last night already, as I was so eager to find a fix for my problem. And as far as the version of the 'Xorg' is concerned; I've Xorg 1.12 because I use Ubuntu 12.04 ;) So, I gues there are chances that I'd be able to tweak the performance issues right? Direct/link me to those if you know any. :(

---

### Post by rex_dante on 2012-12-28
> **QIII said:**
> I recommend very VERY strongly AGAINST following any instructions to downgrade X Server.  How it will affect subsequent upgrades of Ubuntu versions cannot be determined.  You essentially break Quantal.


I ain't going to do that man.:lolflag:

> **QIII said:**
> It would be better to move forward with a 5 year LTS in Precise than a broken Quantal.

I totally agree with you.:p But I need to fix/tweak these ******* performance issues. :confused:](*,)

---

### Post by GreatDanton on 2012-12-28
I solved this problem by not installing any graphic drivers. I have Ati radeon HD4870 , and I found out that without drivers is working better than with.

---

### Post by ArminasAnarchy on 2012-12-28
> **rex_dante said:**
> Hello all!
I'm here because I'm having terrible time while installing drivers for my 'ATI HD 4250' GPU. I've tried the 'additional drivers' (both ones; post-released etc.) and only one have worked but the results are same; I got a hell lot of 'choppy performance'.](*,)
I've also tried installing via .run packges and broke them to .deb files. I also removed and re-installed the "fglrx" drivers via terminal but no luck. By the way, I managed to install the ATI Catalyst 12.10 drivers but they gave me a very terrible performance too. :\ Currently I've installed the ATI Legacy 12.6 drivers. It seems that the installation went successfully. I rebooted my pc too. I can access the 'configuration' window of the ATI i.e. 'amdcccle'. But It seems that the driver isn't even working. :'(

I don't know WHY, WHY I run into issues ONLY when it comes to install the drivers in UBUNTU while I'm practicing Pentesting on Ubuntu. :\

I've attached the copy of my 'Xorg.0.log' to the thread. Check that for assistance and PLEASE...DO respond sooner. I hope I'll get it fixed ASAP as I'm on the best Linux forum ever. :D
Thanks in advanced.:)

I see that a few users have already pointed out that AMD have dropped support for this in 12.10. What I'd recommend is dropping back to 12.04, it's a LTS, so you've got support and use for the next few years, and although you lose the latest and greatest, at least you can install the ATI drivers. I've done this for my cousin's PC (which I've been responsible for building/maintaining), and I managed to get Steam installed. I've not had the time to test it yet, but at least all the bits were working.

Why AMD don't hand the driver over to the community to update and maintain is beyond me. There's a problem upstream, and consequently all of the users down stream are stuffed. Maybe someone could work on a ndiswrapper style work around, but I spent hours trying to get this working to no avail.

---

### Post by verymadpip on 2012-12-28
I've never had a problem with the open source drivers with my HD4870, however, I wanted to participate in the Steam Beta, which is when things got messy.  It would appear that my easiest solution is a new GPU, which I can't justify :)

---

### Post by rex_dante on 2012-12-29
> **ArminasAnarchy said:**
> I see that a few users have already pointed out that AMD have dropped support for this in 12.10. What I'd recommend is dropping back to 12.04, it's a LTS, so you've got support and use for the next few years, and although you lose the latest and greatest, at least you can install the ATI drivers. I've done this for my cousin's PC (which I've been responsible for building/maintaining), and I managed to get Steam installed. I've not had the time to test it yet, but at least all the bits were working.

Why AMD don't hand the driver over to the community to update and maintain is beyond me. There's a problem upstream, and consequently all of the users down stream are stuffed. Maybe someone could work on a ndiswrapper style work around, but I spent hours trying to get this working to no avail.

I AM ON THE "12.04" version ALREADY man and I didn't even upgraded to 12.10 in the past. And I HAVE the drivers installed but having LAG issues everywhere even browsing through my files and ALT+TABing windows. THAT'S the main problem. "I WANT TO RUN UBUNTU JUST LIKE WATER i.e. SMOOTH". :'(

---

### Post by verymadpip on 2012-12-29
What's the problem with the open source drivers if I may ask?

i. e.  Why do you feel you need the AMD proprietary driver?

---

### Post by rex_dante on 2013-01-01
> **verymadpip said:**
> What's the problem with the open source drivers if I may ask?

i. e.  Why do you feel you need the AMD proprietary driver?

**I AM HAVING PERFORMANCE ISSUES.**
No AMD proprietary driver NOR open-source drivers are giving me performance as anyone would expect. Ubuntu LAGS like HELL whenever I install ANY of above drivers (or maybe there's something to tweak that I don't know so point me out on that).:confused::frown:](*,)

---

### Post by verymadpip on 2013-01-01
> **rex_dante said:**
> **I AM HAVING PERFORMANCE ISSUES.**
No AMD proprietary driver NOR open-source drivers are giving me performance as anyone would expect. Ubuntu LAGS like HELL whenever I install ANY of above drivers (or maybe there's something to tweak that I don't know so point me out on that).:confused::frown:](*,)

You shouldn't need to manually install the open source driver following an installation.
If you're doing that something is way off IMO.

I suggest a clean installation of 12.04.1, update it, leave the drivers alone, & see how that is.

As I've had no problems I can't advise you on what to "tweak", sorry bud.

---

### Post by ArminasAnarchy on 2013-01-07
> **verymadpip said:**
> You shouldn't need to manually install the open source driver following an installation.
If you're doing that something is way off IMO.

I suggest a clean installation of 12.04.1, update it, leave the drivers alone, & see how that is.

As I've had no problems I can't advise you on what to "tweak", sorry bud.

I just wanted to second this. If things are still laggy, or if you're planning on installing the steam beta, then try following this guide: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Don't bother using the GUI, jump straight to the command line method. Make sure you enable hardware acceleration too, I don't know the technicalities about what exactly the difference is, but it can't hurt, right?

If after all this you're still having issues, maybe try switching to Kubuntu? Personally I hate Unity anyway, but if everything else is running without issue but you're still suffering, I guess that would suggest the OS is at fault, somehow. Maybe try one of the lightweight desktop environments too, something like Xfce/LXDE? Though you really shouldn't need to with that card.

---

### Post by rex_dante on 2013-01-17
Still waiting for a WORKING response from experienced users. :'(

---

### Post by ZombieApocalypse on 2013-01-17
I run a Compaq Presario laptop with the ATI 4250 on Kubuntu 12.04 using the Catalyst 12.6 legacy drivers and it runs smoothly. It also ran fine with the open source drivers, but I wanted to use some of the Catalyst features. I haven't tried Ubuntu. Perhaps you could try running Kubuntu from a live disk and see how it performs?

---

### Post by rex_dante on 2013-01-24
> **ZombieApocalypse said:**
> I run a Compaq Presario laptop with the ATI 4250 on Kubuntu 12.04 using the Catalyst 12.6 legacy drivers and it runs smoothly. It also ran fine with the open source drivers, but I wanted to use some of the Catalyst features. I haven't tried Ubuntu. Perhaps you could try running Kubuntu from a live disk and see how it performs?

See, Ubuntu runs SMOOTH when I "don't" use ANY drivers. Problem occurs when I install ANY drivers. And I'm just about to remove the drivers now AGAIN and won't install in anymore. I'm fed of this **** now! :\ :'((

---

### Post by ZombieApocalypse on 2013-01-24
AMD have now released 13.1 legacy drivers ([http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)). If you're feeling masochistic you could try these. 

But to be honest, if you want people to help you, I think you need to provide more information. Like the exact procedure you used to installed the drivers (ie commands you typed into the terminal, etc).

However, if your system is working fine on the open source drivers and your needs are adequately fulfilled, then perhaps you should just stick to these?

---

### Post by rex_dante on 2013-01-24
> **ZombieApocalypse said:**
> AMD have now released 13.1 legacy drivers ([http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)). If you're feeling masochistic you could try these. 

But to be honest, if you want people to help you, I think you need to provide more information. Like the exact procedure you used to installed the drivers (ie commands you typed into the terminal, etc).

However, if your system is working fine on the open source drivers and your needs are adequately fulfilled, then perhaps you should just stick to these?

Thanks for the reply man. :) I'll get to it when I get rid of ma unfinished business. And I'll let you know about the commands for sure. :)

I just want you to stick to this thread and assist me at least until I try this version of drivers. :P

Thanks again!

---

### Post by verymadpip on 2013-01-24
"> **rex_dante said:**
> See, Ubuntu runs SMOOTH when I "don't" use ANY drivers. Problem occurs when I install ANY drivers. And I'm just about to remove the drivers now AGAIN and won't install in anymore. I'm fed of this **** now! :\ :'((

If you aren't using ANY drivers then you would have NO VIDEO AT ALL.
Your notion of "no drivers" is what the rest of us refer to as the open source driver - which is installed by default.

We went over this days ago.

---

### Post by ZombieApocalypse on 2013-01-25
These are the exact steps I took to successfully install the Catalyst 13.1 legacy drivers on my laptop which uses an ATI mobility radeon 4250. This was done in Kubuntu 12.04 AMD64, but it should work exactly the same in Ubuntu. Note that these drivers will not work in 12.10 without downgrading xorg.

1. I downloaded the driver from the AMD site ([**_link here_**]("http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip")) to a folder I named AMD and unzipped the file.

2. I purged my system of previous fglrx installations:
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```

3. I made sure all required dependencies were installed:
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx

```
and
```
sudo apt-get install debhelper dkms libqtgui4 libstdc++6 libelfg0 unzip
```
and for 64-bit systems:
```
sudo apt-get install ia32-libs-multiarch i386 lib32gcc1 ia32-libs libc6-i386 ia32-libs
```

4. I installed the driver:
```
cd amd
sudo sh amd-driver-inst*.run --buildpkg `lsb_release -is`/`lsb_release -cs`
sudo dpkg -i *.deb 
sudo aticonfig --initial
```

5. Reboot the system

6. Test the driver installation
```
fglrxinfo
```
and then
```
 fgl_glxgears
```

Note that by default v-sync is enabled in the Catalyst Control Centre, so the fgl_glxgears test will not generate an fps above your refresh rate (in my case 60Hz). By disabling v-sync I get around 300fps.

Hope this is of use to you.

---

### Post by furything on 2013-01-25
I have an ati 4250 or should say did have.

All worked okay bar HD video playback which was choppy/tearing. It was using the cpu as well to do playback rather than pass through which caused the problem.

I replaced with cheap nVidia 210 around £20 and used the vpau mode for hd playback and problem solved on the mythbox.

Will be interested to see if 13.1 drivers fix this as the ati card is now in a different dual boot system that I want to play hd content from mythtv.

---

### Post by ZombieApocalypse on 2013-01-25
> **furything said:**
> I have an ati 4250 or should say did have.

All worked okay bar HD video playback which was choppy/tearing. It was using the cpu as well to do playback rather than pass through which caused the problem.

I replaced with cheap nVidia 210 around £20 and used the vpau mode for hd playback and problem solved on the mythbox.

Will be interested to see if 13.1 drivers fix this as the ati card is now in a different dual boot system that I want to play hd content from mythtv.

I actually haven't tried HD video playback on the new drivers (will try over the weekend) as I've only just installed them, but I had no problems with 12.6. My laptop is plugged into my HDTV and regularly used for watching HD content. Enabling tearfree (or whatever it's called) in the Catalyst Control Centre fixed any tearing and enabling video acceleration ensured smooth playback. This can be enabled by:

```
sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
```

and to test
```
sudo vainfo
```

I use VLC for video playback. In VLC, xvba can be enabled by checking the "Use GPU acceleration" box in the Inputs and Codecs section of the preferences. I think you need to restart VLC for it to take effect.

more info [**_here_**]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Enabling_Video_Hardware_Acceleration")

---

### Post by furything on 2013-01-25
Thanks ZombieAppocalypse
> I actually haven't tried HD video playback on the new drivers (will try  over the weekend) as I've only just installed them, but I had no  problems with 12.6. ....

May give this a try now. 
I am using mythfrontend as the playback tool so I can stream live hd tv content so I will give the new drivers ago.

---

### Post by Steve the Pocket on 2013-01-25
The driver setup program is telling me that fglrx was detected on my system. Do I need to reboot or something?

---

### Post by rex_dante on 2013-01-27
> **ZombieApocalypse said:**
> These are the exact steps I took to successfully install the Catalyst 13.1 legacy drivers on my laptop which uses an ATI mobility radeon 4250. This was done in Kubuntu 12.04 AMD64, but it should work exactly the same in Ubuntu. Note that these drivers will not work in 12.10 without downgrading xorg.

1. I downloaded the driver from the AMD site ([**_link here_**]("http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip")) to a folder I named AMD and unzipped the file.

2. I purged my system of previous fglrx installations:
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```3. I made sure all required dependencies were installed:
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx

```and
```
sudo apt-get install debhelper dkms libqtgui4 libstdc++6 libelfg0 unzip
```and for 64-bit systems:
```
sudo apt-get install ia32-libs-multiarch i386 lib32gcc1 ia32-libs libc6-i386 ia32-libs
```4. I installed the driver:
```
cd amd
sudo sh amd-driver-inst*.run --buildpkg `lsb_release -is`/`lsb_release -cs`
sudo dpkg -i *.deb 
sudo aticonfig --initial
```5. Reboot the system

6. Test the driver installation
```
fglrxinfo
```and then
```
 fgl_glxgears
```Note that by default v-sync is enabled in the Catalyst Control Centre, so the fgl_glxgears test will not generate an fps above your refresh rate (in my case 60Hz). By disabling v-sync I get around 300fps.

Hope this is of use to you.

Thanks for the reply man. I followed all your steps ONE-by-ONE and got it everything just fine. Drivers are installed (without ANY errors :3), configuration is good, glxgears giving nice fps etc.

But the main problem of mine persists. The ******* lagging issues with EVERYTHING including click-dragging lines. They even lags when I drag them to select files and folders. >:-\\

I think the problem could be with the MONITOR I got. I'm showcasing configuration of my system. Tell me if it's the RESOLUTION (1920 x 1080) that's making me mad because ON LOWER resolution (1024 x768), I get acceptable performance comparitively that I get on FULL HD resolution (1920 x 1080).

My systems' configuration:
CPU: AMD FX-4100 Quad-Core Bulldozer 3.6 Ghz
GPU: ATI Radeon HD 4250 512 MB
MOBO: Gigabyte GA-880GM-D2H
HDD: 1 TB Western Digit 7200 Rpm
FANS: Stock Cooler for CPU, One on the shutter of cabinet, one on the backside one of SMPS itself, 4 in total.
MONITOR: LG LS46 series (MEZ-62688468) FULL HD LED (1920 X 1080p)

Also, after installing the drivers, my CPU usage increases sharply (and keep on increasing gradually) nearly bottlenecking the ma CPU. :\

Now I feel like uninstall the drivers again. :'(
Please tell me that could the resolution itself be a problem?
And how the hell ma system can't get to run fine?
How to fix this frigging piece of issue I got?

---

### Post by ZombieApocalypse on 2013-01-27
Well it sounds like you've done everything correctly, so I'm unable to offer any further advice as to what could be the cause of your problem. Though I must admit that I have the mobility version of the card and I am running my laptop at 1366x768, which is the maximum resolution my system supports.

---

### Post by rex_dante on 2013-01-27
> **ZombieApocalypse said:**
> Well it sounds like you've done everything correctly, so I'm unable to offer any further advice as to what could be the cause of your problem. Though I must admit that I have the mobility version of the card and I am running my laptop at 1366x768, which is the maximum resolution my system supports.

So, does it mean I'm hopeless now? :'(
As no one else is replying to this thread but you and I appreciate that.
Also, this new version of drivers is more choppy than the previous ones. I also got a hang-up a few minutes ago that it forced me to reboot. :(

---

### Post by ZombieApocalypse on 2013-01-27
Sorry, wish I could be more help. It sounds like you'll need to revert back to the default/open-source drivers. AMD driver support is pretty poor in linux, to be honest. Although the arrival of Steam on linux might be the incentive that AMD need to get their act together. It might be worth investing in a cheap second-hand Nvidia card (eg 500 series) as the driver support is reportedly a lot better.

---

### Post by rex_dante on 2013-01-27
> **ZombieApocalypse said:**
> Sorry, wish I could be more help. It sounds like you'll need to revert back to the default/open-source drivers. AMD driver support is pretty poor in linux, to be honest. Although the arrival of Steam on linux might be the incentive that AMD need to get their act together. It might be worth investing in a cheap second-hand Nvidia card (eg 500 series) as the driver support is reportedly a lot better.
I can stick to the open source 2d drivers which are inherently present in Ubuntu. At least they don't lag. :(
I love AMD and ATI even that I'm encountering these issues. And I'm planning to get a ATI Radeon HD 6670 or a better GPU rather than a Nvidia GPU (I WAS a nvidia fan). 

Thanks for your support though. :)

---

### Post by furything on 2013-01-28
You may find a new ATI is better
I have a ATI5770 on an iCore 5 with 8gb and it runs like a dream (I am sure the power horse CPU helps a lot). 
Like you it was my ATI4250 I was having issues with. Have not got round to doing my spare PC after reading/commenting on this thread with the ATI4250. If I get chance this week will let you know encase I come up with similar problems and can fix it.
Not sure why your resistance to nVidia as my slower PCs Pentium 4 run with 210 nVidia cards no issues at all - admittedly these are mythtv boxes used for HD vidoe streaming/playback

---

### Post by rex_dante on 2013-01-28
> **furything said:**
> You may find a new ATI is better
I have a ATI5770 on an iCore 5 with 8gb and it runs like a dream (I am sure the power horse CPU helps a lot). 
Like you it was my ATI4250 I was having issues with. Have not got round to doing my spare PC after reading/commenting on this thread with the ATI4250. If I get chance this week will let you know encase I come up with similar problems and can fix it.
Not sure why your resistance to nVidia as my slower PCs Pentium 4 run with 210 nVidia cards no issues at all - admittedly these are mythtv boxes used for HD vidoe streaming/playback

Okay. I'll stick to this thread for some more time too as I need to get it fixed badly. Currently, I've removed the drivers which I download/installed and using only 2d drivers. They run like a charm but NO 3d support. :(

---

### Post by furything on 2013-02-05
Hi Rex_Dante
Finally got round to upgrading my spare system to 12.04. This is the system with the ATI 4250 like yours. Not getting much time but will hopefully test it out later this week.

I will be starting with the video tearing issue I had then start looking at the overall performance. I always run KDE but what desktop environment are you running? Is it actually unity on ubuntu or are you running something else?

I will start testing on KDE but will run the same environment as yours if you confirm what you are running.

---

### Post by rex_dante on 2013-02-21
> **furything said:**
> Hi Rex_Dante
Finally got round to upgrading my spare system to 12.04. This is the system with the ATI 4250 like yours. Not getting much time but will hopefully test it out later this week.

I will be starting with the video tearing issue I had then start looking at the overall performance. I always run KDE but what desktop environment are you running? Is it actually unity on ubuntu or are you running something else?

I will start testing on KDE but will run the same environment as yours if you confirm what you are running.

I'm running Unity of course; Gnome.

---

### Post by Asatru9 on 2013-02-21
I've followed this thread and I was wondering how much RAM do you have in your PC?  I missed any listed amount.  Do you have the maximum possible amount of RAM installed and all the 12.04 updates?

EDIT:  Have you thought about NOT using Unity and using the gnome classic desktop instead?  I used Unity to become familiar with it myself and I found I needed to go back to the gnome classic desktop so it wasn't as slow.

---

### Post by MadmanRB on 2013-02-21
Funny as I am running the exact same card and things are fine on my end.
Maybe you coulkd try something that is not graphics intensive, maybe XFCE is in your future.

---

### Post by furything on 2013-08-19
Hi Rex_dante
Sorry for such a delay. Work has been manic and have not had much time to do anything at home. As I originally stated I was using KDE so had to install unity and compiz to get 3d. I suspect you have either changed card by now or got it sorted.

For anyone else trying this all seems ok. I am running an AMD 3000+ with 2gb. 64bit version of 12.04 and on the latest kernel as at 17/08/2013.

3d effects with the ATI4250 seem absolutely fine without any tinkering. There are warnings when activating the 3d desktop but the cube desktop change and wavering windows seem to render fluidly. I could not see a fault anywhere.

Good luck to anyone else.

---

