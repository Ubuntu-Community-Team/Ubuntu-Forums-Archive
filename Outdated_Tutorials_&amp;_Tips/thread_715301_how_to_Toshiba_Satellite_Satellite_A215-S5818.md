---
title: "how to: Toshiba Satellite Satellite A215-S5818"
date: 2008-03-04
forum: Outdated Tutorials &amp; Tips
---

### Post by fissionmailed on 2008-03-04
This is for 7.10.

If I don't reply in 24ish hours PM me to let me know. I forget to check my subscribed threads some times. 

This is a how to to get the sound, wireless working and video card drivers.  The wireless was a huge problem for me and it took me a month to get it to work right.  Most of this is just reposts, but this way, there's one thread plus the wireless was especially hard so.  I did this on a 64 bit install of Ubuntu.

First off is the sound.
I used this [thread]("http://ubuntuforums.org/showthread.php?t=568463") if you want to see the original thread. 

You'll need these to compile the Alsa files.
```
sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install libncurses5-dev
sudo apt-get install build-essential gettext ja-trans
```Note: I didn't always install the last one but it never hurts to play it safe I suppose.

Next is to install the headers.
```
sudo apt-get  install linux-headers-`uname -r`
```You can download the latest Alsa drivers and all [here]("http://www.alsa-project.org/main/index.php/Download").  I just downloaded the driver, lib, utils and firm files.  Assuming you are in the directory with the files(firefox's default is the desktop).

To move the files
```
sudo mkdir -p /usr/src/alsa
sudo cp alsa-driver* /usr/src/alsa
sudo cp alsa-lib* /usr/src/alsa
sudo cp alsa-firm* /usr/src/alsa
sudo cp alsa-util* /usr/src/alsa

```To go to the files in /usr/src/alsa
```
cd /usr/src/alsa 
```
To untar them
```
sudo tar xjf alsa-driver*
sudo tar xjf alsa-lib*
sudo tar xjf alsa-firmware*
sudo tar xjf alsa-utils*
```Now to compile them.
```
cd alsa-driver*
sudo ./configure 
sudo make 
sudo make install
cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install
cd ../alsa-firm*
sudo ./configure
sudo make
sudo make install
cd ../alsa-util*
sudo ./configure
sudo make
sudo make install 
```Assuming all of the same model laptops are the same.
```
gksu gedit /etc/modprobe.d/alsa-base
```and add to the bottom of the file
```
options snd-hda-intel model=toshiba
```If not, or you really wanna play it safe, this [thread]("http://ubuntuforums.org/showthread.php?t=568463") can tell you how.

Reboot and you should have sound.  

------------------------------------------

For for the fun part, wireless.

**UPDATE!!!!!!!!!**  There's a new HAL that supports the card.  I downloaded the madwifi with the new HAL and installed it and it worked. I grabbed madwifi-hal-0.10.5.6-r3861-20080903 and it worked.  Of course I'm sure there's a newer one out now.  You just have to installed it which you can find out how to do that online. The madwifi site and the read me inside the download.


If you have a 32 bit install, scroll down to the bottom of the wireless section and read what DUfire posted first and then decide what you want to do.

First you want to go to the restricted drivers and disable the HAL, it will want to reboot but hold it's horses for now.  You can go ahead and enable the video driver too now if you want too.  This [thread]("http://ubuntuforums.org/showthread.php?t=574501") is the one I used the most, but I also used others.

```
 gksu gedit /etc/modprobe.d/blacklist 
```and add this 
```
blacklist ath_pci
blacklist ath_hal
```reboot

You need ndiswrapper version 1.44 or 1.45rc1, I used 1.45rc1 and it works great so, but I heard either one can be used from [here]("http://ndiswrapper.sourceforge.net/joomla/index.php?option=com_fireboard&Itemid=34&func=view&id=906&catid=2#906").
You can download them [here]("http://sourceforge.net/project/showfiles.php?group_id=93482"), you just have to click on the "view older releases.." link.
**EDIT:  I have installed 1.53 and it works fine and without a problem. I'm not sure if it was the software before or me, but now the latest ndiswrapper seems to work. **



To download the driver you need, go [here]("http://www.atheros.cz").  Note: you want the 5007EG, if you have a 64-bit version of Ubuntu etc you want the 64-bit XP driver, if you have a  32-bit version of Ubuntu, you want the 32-bit version of the XP driver.

Once you have ndiswrapper and assuming you're in the directory.

```
tar -zxvf ndiswrapper-* 
sudo remove
sudo make
sudo make install
```You want to make sure to do the remove step until you don't remove anything.

Once you do this, you want to unzip the zip file the driver is in, I did this is the GUI.  You want to make sure the .sys file and the .inf file are in there.
Assuming you're in the file you extracted
```
sudo ndiswrapper -i ____.inf
ndiswrapper -l
```It should say the driver is installed, something like this:
```
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
```NOTE: if you use a 32 bit driver(because you use a 32 bit version of Ubuntu) the driver name won't be the same but the driver installed part should be there.
If not, you may have gotten the wrong driver or something else might have gone wrong.   

Once you have finished this, ndiswrapper wrap should be installed but there still needs to be some tweaking done. 

Here, on the bottom of the laptop there is a sticker with the wireless LAN (reminiscent of Metal Gear Solid eh?).  You'll need that MAC address. 

Note: your wireless device might be called something else rather than wlan0, you'll need that need, mine was wlan0 so I'm using it as an example.  You can check this by iwconfig, it should be something like wlan(n) where (n) is a number.

```
gksu gedit /etc/network/interfaces 
```Here you will need to add  something like:
```
 ifconfig wlan0 hw ether 00:1b:9e:85:6a:38 
```Where my MAC address (aka the wireless LAN on the back of the laptop) is 00:1b:9e:85:6a:38 and my wlan0 section of the file looks like:

```
 auto wlan0
ifconfig wlan0 hw ether 00:1b:9e:85:6a:38
iface wlan0 inet dhcp 
```I also did this
```
 gksu gedit /etc/modules 
```and added 
```
ndiswrapper
```to the bottom of it.

Now reboot.

Network manager does not show any wireless networks.   I have not tried WICD but I've heard people have had success with it where network manager fails.

To set up a connect without Network Manager, I followed kevdogs thread [here]("http://ubuntuforums.org/showthread.php?t=684495").

installing wpa_supplicant and all it rather easy.  

This is what DUfire did and it worked for him on a install of a 32 bit version of Ubuntu.  I did mine on a 64 bit, so if you have a 32 bit install you might want to try his.

> **DUfire said:**
> Great guide on getting that dreaded ALSA to work for me! This is my second day using 32-bit Gutsy and there seems to be many conflicting tutorials on getting my Intel HDA card to work properly. 

As for the wireless, starting from a clean install yesterday, I only took about one-third of those steps to get mine fully-functional.
Basically, just make sure you have ndiswrapper-common and other installed [not on my laptop now], extract the .inf and .sys files into your /home directory, and...

```

sudo ndiswrapper -i ___.inf

``` 

...should prove to install the drivers correctly. A quick sudo ndiswrapper -l will show if the driver installed correctly or not. 

After it shows to be installed correctly, you need to add it to the kernel module [I guess this is what that does]. To do that, in your terminal type...

```
sudo ndiswrapper -ma && sudo ndiswrapper -mi
```


Also, you need to configure it at every boot so you don't have to reconfigure this everytime you reboot [which is probably a lot if you're still in the stage of configuring drivers/hardware]. To do that, type this in your terminal...

