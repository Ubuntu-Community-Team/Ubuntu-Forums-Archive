---
title: "[SOLVED] advice for video card needed"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by heian on 2008-11-12
Hi,

Im new here and trying to install ubuntu.

Here is my very "simple" question.

I need to buy a videocard, only for internet use.
Not a new one, only 1024x768 pixels and pci or Agp (4x)

** and it should work out of the box **  
(as i get tired from changing my xorg.conf, trying to get 
it working)

Is there a list from current supported cards?  or what card
do you guys advice my?  (brand, type)

Thank in advance!

heian

(who loves ubuntu on first sight, but confused about not
working videocards)

---

### Post by nhasian on 2008-11-12
just get the cheapest nvidia card you can find new and you should be all set.

---

### Post by jimmy the saint on 2008-11-12
Nearly all Motherboards have integrated graphics that work fine and are more than sufficient for your needs.
Alternately, go for a cheap Nvidia or ATI card. Both have opensource drivers and will just work with Ubuntu.  Go for a generation back to ensure compatibility.

---

### Post by binbash on 2008-11-12
Don't go for Ati, their drivers suck at linux

---

### Post by damis648 on 2008-11-12
> **binbash said:**
> Don't go for Ati, their drivers suck at linux

+1, just get a cheap Nvidia card, maybe a 7 or 8 series. The restricted drivers for those are pretty good, no Xorg.conf modifications needed. I have an 8600M GT (mobile) and it works great. Alternatively, I don't know if they sell as AGP or PCI cards, but cheap Intel chipsets work out of the box, so if you have a motherboard with one, go for it. Maybe they sell them separately, I don't know.

---

### Post by jimmy the saint on 2008-11-12
I agree that nvidia cards perform better, but for his needs, I think ATI is fine.  They opened their driver specs so the open source drivers are getting better, and the internet does not require 3D acceleration.  I doubt he will be installing the binary drivers if all he needs is the internet.  Therefore, ATI/Nvidia should both be fine.  

Also, the 8 series is a bit much for 1024/768 internet browsing

---

### Post by heian on 2008-11-12
That is my experience too at the moment. 
I got a nVidia fx 5200 V128 and it is not supported in linux anymore.

Ati i don't know yet, hope that someone had a good experience after a clean install, and got the videocard working without any driver issues.
(brand and model name are very wellcome)
Or is there a list with fully supported cards ?

---

### Post by overdrank on 2008-11-12
> **heian said:**
> That is my experience too at the moment. 
I got a nVidia fx 5200 V128 and it is not supported in linux anymore.

Ati i don't know yet, hope that someone had a good experience after a clean install, and got the videocard working without any driver issues.
(brand and model name are very wellcome)
Or is there a list with fully supported cards ?

Hi and I believe that graphics card will work well in Hardy 8.04. Which version are you installing?

---

### Post by Elfy on 2008-11-12
It should work in intrepid as well - might need to enable proposed repos though to get the updates

I was running a GeForce4 MX400 until yesterday in intrepid :)

---

### Post by heian on 2008-11-12
Thank you all for the quick replies !  :)

Got some idea now, the Geforce mx400, nvidia 7-8 series, so now i can try to find one for sale.

What i see is that the xorg.conf is abit changed from earlier versions. Not possible to set the resolution anymore.

The fx5200 v128 i can't get it working in 8.04 and 8.1
installed envy ng-core, nvidia-glx-legacy, restricted drivers and so on, but still the resolution was set to 800x600 :(

[http://start.ubuntuforums.org/showthread.php?t=971567](http://start.ubuntuforums.org/showthread.php?t=971567)

im nearly to give up this card

---

### Post by Elfy on 2008-11-12
I wasn't saying get a new card - I don't believe overdrank was either :)

First - what version of ubuntu are you using?

Second what have you done to install a driver?

Can you also open a terminal from Apps>accessories and give us the output you get after running these commands

```
lspci
cat /etc/X11/xorg.conf
```

Lets see what can be done before you wander of to the shops :)

