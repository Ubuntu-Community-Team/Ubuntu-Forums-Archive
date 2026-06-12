---
title: "Need driver help!! New to ubuntu"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by ayhan_isaacs on 2008-08-06
Hello

I just installed Ubuntu 8.04

I need the drivers for these hardwares i cannot find them!!

-Creative 5.1 sound blaster audigy sound card (ubuntu didnt pick it up)

I have 2 DVD writers (LG and SAMSUNG), Ubuntu only picks up the Samsung i am guessing because it is the drive that allows CD's to be bootable. How do i get the LG to be activated as well? Driver??
  

Thanks 

-Ayhan

---

### Post by K2712 on 2008-08-06
> **ayhan_isaacs said:**
> 
-Nvidia 7300 VGA card (system > admin > hardware drivers ....gives me an error

What's the error message?

Also, post the output of:
```
lspci
```

---

### Post by billgoldberg on 2008-08-06
> **ayhan_isaacs said:**
> Hello

I just installed Ubuntu 8.04

I need the drivers for these hardwares i cannot find them!!

-Nvidia 7300 VGA card (system > admin > hardware drivers ....gives me an error)
-Creative 5.1 sound blaster audigy sound card (ubuntu didnt pick it up)
-Wacom tablet

I have 2 DVD writers (LG and SAMSUNG), Ubuntu only picks up the Samsung i am guessing because it is the drive that allows CD's to be bootable. How do i get the LG to be activated as well? Driver??
  
Also a link to download audio and video codecs

Thanks 

-Ayhan

For the codecs:

In a terminal (applications -> accessories -> terminal) copy/paste this command.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

Then press enter.

Enter you password (you want see how many digits you enter).

And it should start downloading and install all of them.

When it's ready, you'll have them all installed.

--

For the nvidea drivers, take a look here:

[http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A)

--

Don't forget to give us you lspci results.

Just type that in a terminal, and copy/paste (higlight the text in the terminal, and press the middle click button in the forum to paste it).

---

### Post by ayhan_isaacs on 2008-08-06
Thank you for the quick reply!

Your codec thing i am assuming worked because it downloaded some stuff, same thing for video thing then. but it says some index files failed to download

My updates icon picked up more stuff which i am guessing is what suppose to happen...

Also any good msn type programs on ubuntu and virus software??

WHat about the dvd drivers?

oo here is the code thing you wanted:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS649 Host (rev 10)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 48)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Gigabit Ethernet Adapter
00:08.0 RAID bus controller: Silicon Integrated Systems [SiS] 182 SATA/RAID Controller (rev 01)
00:0b.0 Multimedia audio controller: Creative Labs SB Audigy LS
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)

---

### Post by aeiah on 2008-08-06
most people use pidgin for msn messaging i think. and you dont need antivirus software unless you regularly send a lot of files to windows users and want to protect them. in which case, you could use clam-av. in general linux isnt affected by viruses. there havent been any spotted in the wild and only a small handful of proof-of-concepts

---

### Post by ayhan_isaacs on 2008-08-06
Thanks, yeah i just ended up using pidgin

And i will not install any virus scanners

I am still left with my 2 porblems, gettin my 5.1 speakers(no driver) to work and my LG dvd writer

THank you

---

### Post by Nepherte on 2008-08-06
Your lspci output lists 2 sound cards, one on board and your sound blaster live. I suggest you start with disabling your on board sound card. Ubuntu might have difficulties when both are enabled.

---

### Post by ayhan_isaacs on 2008-08-06
how do i disable my motherboard sound card??? When i tried plugging the speaker jacks into the motherboard audio inputs i got no audio i even messed around with the speaker settings...still no good!!

---

### Post by Cypher on 2008-08-06
You can disable the onboard sound card in the BIOS, hit F12/Del while the machine is booting up..

---

### Post by ayhan_isaacs on 2008-08-07
Switching off the audio input from my motherboard DID NOT HELP!

Still cant get my 5.1 to work, only the front speakers are working
HELPPPPPPP

---

### Post by curly_ on 2008-08-07
Have you looked at the sound levels? The rear(?) speakers might be muted. Use alsamixer and just press m on the things (Master, Headphone, etc.) so that under the vertical bar it says "00" not "MM".

---

### Post by ayhan_isaacs on 2008-08-07
I tried messing with those settigns still no good. you cant control volume of my front speakers unless you go to PLAYBACK: ALSA PCM.

Over there the master actually works while everything else doesnt. But om ALSA PCM there is only master no rear, front, center.

In ALSA mixer i tired all the 'tracks' under preferences but none them help with my speakers!!

AHHHHHHHHHHH

---