```

sudo gedit /etc/modules

```

...and add ndiswrapper to the end of the list.
Save it, re-install, and it should be working for you.
Then again, this was a clean install and I'm not too familiar with the complete workings of Ubuntu quite yet so I'm not sure how this would respond on other's machines.

EDIT:  I installed WICD from the instructions here:
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) and it works.  It's a nice GUI if you ask me but I still just do it all in the command line so. 


-----------------------

The easy part for last. ;)

To get the video card driver just go to the restricted drivers part and enable it.
**EDIT:  IMO Envy is a breeze to get the drivers working and works great. [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) Personally I think this is the best way but it's just me. You simply download the deb and install it so. **
Reboot.

IIRC all I had to do was install it from the restricted drivers and install it, but mine was on a 64-bit and was a couple of months ago so.  If you're having problems with the video driver this is what DUfire said.

> **DUfire said:**
> 
EDIT: Also, from my experience with this computer, the ATI proprietary driver won't just work by enabling it from the restricted drivers menu. You might get and zorg error. You actually might have to get your wireless working then install some updates. Quite a simple fix, actually.

In your terminal, type...
```

sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager

```

Once that is finished, you need to tell your system that the main video driver is the fglrx driver [rather than the default, or vesa]. To do that, go to...
```

sudo gedit /etc/X11/xorg.conf 

``` 

...and go to the "Device" section and change "vesa" to "fglrx".
Save, close, reboot, and it should work for you, assuming just enabling it from the restricted drivers manager didn't work and you are indeed using an ATI Radeon X1200 video card.


--------------------------------


I might have made a mistake in there some where due to having done most of this stuff a month ago, but if you have any problems, just let me know and I'll update this. Plus most of this was done at 3 am at night after a day of class so I'm not saying it's perfect.  This is just what got it to work for me. Also, most of ,the links I put there are to the threads that helped me,  if my write up is not clear enough let me know and also until I post or reply to a PM look in those threads I linked, there's a whole host of information on the Ubuntu forums and the wiki.  Some times it's easy to find and some times not though.  Again, if you have questions, you can PM me.

---

### Post by LuisGMarine on 2008-03-04
I just want to say thanks, reading your guide helped me fix my system completely.  The only thing wrong with my toshiba laptop was the sound, I already compiled my own alsa drivers and all that stuff, but adding the model=toshiba is what did the trick.

I must of overlooked it, but when I say it here and gave it a try, it fixed everything!  Now I have FULL sound, before I was getting this low crappy sound, and now its actually loud as hell I even woke my room mate up!

The only thing I have to do now , is check the microphone, which I'll do tomorrow.

But thanks for this guide, I've been waiting on something like this to happen.  Mad kudos man, seriously.  :guitar:

---

### Post by Glaxed on 2008-03-04
I loves this. :D, thx.
I've only tried Gutsy live on this laptop but im gonna fix that Saturday.

---

### Post by fissionmailed on 2008-03-05
To: LuisGMarine
No worries man, mostly this is just stuff I've found on the board.

To: Glaxed
While this is what done it to work for mine, some times things vary or just my instructions reek. :lolflag:   


