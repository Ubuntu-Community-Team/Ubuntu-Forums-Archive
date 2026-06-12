---
title: "Sound Problems"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Obso1337 on 2008-06-09
Hi, I just switched to Ubuntu last night so am a complete newb. Everything went just fine, disks wiped, M$ gone, only Ubuntu remains. The biggest problem I have right now is a complete lack of any sound output. Now normally I would be able to just find a driver or something for my soundcard, however I bought this computer from my friend and have no idea what sound card it has. 
What I need is someone to show me the simplest way I can have Ubuntu find out what card I have so I can go about acquiring a driver.  
Many thanks.

---

### Post by BandD on 2008-06-09
Can you post the output of the following run in a terminal (Applications--> Accessories--> Terminal)

```
lspci
```

and

```
aplay -l
```

---

### Post by Obso1337 on 2008-06-09
obso1337@Proust:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

obso1337@Proust:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
obso1337@Proust:~$

---

### Post by BandD on 2008-06-09
**00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)**

**card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]**

These two together make up your sound card.  the first if the card itself and the second is the chipset of the actual card.  I'm about to head to bed, but try googling and searching the forums with those two things.  Namely from ATI on in the first and ALC on in the second.

Also, just to see, open up System--> Preferences--> Sound and change everything in the devices section to ALSA instead of default or pulseaudio and see if that makes a difference.  

Hopefully someone else can help you out.  I'll check back tomorrow sometime...

---

### Post by Colin82 on 2008-06-09
What kind of computer is it?  I have a Toshiba A135-S4427 that has the ALC861VD, but it is a Realtek.  The way I got sound working was adding 
```
options snd-hda-intel model=3stack
```
to the file.
```
/etc/modprobe.d/alsa-base
```

model=auto also worked for me.  However, I have still had no joy in getting the internal speakers on the laptop to mute when I plug in headphones.

---

### Post by Obso1337 on 2008-06-09
Alright, thanks a lot Band! :-)

Edit: Colin, this computer is a Toshiba Satellite.