Edit - I certainly wouldn't suggest getting a card as old as my old GeForce4 :)

---

### Post by heian on 2008-11-12
Hi,

Im new to linux, and try to install a fx5200-v128
on ubuntu 8.04.  I got the same card like this link:
[http://www.ciao-shopping.nl/AOpen_Aeolus_FX5200_V128_PCI__659817](http://www.ciao-shopping.nl/AOpen_Aeolus_FX5200_V128_PCI__659817)

I think i have tried everything already to get it working, installed envyng-core, nvidia-glx-legacy, restriced drivers and so on, but the resolution keeps being 800x600.

Can somebody who did a clean install with 8.04, and got the same
card working, tell me in newbie language what to do to get it running? Spend evenings already to try myself, but not succesfull.

Many thanks in advance!

heian

---

### Post by starcannon on 2008-11-12
Heres a great deal on ebay:
[http://cgi.ebay.com/BFG-nVidia-GeForce-FX-5500-OC-AGP-128MB-Video-Card-New_W0QQitemZ120332149573QQihZ002QQcategoryZ3762QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/BFG-nVidia-GeForce-FX-5500-OC-AGP-128MB-Video-Card-New_W0QQitemZ120332149573QQihZ002QQcategoryZ3762QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

---

### Post by emshains on 2008-11-12
> **jimmy the saint said:**
> Nearly all Motherboards have integrated graphics that work fine and are more than sufficient for your needs.
Alternately, go for a cheap Nvidia or ATI card. Both have opensource drivers and will just work with Ubuntu.  Go for a generation back to ensure compatibility.

The Silicon Integrated Systems on-board video adapter sucks. The intel on-board video adapter sucks. No on-board video adapter sucks even more. 
By what I mean with sucks, is that it doesn't even support 2D acceleration, or, oh wait, the last xorg update came with a -intel ending, and in the description, there was said something about 2D, nothing about 3D though, its about time. 







Now on to the topic. 
If you want a card that works out of the box, you will have to install ubuntu with it, because if you suddenly change the video card, the X won't work at all, at least for me it didn't. I'd suggest a GeForce 2, atleast it worked for me, when I had 7.10. I could play some games, but not too much/good. It was fully supported, the only thing I had to do, is install the restricted drivers. 
You could try an ATI, but that's not the one I'd suggest. 
Just for the record, we are talking about second hand ones, at least I am.

---

### Post by overdrank on 2008-11-12
> **heian said:**
> Hi,

Im new to linux, and try to install a fx5200-v128
on ubuntu 8.04.  I got the same card like this link:
[http://www.ciao-shopping.nl/AOpen_Aeolus_FX5200_V128_PCI__659817](http://www.ciao-shopping.nl/AOpen_Aeolus_FX5200_V128_PCI__659817)

I think i have tried everything already to get it working, installed envyng-core, nvidia-glx-legacy, restriced drivers and so on, but the resolution keeps being 800x600.

Can somebody who did a clean install with 8.04, and got the same
card working, tell me in newbie language what to do to get it running? Spend evenings already to try myself, but not succesfull.

Many thanks in advance!

heian
Hi and you have a thread already on this so please stick to it. I have moved your post to your thread and hopefully you issues will get resolved. :)

---

### Post by heian on 2008-11-12
Thanks to everybody for helping me !!!

Here are some more details about my pc:

motherboard is a MS-6545  ver. 1
fx5200-V128   brand unknown
running Ubuntu 8.04   (fresh install)

after a new install, the resolution is 800 x 600
after enable restricted drivers in system, the resolution will be even
more low then it is right now.
with synaptic i had installed several packages concerning nVidia      drivers, like envyng-core, nvidia-glx-legacy and several more, don't know which one exactly anymore. But still resolution keeps on staying at 
800 x 600

(Ubuntu is just newly installed and not updated yet)

output of lspci:

robby@ubuntu-2:~$ lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
02:01.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:03.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:03.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
02:03.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
02:04.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
robby@ubuntu-2:~$ 



this is my xorg.conf

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by overdrank on 2008-11-12
> **heian said:**
> Thanks to everybody for helping me !!!

Here are some more details about my pc:

with synaptic i had installed several packages concerning nVidia      drivers, like envyng-core, nvidia-glx-legacy and several more, don't know which one exactly anymore. But still resolution keeps on staying at 
800 x 600



This can cause issues. If you installed envy and used it to install the drivers the others are not need and can cause conflicts in the system. Have you tried the xfix option when booting into recovery mode?

---

### Post by heian on 2008-11-13
hi,

I tried to boot with ctrl-alt-F1, but it gave me only a short of
terminal prompt at the end. Don't know what to do then.

The pc is just formatted and installed with Ubuntu 8.04.

With Synaptic i installed  envyng-core 1.1.1ubuntu17. After it
succeeded, rebooted again but there was still the 800 x 600 pixel
screen. No higher resolution possible. 
After that uninstalled envyng.

Following on above, i enabled the restricted drivers,
(nVidia accelerated graphics driver, (latest cards)
and now the resolution is max: 640x480
After that disable the restriced drivers, got my 800x600
screen back.

Can you please advice me what i can try next?

---

### Post by Elfy on 2008-11-14
The xorg.conf posted does not show the driver - please run the cat xorg command above - check that nvidia is shown there.

If it is run this command

```
gksudo nvidia-settings
```

If it says it's not installed do so it will give instruction - you can use ti to set the resolutionfor your nvidia card.

---

### Post by cochingeek on 2008-11-14
Hi I am using nvidia 8600GT in intrepid ibex 64bit. It is working fine on nvidia driver 177 (ubuntu supported). I get all the compiz special effects.

---

### Post by heian on 2008-11-14
Hi,

I did exactly what you mention, and this was the result:

gksudo nvidia-settings : had to type my password and then it
returns back to terminal.

cat /etc/X11/org.conf  gave the following output:

robby@ubuntu-2:~$ gksudo nvidia-settings
robby@ubuntu-2:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
robby@ubuntu-2:~$ 

strange enough i didn't got a way to set the screen resolution.
( i noticed that xorg.conf from 8.04 is so different from 7.10 )

hope that this give some more information, is there anything i can do next? (btw, this pc contains no personal information, if it makes it more
easy, i can open remote desktop for help)

thanks for all the response!

heian

---

### Post by Elfy on 2008-11-16
After you removed envyng did you rerun the hardware drivers tool to install the driver?

Xorg is still not showing the driver.

When you open hardware drivers does it recognise that the card is there? If it does what state does it say the driver in - deactivated, activated, activated but not in use?

---

### Post by heian on 2008-11-16
Hi guys,

Finally got this card working, found it accidently !

Reason was that i used a KVM switch, and therefore the monitor
was probably not detected well.

After the monitor was connected straight to the computer,
it comes standard already with the right resolution 1024x768.
(Even ubuntu 8.10 works well now)

Strange enough this problem appears only on this machine.

Thanks forestpixie and others for your support, if you where not
here, i throw away money for another old pci card.

---

### Post by Elfy on 2008-11-16
I haven't gone back and looked at the whole thread - so don't know if you mentioned it previously - the kvm switch that is. If you didn't then I guess it's a bit of a lesson in "we might like to know that" :lol:

Glad you're sorted anyway - can you mark the thread solved please.

Have fun

---

### Post by videoshoros12 on 2009-01-07
Hi,
Horoscope is a powerful tool offering insight into deep influence on our lives and there are many people depending entirely on it to take decisions. It is in the human nature to be curious about ourselves and there are many people considering the horoscope as the answer to their questions.You can get more information from [http://www.astrology-enterprises.com/Horoscope-Videos.asp](http://www.astrology-enterprises.com/Horoscope-Videos.asp).

---