Once I get back to my dorm, I'm going to experment with the video drivers to try to find how to get those to work with another monitor.  Once I figure that out, I'll edit that information in.  
If anything one has info at needs to be put in here for this, just let me know.

---

### Post by LuisGMarine on 2008-03-05
I was wondering if we can try to figure out the web cam situation?

I Don't know about your laptop, but mine has a built in 1.3 mega pixel camera installed on the screen.  I tried EasyCam, but I keep on getting errors that it's not supported.  But I"m not even sure how to check what model the card is etc, I'm not sure of what commands to be running.

BTW has anyone tried playin an HD movie?  Mine has an HD drive, but I was wondering if any application in linux can play the HD format.  That's another thing to try.

Now that I'm starting college I need to find out if this computer is good with baterry life, hopefully it can last from 5:30 PM to about 10:00 PM, that's when my classes go.  I don't knwo if I need to set up extra things to be able to get that much power out of the battery.

---

### Post by fissionmailed on 2008-03-05
> **LuisGMarine said:**
> I was wondering if we can try to figure out the web cam situation?

I Don't know about your laptop, but mine has a built in 1.3 mega pixel camera installed on the screen.  I tried EasyCam, but I keep on getting errors that it's not supported.  But I"m not even sure how to check what model the card is etc, I'm not sure of what commands to be running.

BTW has anyone tried playin an HD movie?  Mine has an HD drive, but I was wondering if any application in linux can play the HD format.  That's another thing to try.

Now that I'm starting college I need to find out if this computer is good with baterry life, hopefully it can last from 5:30 PM to about 10:00 PM, that's when my classes go.  I don't knwo if I need to set up extra things to be able to get that much power out of the battery.

lsusb might offer some info but I'm not sure, mine doesn't have one. 

But what I can offer you is this
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Enable_laptop_mode_on_battery_power](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Enable_laptop_mode_on_battery_power)

THat might help with the battery,  I need to configure mine that way. 

And this
[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)
for the HD dvd.

Sorry I couldn't help more but I'm not too knowable on this things.  All I can do is just point you in the right direction.

---

### Post by LuisGMarine on 2008-03-07
Thanks for the directions.

I'm curious if you got your microphone to work?  I tried my microphone today and it was a no go.  Maybe I should use the stable version of alsa, and not the darn rc ones, but I don't see why it should make that big of a difference.

---

### Post by fissionmailed on 2008-03-08
> **LuisGMarine said:**
> Thanks for the directions.

I'm curious if you got your microphone to work?  I tried my microphone today and it was a no go.  Maybe I should use the stable version of alsa, and not the darn rc ones, but I don't see why it should make that big of a difference.

Yup, I just tested it.  It works with the computer speakers and with audacity.

---

### Post by LuisGMarine on 2008-03-08
going to compile the stable release of alsa.  Then test the microphone, as for the HD movie thanks they worked like a charm.  

I'm curious did I already ask you about the webcam?

Thanks again I'll post with my results later.

---

### Post by Ebbonified on 2008-03-08
Followed your directions... with minor corrections when warranted (like when your directions showed to compile firmware twice...)

And after two very careful tries.. including a reformat with clean install & update of 7.10, a no-go.

GUI puts two error msgs... one says :


No volume control GStreamer plugins and/or devices found.


Other one says:


The volume control did not find any elements and/or devices to control.  This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.      You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.




Hmmmmmm... any ideas?   

I have a Toshiba Satellite A215-S5818.. so we're at the very same specs.. :confused:

---