So, to make the changed you posted above what exactly should I put in the Terminal and in what order? Sorry I have never worked with a Terminal before this morning. :-(

---

### Post by Colin82 on 2008-06-09
It's alright, I feel your pain.  I just switched not too long ago, but I will helped you as best I can.

Open the terminal, and enter 
```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base_bak
```
to make a backup of your alsa-base file, in case things don't work, you hav this to fall back on, but this is pretty easy/safe to do and easily reversible.

Then type 
```
sudo gedit /etc/modprobe.d/alsa-base
```
It will open alsa-base text document.  At the very bottom, add this line:
```
options snd-hda-intel model=auto
```
Save and close the file, exit terminal window and reboot the computer.  We'll try that line for now, and if that doesn't work we've got a couple others we could try.
I hope this helps.

---

### Post by Obso1337 on 2008-06-09
That did it! I have audio. 
As you said though there are issues with headphones. They mute my speakers, but do not produce sound themselves when plugged in. :-(
If anyone knows of any fixes for this I'd sure love to know them, but thats a fairly minor issue for me.

Thank you so much for your help Colin! :-D

---

### Post by Colin82 on 2008-06-09
Hey, not a problem, glad I could help.  Now to work on the headphone issue.

Doubleclick on your speaker icon to open up the sound mixer.  There should the a switches tab.  Ensure that headphones is checked.  If you don't have a switches tab, you could also try replacing that line in alsa-base with this.
```
options snd-hda-intel model=3stack
```
Like I said, replace the line I had you put in previously, don't just add this line.  Then save, exit, and reboot.

If that doesn't work, just go back into the alsa-base file and put the first line I gave you back in and reboot to get your sound back.

---

### Post by Obso1337 on 2008-06-09
Ok, headphones is checked, still no response. Changed the line and rebooted. No response from headphones however the sound from speakers sounds fuller and less anemic. Odd.

---

### Post by Nepherte on 2008-06-09
Try this instead:
```
options snd-hda-intel position-fix=1 model=3stack
```

---

### Post by Colin82 on 2008-06-09
Well, at least you got better sound out of it.  Go into the Terminal and type
```
alsamixer
```
and see if you can turn up your headphone volume.

Also, what kernel are you using?  If you're not sure, type
```
uname -r
```
into a terminal window and post the output please.

Edited the code for the uname command.

---

### Post by Obso1337 on 2008-06-09
obso1337@Proust:~$ uname -r
2.6.24-18-generic


First tried opening the alsa mixer in terminal. It came up, but there was no bar above the headphone section and I got no response from it. 
Then I tried the line Nepherte posted and rebooted. No results. Headphone still mute the speakers and produce no sound.

---

### Post by Colin82 on 2008-06-09
Unfortunately, I don't have any more advice for you to try.  I can't connect my laptop to the internet right now, but when I get back to the U.S. at the end of the month I will be able to.  I'm going to try compiling ALSA from source and upgrading to the -19 kernel.  Hopefully one of those will be the solution to the problem.

---

### Post by argail1980 on 2008-06-09
actually, the snd-hda-intel module seems the wrong one for you. However, there is a "toshiba" model

change the line 
> options snd-hda-intel model=3stack (or whatever it is now)
to 
```
options snd-hda-intel model=toshiba
```

if that doesn't work, try playing with the options for snd-atiixp. Judging from your lspci, you have a ATI IXP card, not a hda intel. but I have no idea at all what options to set. Thats why I would try the other possibility

---

### Post by Nepherte on 2008-06-09
Looking on the sound card matrix of the alsa-project, it shouldn't be hda-intel but indeed atiixp: [http://www.alsa-project.org/main/index.php/Matrix:Module-atiixp](http://www.alsa-project.org/main/index.php/Matrix:Module-atiixp)
If the above suggestion did not work, you might want to compile the alsa drivers manually with explicitly specifying atiixp card. You can find the details on compiling the drivers on the same site. You can always ask some extra information here.

---

### Post by Obso1337 on 2008-06-12
Thanks for trying Argail, however that didn't seem to work either. I'll check the website posted above and try and get it fixed as soon as I can. Thanks to everyone for all your help. :-D

---

### Post by portlandor on 2008-06-12
Hi,

I fixed all of my Alsa HDA problems by using Gnome-alsamixer.  I had no sound inputs that worked before that.  Also, I found a couple of other non-alsa specific mixers that work.  So install a couple others from the package manager and try them.

Rob.

---

### Post by orange on 2008-06-14
> **Nepherte said:**
> Try this instead:
```
options snd-hda-intel position-fix=1 model=3stack
```

This fix worked, along with [http://ubuntuforums.org/showpost.php?p=5148501&postcount=4](http://ubuntuforums.org/showpost.php?p=5148501&postcount=4) got sound working on my sahara notebook nb545410.

 lspci|grep Audio
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

thanks guys!

---

### Post by virtudtierra on 2008-07-08
I added to two lines in the /etc/modprobe.d/alsa-base file:

options snd-hda-intel model=dallas
options snd-hda-intel model=3stack

So, if I want to use the frontspeakers, I comment (#) the line with the option that let work the headphone (dallas) and reboot.

And now work the headphone output and the frontspeaker system. But, I need reboot to use ¿There is any other solution?

try it and enjoy it (solved?, I guess no)

virtudtierra

---

### Post by virtudtierra on 2008-07-09
> **BandD said:**
> **00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)**

**card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]**

These two together make up your sound card.  the first if the card itself and the second is the chipset of the actual card.  I'm about to head to bed, but try googling and searching the forums with those two things.  Namely from ATI on in the first and ALC on in the second.

Also, just to see, open up System--> Preferences--> Sound and change everything in the devices section to ALSA instead of default or pulseaudio and see if that makes a difference.  

Hopefully someone else can help you out.  I'll check back tomorrow sometime...



Yo agregué las siguientes librerías desde adept_manager

alsaplayer-jack libjack0 libavc1394-0 libiec61883-0 libfreebob0

y tengo 100% operativos el jack de los audífonos y los frontspeakers

slaudos, y enjoy it!

Jorge

---

### Post by enigmatic28 on 2008-12-24
Hi All,

i am experiencing the same problem, i have the same hardware on my laptop.

i tried all the steps listed in this thread, but none of them worked for me.

this is one of the problem that is preventing me to fully switch to linux even though i love to fully switch to linux.

thanks....

---

### Post by SpaceAceFrehley on 2011-10-19
Sorry to bump a very old thread but i had a simmilar problem and after several hours of fighting with not working sound with
```
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
``` on a Toshiba Sattelite L30-114 i finally found how to make it work perfectly (including headphones).

After the installation of Ubuntu 8.04.4 LTS alsamixer did not work at all. To enable it i did this in the terminal (as root):
```
apt-get install module-assistant
m-a update
m-a prepare
m-a a-i alsa
```
It takes about 15 minutes to complete but it's worthwile. Alsamixer now works perfectly, but there is still no sound. Now i opened
```
vim /etc/modprobe.d/alsa-base
```
(you may use any kind of text editor instead of vim like gedit, kate, nano etc.)
and add this line at the end of the file:
```
options snd-hda-intel model=asus-laptop
```
Now the interesting thing is that i did not do that on an asus laptop so don't worry about the name. Just save it.
Now you may reboot, or paste this:
```
alsa force-reload
```
And voila! It worked for me.

The alsamixer repair part may not be vital to enable sound.
If model=asus-laptop does not work for you try model=uniwill-31 or just model=asus.
Hope my solution helps somebody just like i helped my friend with coming up with it (now she does not have to use XP anymore :) ).

---

