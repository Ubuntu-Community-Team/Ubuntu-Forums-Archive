---
title: "[Support Request] Headphones"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by kellja2001 on 2008-11-21
Hey everyone!

Sorry to be a pain, I know a few people have submitted this problem already.

I haven't yet found a response that gives a solution.

I'm using the newest version of Ubuntu (I think its 8.10) and I can't get my headphones to work. Please see the attached movie for a walkthrough of the problem.

My PC is a Sony Vaio VGN-FZ11Z
I'm running Ubuntu on a 110Gb partition and Vista on a 90GB partition.
Both were installed yesterday, so haven't had any time to screw up settings.
I'm using extended desktop (TwinView) in Ubuntu, if you're thinking I'm using 2 different PCs.

[B][SIZE="4"]Please see the attached video to show you what I have so far:

[http://www.kellja2001.co.uk/random/UbuntuAidHeadphones.mpg](http://www.kellja2001.co.uk/random/UbuntuAidHeadphones.mpg)[/SIZE][/B]

I am totally new to Ubuntu, and have limited knowledge of computers (I do want to learn though!), so please keep answers very detailed/comprehensive.

Many thanks in advance!

XxX

kellja2001

---

### Post by NullHead on 2008-11-21
What model is the sound device? You can look in lspci to find out.

---

### Post by kellja2001 on 2008-11-21
> **NullHead said:**
> What model is the sound device? You can look in lspci to find out.

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86M [GeForce 8400M GT] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

Thats what it showed me (I'm not sure which one of them is needed)

---

### Post by NullHead on 2008-11-21
I applaud you for understanding that lspci is a command to run in the terminal! I thought I'd give you a test considering that you already knew about alsamixer =D>

Anyhow, that device should be supported. > 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)That's the one that you've got. Notice it says "Audio deice". At first glance, I'd say it should be fully supported out of the box. From a [google search](http://www.google.com/search?hl=en&q=intel+82801H+ubuntu&btnG=Google+Search&aq=f&oq=), I'd say that you have a common problem. It also looks like your problem has already been fixed. 

This might be useful: [http://ubuntuforums.org/showthread.php?t=747054](http://ubuntuforums.org/showthread.php?t=747054) 

It's apparently for 8.04, but it might work in 8.10. I don't have the card myself, but perhaps with you now knowing what your sound device actually is, perhaps you can find out some more stuff by searching and googleing :D 

Hope this helped, and best of luck trying to figure it out.

---

### Post by kellja2001 on 2008-11-21
> **NullHead said:**
> I applaud you for understanding that lspci is a command to run in the terminal! I thought I'd give you a test considering that you already knew about alsamixer =D>

Thanks a bunch lol!

I took a shot in the dark. I won't lie, first time round, I typed ispci!!

> **NullHead said:**
> This might be useful: [http://ubuntuforums.org/showthread.php?t=747054](http://ubuntuforums.org/showthread.php?t=747054)

Haha! "Might" be useful, that totally solved the problem :D

It took a lot of reading, and guessing as to what it meant, but I eventually got there!

THANKYOU SO MUCH FOR YOUR HELP!!!

Lol, you've been awesome, cheers mate :D

XxX

kellja2001

P.s. If this is a recurring theme, and I suspect will bother many newbies to Ubuntu, is it worth me writing out a thread with a step-by-step guide as to how to fix the problem?

---

### Post by NullHead on 2008-11-21
> **kellja2001 said:**
> Thanks a bunch lol!

I took a shot in the dark. I won't lie, first time round, I typed ispci!!



Haha! "Might" be useful, that totally solved the problem :D

It took a lot of reading, and guessing as to what it meant, but I eventually got there!

THANKYOU SO MUCH FOR YOUR HELP!!!

Lol, you've been awesome, cheers mate :D

XxX

kellja2001

P.s. If this is a recurring theme, and I suspect will bother many newbies to Ubuntu, is it worth me writing out a thread with a step-by-step guide as to how to fix the problem?

If you think you could provide help to other people, then sure go ahead and write it. Often times, if a guide doesn't say "this is offically for X version of ubuntu" they won't use it, but in reality, most of the practice is the same from version to version. That's why the link worked for you. If you want to make one that says 8.10 on it, people will use it. Heck, if you just copied out that guide, and pasted it into a new thread that said 8.10 in there somewhere, than you'll get attention. 

People will ask you for help and what not, so be prepared to provide answers to people that could ask complicated question or even simple ones. 

It's up to you, but I'm glad you have everything working. :)

---

### Post by kellja2001 on 2008-11-21
[CENTER][SIZE="5"]**_[COLOR="Red"]Written Solution[/COLOR]_**[/SIZE][/CENTER]

**_Problem_**

When I play sounds in Ubuntu 8.10, they only play through my speakers. If I plug headphones in, the sound continues to play through my speakers, and the headphones remain silent.

**_Solution_**

1) Ensure the problem is not a broken headphone jack. If you have recently had a different operating system installed, and the headphone jack worked fine, it is very unlikely the jack is broken.

2) Open Terminal by pressing &#8220;Applications &#8594; Accessories &#8594; Terminal&#8221;

3) Type the command:

```
cat /proc/asound/card0/codec#* | grep Codec
```

This returns the model of your sound card(s)

e.g.

```
Codec: SigmaTel STAC9872AK
```


4) Open this link:

[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

5) Press ctrl+f and type the third group of characters from the model of your sound card (&#8220;STAC9872AK&#8221; in this example), one character at a time, until you find the closest possible match (&#8220;STAC9872&#8221; in this example).

6) Scroll down a small bit, read all the descriptions under the heading, and identify which is most similar to your sound card/PC (&#8220;vaio&#8221; in this example)

7) Type the following command in Terminal:

```
sudo nano /etc/modprobe.d/alsa-base
```

Enter your password if prompted.

8. Paste the following line at the end of the file (change MODEL with the type of sound card's model, in our example it should be "vaio" (without quotation marks)):

```
options snd-hda-intel model=MODEL
```

9) Press "ctrl+x" to "Exit", and press "y" to save.

10) Close all open windows.

11) Reboot your PC

12)Test your headphones out! They should hopefully work!

( I hope this helps someone! Many thanks to NullHead and "https://help.ubuntu.com/community/HdaIntelSoundHowto" for the information that aided me to solve this)

---