### Post by Ebbonified on 2008-03-09
Sound problem solved with this thread [http://ubuntuforums.org/showthread.php?p=4482974#post4482974]("http://ubuntuforums.org/showthread.php?p=4482974#post4482974")

As for the wireless issue, the terminal commands seemed to work, but I still have the problem of connecting on startup.  When I created the cp.local script, the machine would hang (before it even echoed the kernel activity)... I attribute this problem to the fact that there is a hardware switch (toggle) on the laptop for wireless network.  When it's toggled ON during startup, the machine hangs.

When the wireless toggle switch is OFF during startup, it loads normally.  So, for the moment, I have to toggle it OFF after shutdown and then toggle it ON after startup.

As for the UI (Ubuntu 7.10), I can manually connect to my WPA1 manually. If I set it  for "roaming" from the Administration >> Network menu, it doesn't seem to play nice.. and poops the stored key settings.  
But if I select it from the hotbar (in the upper right) it detects local wireless networks, and I enter the shared key, it remembers *that* just fine.. .so that's what I'm doing right now.

Hope that helps, and thanks for your help.

---

### Post by fissionmailed on 2008-03-09
> **Ebbonified said:**
> Sound problem solved with this thread [http://ubuntuforums.org/showthread.php?p=4482974#post4482974]("http://ubuntuforums.org/showthread.php?p=4482974#post4482974")

As for the wireless issue, the terminal commands seemed to work, but I still have the problem of connecting on startup.  When I created the cp.local script, the machine would hang (before it even echoed the kernel activity)... I attribute this problem to the fact that there is a hardware switch (toggle) on the laptop for wireless network.  When it's toggled ON during startup, the machine hangs.

When the wireless toggle switch is OFF during startup, it loads normally.  So, for the moment, I have to toggle it OFF after shutdown and then toggle it ON after startup.

As for the UI (Ubuntu 7.10), I can manually connect to my WPA1 manually. If I set it  for "roaming" from the Administration >> Network menu, it doesn't seem to play nice.. and poops the stored key settings.  
But if I select it from the hotbar (in the upper right) it detects local wireless networks, and I enter the shared key, it remembers *that* just fine.. .so that's what I'm doing right now.

Hope that helps, and thanks for your help.


Sorry about teh sound issue, I put the firmware twice and left out the util which I installed,  it's would because those always worked for me.  Then again I talked to some one else who got the wireless to work another way that I tried and couldn't get it to work.   

Yeah, I just do it in the terminal so.  I might have to look into that, hhmm. Thanks for the info man. :)

---

### Post by Folk Theory on 2008-04-01
hey thanks a lot for this!

i finally got the audio working but...
the wireless still isn't!

i did everything until the end, rebooted and then followed the commands posted on the link you gave at the very end and they all say no such device (for wlan0) so what am i missing?

the drivers seems to be correct and all...

netathr : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

---

### Post by Folk Theory on 2008-04-01
OK the back of my computer has two MAC-looking numbers..

one says MAC LAN followed by a number
the other one says wireless LAN followed by a different number.
theyre both equal length.

which one is the one i need for /etc/network/interfaces??
i tried both but neither worked!!

help much appreciated,

FT

---

### Post by fissionmailed on 2008-04-01
> **Folk Theory said:**
> OK the back of my computer has two MAC-looking numbers..

one says MAC LAN followed by a number
the other one says wireless LAN followed by a different number.
theyre both equal length.

which one is the one i need for /etc/network/interfaces??
i tried both but neither worked!!

help much appreciated,

FT

It should be the wireless MAC address.

---

### Post by Folk Theory on 2008-04-01
thanks! i wasnt sure because it says wireless LAN instead of MAC....
i'll try again

---

### Post by fissionmailed on 2008-04-01
> **Folk Theory said:**
> thanks! i wasnt sure because it says wireless LAN instead of MAC....
i'll try again

Thanks for asking, I needed to clarify that.  If you can't get the wireless to work, I was chatting on IM to someone who said that my steps wouldn't work on his.  Now they've worked on mine so it seems that there is some hhmm "flexibility" in the wireless cards.  Any who, he used [this]("http://ubuntuforums.org/showthread.php?t=512828") thread.  It might work for you.  I know I tried that one and it didn't work for me, but maybe I drank too much coffee that day. :)


Edit: If I don't reply, just send me an PM to let me know. Some times I forget to look at my subscribed threads.

---

### Post by Folk Theory on 2008-04-02
aha!

```
lspci
0e:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
```

note the six instead of 500**7** I'll try with that driver instead

---

### Post by Folk Theory on 2008-04-02
ok it's finally working.
try using lshw -C network like kevdog wrote. mine was using wlan1 instead of wlan0 for some reason and thats what caused all the trouble....

Thanks everyone for your help!

---

### Post by DUfire on 2008-04-02
Great guide on getting that dreaded ALSA to work for me! This is my second day using 32-bit Gutsy and there seems to be many conflicting tutorials on getting my Intel HDA card to work properly. 

As for the wireless, starting from a clean install yesterday, I only took about one-third of those steps to get mine fully-functional.
Basically, just make sure you have ndiswrapper-common and other installed [not on my laptop now], extract the .inf and .sys files into your /home directory, and...

```

sudo ndiswrapper -i ___.inf

``` 

...should prove to install the drivers correctly. A quick sudo ndiswrapper -l will show if the driver installed correctly or not. 
After it shows to be installed correctly, go to...

```

sudo gedit /etc/modules

```

...and add ndiswrapper to the end of the list.
Save it, re-install, and it should be working for you.
Then again, this was a clean install and I'm not too familiar with the complete workings of Ubuntu quite yet so I'm not sure how this would respond on other's machines.

---

### Post by fissionmailed on 2008-04-02
> **Folk Theory said:**
> ok it's finally working.
try using lshw -C network like kevdog wrote. mine was using wlan1 instead of wlan0 for some reason and thats what caused all the trouble....

Thanks everyone for your help!

aaaahhhh, yeah that might be a problem. 

Mine says it's a AR5006EG too though, for some reason it reads it wrong, but IIRC the drivers still work.   I'm glad you got it to work. :) I know after two months of banging my head against the wall I was ecstatic.

---

### Post by fissionmailed on 2008-04-02
> **DUfire said:**
> Great guide on getting that dreaded ALSA to work for me! This is my second day using 32-bit Gutsy and there seems to be many conflicting tutorials on getting my Intel HDA card to work properly. 

As for the wireless, starting from a clean install yesterday, I only took about one-third of those steps to get mine fully-functional.
Basically, just make sure you have ndiswrapper-common and other installed [not on my laptop now], extract the .inf and .sys files into your /home directory, and...

```

sudo ndiswrapper -i ___.inf

``` 

...should prove to install the drivers correctly. A quick sudo ndiswrapper -l will show if the driver installed correctly or not. 
After it shows to be installed correctly, go to...

```

sudo gedit /etc/modules

```

...and add ndiswrapper to the end of the list.
Save it, re-install, and it should be working for you.
Then again, this was a clean install and I'm not too familiar with the complete workings of Ubuntu quite yet so I'm not sure how this would respond on other's machines.

Yeah, I did mine on a 64 bit install so it might be differently.  Although the more and more I read it seems different for every one, which is weird, but as long as it works, it works.

---

### Post by DUfire on 2008-04-03
> **DUfire said:**
> Great guide on getting that dreaded ALSA to work for me! This is my second day using 32-bit Gutsy and there seems to be many conflicting tutorials on getting my Intel HDA card to work properly. 

As for the wireless, starting from a clean install yesterday, I only took about one-third of those steps to get mine fully-functional.
Basically, just make sure you have ndiswrapper-common and other installed [not on my laptop now], extract the .inf and .sys files into your /home directory, and...

```

sudo ndiswrapper -i ___.inf

``` 

...should prove to install the drivers correctly. A quick sudo ndiswrapper -l will show if the driver installed correctly or not. 

[B]After it shows to be installed correctly, you need to add it to the kernel module [I guess this is what that does]. To do that, in your terminal type...

```

sudo ndiswrapper -ma && sudo ndiswrapper -mi

```[/B]

Also, you need to configure it at every boot so you don't have to reconfigure this everytime you reboot [which is probably a lot if you're still in the stage of configuring drivers/hardware]. To do that, type this in your terminal...

```

sudo gedit /etc/modules

```

...and add ndiswrapper to the end of the list.
Save it, re-install, and it should be working for you.
Then again, this was a clean install and I'm not too familiar with the complete workings of Ubuntu quite yet so I'm not sure how this would respond on other's machines.

I added a fix, Fission, it's in bold.
Thanks :P.

EDIT: Also, from my experience with this computer, the ATI proprietary driver won't just work by enabling it from the restricted drivers menu. You might get and zorg error. You actually might have to get your wireless working then install some updates. Quite a simple fix, actually.

In your terminal, type...
```

sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager

```

Once that is finished, you need to tell your system that the main video driver is the fglrx driver [rather than the default, or vesa]. To do that, go to...
```

sudo gedit /etc/X11/xorg.conf 

``` 

...and go to the "Device" section and change "vesa" to "fglrx".
Save, close, reboot, and it should work for you, assuming just enabling it from the restricted drivers manager didn't work and you are indeed using an ATI Radeon X1200 video card.

I think that's all. I'm going to go celebrate my 16th birthday downstairs in the campus lobby now. Cheers!

---

### Post by fissionmailed on 2008-04-03
> **DUfire said:**
> I added a fix, Fission, it's in bold.
Thanks :P.

EDIT: Also, from my experience with this computer, the ATI proprietary driver won't just work by enabling it from the restricted drivers menu. You might get and zorg error. You actually might have to get your wireless working then install some updates. Quite a simple fix, actually.

In your terminal, type...
```

sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager

```

Once that is finished, you need to tell your system that the main video driver is the fglrx driver [rather than the default, or vesa]. To do that, go to...
```

sudo gedit /etc/X11/xorg.conf 

``` 

...and go to the "Device" section and change "vesa" to "fglrx".
Save, close, reboot, and it should work for you, assuming just enabling it from the restricted drivers manager didn't work and you are indeed using an ATI Radeon X1200 video card.

I think that's all. I'm going to go celebrate my 16th birthday downstairs in the campus lobby now. Cheers!

I know I could get the ethernet to work right off the bat so I didn't have to wait to get the wireless working.  The funny thing is that I don't remember having to do all that with the video drivers. Who knows though, I'll have that to the video card section though, can't hurt to have that in there if people are having trouble. 

And happy birthday man!  Treasure those years, they go by fast. ;_;

---

### Post by DUfire on 2008-04-03
> **fissionmailed said:**
> I know I could get the ethernet to work right off the bat so I didn't have to wait to get the wireless working.  The funny thing is that I don't remember having to do all that with the video drivers. Who knows though, I'll have that to the video card section though, can't hurt to have that in there if people are having trouble. 

And happy birthday man!  Treasure those years, they go by fast. ;_;

I'm afraid of that last part, too.
Aha, maybe I'm letting them waste away here? Well, at least I'm doing something I enjoy.

Sorry for including all that extra information! Just playing it safe for other people in the case they come across the same problems I had.

---

### Post by Folk Theory on 2008-04-04
no i enabled mine using the restricted drivers manager. 
ok. seems like we all got internet working, we can now turn to Compiz...
so i tried enabling it and i got something like "the composite extension isn't available" so i went to xorg.conf and changed it from "0" to "1" (on section extensions) now i get 

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

so I'm afraid installing xgl will mess up other things....will it?

---

### Post by radtek on 2008-04-05
Thanks guys!

A few comments: I bought this particular model laptop about 4 weeks ago... No sound... Then that day I found the beginnings of this thread. Voila! Sound worked in 7.10 32bit.

Then I ordered a new 7200rpm HD and 4gb RAM which I placed in yesterday. 

Anticipating this clean install, I had upgraded the BIOS v1.30 to v1.70 the night before. Everything worked fine. Still had sound and wireless.

I did a clean install on the new HD and wireless worked, but no sound! Nothing I could do would get the sound to work! Repeated tries to no avail.

I found an .iso of the v1.30 and reflashed the BIOS. Fresh install 7.10 32bit and then the method in the start of this thread... reboot and nice drums, chanting etc... WTF?

My advice to ya'll is not to upgrade the BIOS to v1.70 at this point. Mainly it solves Vista problems anyway.

Also, I tried the 7.10 64bit. Like in 32bit win98 .inf, I added the line in the x64 net8187b.inf to read like this:

```
;;****************************************************************************

;; IDs for X64

;;****************************************************************************

[Realtek.NTamd64]

%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200
[COLOR="Red"]%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200[/COLOR]
```

Using the graphical installer I was able to install the driver as I had in 32bit. Sees the hardware. Sees all the available wireless networks including my own. Even so, I couldn't connect even in open wireless mode.

Iwconfig returns that my access point doesn't/hasn't registered a MAC Address or an "ESSID" All attempts to force it to do so failed.

I was so frustrated I didn't even try the sound. After 12 hours, I got the 32bit working right away after the BIOS correction.

I really want to try the 64 bit! I was so close! Any ideas about this whole mess?

---

### Post by fissionmailed on 2008-04-06
> **Folk Theory said:**
> no i enabled mine using the restricted drivers manager. 
ok. seems like we all got internet working, we can now turn to Compiz...
so i tried enabling it and i got something like "the composite extension isn't available" so i went to xorg.conf and changed it from "0" to "1" (on section extensions) now i get 

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

so I'm afraid installing xgl will mess up other things....will it?

I dunno, I haven't tried too much with the video drivers.  

I tried something like this [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects)

But couldn't get it to work for some reason.  Of course I dislike desktop effects so I'm not the most motivated person to get it to work.

> **radtek said:**
> Thanks guys!

A few comments: I bought this particular model laptop about 4 weeks ago... No sound... Then that day I found the beginnings of this thread. Voila! Sound worked in 7.10 32bit.

Then I ordered a new 7200rpm HD and 4gb RAM which I placed in yesterday. 

Anticipating this clean install, I had upgraded the BIOS v1.30 to v1.70 the night before. Everything worked fine. Still had sound and wireless.

I did a clean install on the new HD and wireless worked, but no sound! Nothing I could do would get the sound to work! Repeated tries to no avail.

I found an .iso of the v1.30 and reflashed the BIOS. Fresh install 7.10 32bit and then the method in the start of this thread... reboot and nice drums, chanting etc... WTF?

My advice to ya'll is not to upgrade the BIOS to v1.70 at this point. Mainly it solves Vista problems anyway.

Also, I tried the 7.10 64bit. Like in 32bit win98 .inf, I added the line in the x64 net8187b.inf to read like this:

```
;;****************************************************************************

;; IDs for X64

;;****************************************************************************

[Realtek.NTamd64]

%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200
[COLOR="Red"]%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200[/COLOR]
```

Using the graphical installer I was able to install the driver as I had in 32bit. Sees the hardware. Sees all the available wireless networks including my own. Even so, I couldn't connect even in open wireless mode.

Iwconfig returns that my access point doesn't/hasn't registered a MAC Address or an "ESSID" All attempts to force it to do so failed.

I was so frustrated I didn't even try the sound. After 12 hours, I got the 32bit working right away after the BIOS correction.

I really want to try the 64 bit! I was so close! Any ideas about this whole mess?

Well I have a 64 bit install, and I had a fit getting everything to work, but I did although it took some time. What worked for me I posted here, but it seems like every one has a different story when it comes to getting things to work which is weird to say the least.

---

### Post by radtek on 2008-04-06
I've lost my sound. Again. Happened after installing the 206 updates...

Re-installed gutsy and the whole process again and still no sound, even with the the old HD that had everything working. I'm beginning to wonder if it is a hardware problem and it needs to be RMA'd (laptop).

Sudo lshw gives me this:

```
 *-multimedia UNCLAIMED
             description: Audio device
             product: SBx00 Azalia
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=64
```

---

### Post by Folk Theory on 2008-04-06
did you do all the steps again? recompile alsa, add the model=toshiba etc.?

---

### Post by Folk Theory on 2008-04-06
you can fell free to go ahead and install glx. desktop effects are working perfectly for me.

---

### Post by radtek on 2008-04-06
yes I did. I'm installing again at this moment. In the live cd environment the card is recognized with sudo lshw.

So I'm hopeful...?

I'll report back in a few

---

### Post by radtek on 2008-04-06
OK!

I have sound even after a reboot. Wireless was a snap with ndisgtk and I didn't need a reboot to get the driver to work.

I've disabled updates for the time being since I suspect something is broken in the repos.

Another thing is I've noticed gutsy seems to install a little differently each time, Alot like win98 did back in tha day. Its a "work in progress" and still pretty young for a release, but edgy seemed more stable. 

IMO, I'm not a big fan of this Toshiba and I think prospective buyers could do better. Boot time is quite long even with the extra ram and faster drive: 55 sec from grub start. My old averatec 3200 boots 6.06 in about 30 seconds even now. 

Still the price was right at the time- $598 @wallyworld, but the upgrades cost me close to $250 on newegg. Even so...cheaper than a Dell with about the same specs.



Since this is a "how to" for this model Toshiba; how about some investigation into booting?

---

### Post by Folk Theory on 2008-04-06
my booting time is _exactly_ the same: 55 from GRUB to gdm login and then it logs me in really fast. i think there's no point in getting intospeeding boot time untill we see how much faster Hardy is. it's supposed to be quite faster than Gutsy

---

### Post by fissionmailed on 2008-04-06
Every time I installed new linux headers I've had to recompile ALSA.  It's just something I've had to do.

---

### Post by radtek on 2008-04-06
I suspected this was a problem. I'm not updating a thing for a while. I just want my lappy to work and be stable enough so *I can work.*

I spent way too many hours on the sound issue.

---

### Post by Folk Theory on 2008-04-06
well by now ive done some 4 times, and it really doesnt take much to recompile ALSA...i think it's worth it to get the newest linux kernels.

btw dont enable compiz fusion...endless crashes. im never buying an ATI graphics video card again

---

### Post by radtek on 2008-04-08
Do you just go through the process again? And... Synaptic sez I have Alsa 1.0.14 when I 've installed 1.0.16. Is there a log file I need to edit in Synaptic?

---

### Post by fissionmailed on 2008-04-08
> **radtek said:**
> Do you just go through the process again? And... Synaptic sez I have Alsa 1.0.14 when I 've installed 1.0.16. Is there a log file I need to edit in Synaptic?

Well you because you already have all the files you need in there you just have to go in the directories(in /usr/src/alsa) and sudo ./configure ; sudo make ; sudo make install them.  You just have to recompile them. :)

I personally didn't change any log files in Synaptic.

---

### Post by Folk Theory on 2008-04-08
would using checkinstall change what synaptic says?

---

### Post by radtek on 2008-04-12
I'd already compiled them... But 'checkinstall'? I'll look at this command.

---

### Post by DUfire on 2008-04-13
> **fissionmailed said:**
> Every time I installed new linux headers I've had to recompile ALSA.  It's just something I've had to do.

Ahh, you do?
That's very odd indeed [to me, at least]. 
The only problems I've had since actually getting my sound to work [woot] has been it not working after stand-by/hibernate - a problem in which I've heard of a few different people having.

EDIT: Fission, you go to UNCC? 
I'm dual-enrolled at the CPCC Cato Campus a few miles down the road and I pass the main campus everyday. 
^^;

---

### Post by radtek on 2008-04-16
I've been able to speed up my boot time dramatically when I do this:

```
sudo gedit /etc/usplash.conf
```

I then change the 'yres' to 800 instead of 1040

then command:

```
sudo update-usplash-theme usplash-theme-ubuntu
```

I've been able to knock at least 10 seconds off.

Source:

[http://ubuntuforums.org/showthread.php?t=581075]("http://ubuntuforums.org/showthread.php?t=581075")

---

### Post by Folk Theory on 2008-04-18
no effect on mine...still 55 seconds

---

### Post by radtek on 2008-04-26
I upgraded to 8.04 several hours ago. Sound worked OEM, but I had to re-edit the driver for the wireless card. I had to add another line with "8197" in the Win ME .inf. Rebooted and it was working.

I'll add that while 7.10 is nice I really didn't care for it at all. It wasn't stable and I had way too many problems with it (at least in my case). I anxiously waited for the new LTS release. I'll stick with 8.04 for quite some time I believe.

Boot time is fairly swift, around 35-40 seconds without any tweaking.

The ATI driver appears to be working well. I'm getting desktop and window effects but haven't managed to locate where to GUI configure Compiz.

Some nice features. I'll have to explore further...

---

### Post by Folk Theory on 2008-04-27
upgraded to 8.04. lots of cool improvements. sound works out of the box!

i restarted after installation and guess what? no wireless! well im not sure what is the easiest way of going around it since i did alot of messing around but more or less 1)mark to stop using the HAL restricted driver and a new third restricted driver called atheros support or something.

2) i then uninstalled the .inf and reinstalled but i _doubt thats necessary_. there's definitely _no need to edit_ the net5211.inf file or any of the files we actually had to edit (blacklist, interfaces) 

3) anyways restart, do the usual ifup/down dhclient dance and you should be up and running in hardy

---

### Post by Folk Theory on 2008-04-30
ok. everytime i restart the 'front' is turned on, so even though i have earphoes plugged in, the computer's speakers go off at full sound...this has caused some embarrasing moments including waking up my family at 1:00 AM...how do i fix this?

---

### Post by DUfire on 2008-05-01
Go to bed at a decent hour? :P

[Just kidding].

---

### Post by fissionmailed on 2008-05-05
> **Folk Theory said:**
> ok. everytime i restart the 'front' is turned on, so even though i have earphoes plugged in, the computer's speakers go off at full sound...this has caused some embarrasing moments including waking up my family at 1:00 AM...how do i fix this?

I just turn the log in sound off and make sure to plug it in after I boot up.  This may not be any help in fixing the problem but this is what I do as a bandaid. 



Sorry I haven't been much help lately but it's been final exam time here at my college and I've been busy. 

That's interesting to know about 8.04, has anyone upgraded or has every one just did a clean install?  Oddly enough I've never upgraded but always did a clean install(most likely to me using windows D= ).  I'm interesting in the upgrading so I don't have to set up a 32-bit browser and all the plug ins again but it may not even work that way haha.

Edit: I just reread radtek's post, dur dur dur. Never mind me.

---

### Post by Folk Theory on 2008-05-05
no you see pluging in speakers or headphones normally/expectedly turns off the computer's own speakers (called 'front' in the sound settings) however, this isn't happening. so plugging in headphones doesn't work as 'a bandaid'. if it did, that'll be enough for me, i dont need an actual fix just a hack.

---

### Post by fissionmailed on 2008-05-06
> **Folk Theory said:**
> no you see pluging in speakers or headphones normally/expectedly turns off the computer's own speakers (called 'front' in the sound settings) however, this isn't happening. so plugging in headphones doesn't work as 'a bandaid'. if it did, that'll be enough for me, i dont need an actual fix just a hack.

Ooohhhhh, sorry for misunderstanding.  Have you tried putting the "options snd-hda-intel model=toshiba" back in /etc/modprobe.d/alsa-base?  Because it might have overwritten that in the upgrade or something. I can't really think of anything other than that.

---

### Post by fissionmailed on 2008-05-15
I found an easy way to get the effects working.  What I did was uninstall the driver from the restricted drivers and then installed it with [envy]("http://albertomilone.com/nvidia_scripts1.html"). That got it working and if you want more things to toy with even more...

```
sudo aptitude install compizconfig-settings-manager 
```

That will let you customize it.  I've been trying to get the big desktop to work with my monitor but it's been bring hard.  That's how I stumbled upon envy.  

[http://ubuntuforums.org/showthread.php?t=301941&page=1](http://ubuntuforums.org/showthread.php?t=301941&page=1)
If you wanna the info on it.  
[http://wiki.cchtml.com/index.php/Configuring#Graphical_Configuration](http://wiki.cchtml.com/index.php/Configuring#Graphical_Configuration)
Has some good info too.

---

### Post by Folk Theory on 2008-05-15
yah i got it working just by installing fglrx or wtvr thats called and changing xorg.conf to say 'enabled' wherever it says compositng extension or something similar BUT problem is...its awfully slow with our ATI radeon graphic cards...so the question is, is yours really slow or does it operate at normal speeds? 

if it's not slowing you down i'll re-instal it using your method.

---

### Post by fissionmailed on 2008-05-16
> **Folk Theory said:**
> yah i got it working just by installing fglrx or wtvr thats called and changing xorg.conf to say 'enabled' wherever it says compositng extension or something similar BUT problem is...its awfully slow with our ATI radeon graphic cards...so the question is, is yours really slow or does it operate at normal speeds? 

if it's not slowing you down i'll re-instal it using your method.

I'm using 7.10 and it's fast for me.  I haven't upgraded yet due to the virtualbox thing and I use that for working some in XP.  I should install Hardy on another partition and see how it goes though.

---

### Post by Folk Theory on 2008-05-17
when i did it it was still 7.10. i'll go ahead and install with your method.

---

### Post by Folk Theory on 2008-05-17
i found this [article]("http://www.ubuntugeek.com/toshiba-laptops-alive-to-the-sound-of-music.html") about sound in toshiba laptops. he has some small differences to what we did.

installing envyNG atm

EDIT: i installed envy succesfuly. however:
> $ compiz
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity
did you have to install xgl?

---

### Post by Folk Theory on 2008-05-18
yeah i still can't get it to work but now when starting compiz from the command line everything goes white...

---

### Post by Folk Theory on 2008-05-29
today my boot time clocked in at only 33 seconds with debian lenny...
i use:
dash as /bin/sh, readahead and insserv
[http://wiki.debian.org/BootProcessSpeedup?highlight=%28boot%29](http://wiki.debian.org/BootProcessSpeedup?highlight=%28boot%29)

im not sure if all this would work on ubuntu too...but IIRC ubuntu uses dash already so no need to do that.

---

### Post by fissionmailed on 2008-06-03
IF you want a GUI I finally tried WICD and it works perfectly.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

Follow the instructions and it works fine.

---

### Post by Folk Theory on 2008-08-04
yo guys, it's been a long time. have any of you found any remaining problems that are inherent to our particular model?
i've been using debian lately so i haven't tested hardy too much on this computer...

---

### Post by lacostranostra on 2008-08-04
i have not been able to reduce the brightness of my laptop screen on my a215 s5837. anyone find a work around?.

---

### Post by radtek on 2008-09-01
I've developed a problem over several "clean installs" that the virtual terminal no longer works but displays a corrupted screen.

Overall installation is better with 8.04 but for some reason 8.04.1 gives me an unstable system. I had to revert. Still a corrupted virtual terminal. WTF?!

---

### Post by radtek on 2008-09-07
Another issue I've had since buying this laptop is the random freezes and lockups. Well not so random since the problem seems to only occur when I am web browsing. I use FF or Epiphany and it doesn't seem to make a difference.

I'm wondering if anyone else sees this problem? Could it actually be hardware based instead? I'll admit that I haven't run anything but several different flavors of Ubuntu on this lappy so I have only a singular frame of reference.

Thanks

[edit] 09/10/2008

I've been running DesktopBSD with ZERO problems or lockups since Sunday. No wifi yet. I got rid of everything related to Firefox and just use Konqueror with an ethernet cable.

---

### Post by radtek on 2008-10-23
Hooray!

I installed Intrepid Ibex 64bit beta last week. EVERYTHING works OEM! Very stable!

Wifi works better. Instead of 78% signal I get 100% frequently.

Zero lockups so far.

Laptop seems a little snappier as well.

Virtual terminal works again.

---

