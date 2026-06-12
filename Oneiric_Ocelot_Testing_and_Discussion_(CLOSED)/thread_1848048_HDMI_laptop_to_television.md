---
title: "HDMI laptop to television"
date: 2011-09-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Yumi on 2011-09-21
Any howto on getting movie output to HDMI on my laptop to watch it on the television?

Michael

---

### Post by Harry33 on 2011-09-22
> **Yumi said:**
> Any howto on getting movie output to HDMI on my laptop to watch it on the television?

Michael

You would need to have a digital (at least DVI) output on your laptop.
Then you can use an adaptor to change to DVI socket into HDMI socket.
And that is it.

I use the DVI output on my graphics card with a HDMI adaptor and a HDMI cable connected to the screen.

---

### Post by Harry33 on 2011-09-22
The above instuctions are for the picture only.
For the sound I use a separete S/PDIF plug into the separate amplifier.

---

### Post by technosysind on 2011-09-22
u cannot connect sound through HDMI port. Its only for picture. Harry is very correct :)

---

### Post by andrewabc on 2011-09-22
HDMI should output sound. Unless linux is not able to do so yet.

---

### Post by Harry33 on 2011-09-22
> **andrewabc said:**
> HDMI should output sound. Unless linux is not able to do so yet.

Basically yes, but in computers the graphics cards usually have a DVI output socket (some do also have a HDMI socket) only for graphics. Some cards also have S/PDIF socket, but this is rare. Instead, one may use the S/PDIF socket of the motherboard.
So, generally the sound card is integrated into the motherboard, not into the graphics card.

---

### Post by varesa on 2011-09-22
I think most of the laptops that have hdmi, can supply sound through it.

---

### Post by Harry33 on 2011-09-22
> **varesa said:**
> I think most of the laptops that have hdmi, can supply sound through it.

This is possible yes.
At least modern AMD desktop graphics cards can also do this.
Anyway, if it is HIFI sound you want, you need to buy a separate dedicated sound card into the PCI slot of the motherboard.

---

### Post by technosysind on 2011-09-22
I think you are talking about APU's and not regular CPU's. For a regular CPU, HDMI can never transmit good quality sound as the sound card is separate from the display IC

---

### Post by philinux on 2011-09-22
My Acer 1410 has an HDMI socket. It connects to my Onkyo receiver and I get great results. Sound and Video.

---

### Post by technosysind on 2011-09-22
Its the Receiver that is giving you great sound. If you use DMI cable directly to the LCD, sound will not be gr8.

---

### Post by philinux on 2011-09-22
> **technosysind said:**
> Its the Receiver that is giving you great sound. If you use DMI cable directly to the LCD, sound will not be gr8.

Also sounds good plugged directly into lcd tv. Obviously not as good as receiver.

---

### Post by perspectoff on 2011-09-22
My (HP) laptop has an HDMI connector. I connect it directly to my TV.

I use PulseAudio.

PulseAudio has a setting for HDMI output. 

No sweat.

I play stuff (video and audio) from laptop to TV all the time (HDMI is both video and sound, and yes, Linux supports it.) 

First I check to see if my kernel has the HDMI drivers (since Lucid, all the kernels do):

 aplay -l
 aplay -L

Then I install PulseAudio Volume Control (which will also install pulseaudio as a dependency):

 sudo apt-get install pavucontrol

Then I set the output to be the HDMI digital output:

Menu -> Multimedia -> PulseAudio Volume Control -> Configuration -> Internal Audio -> Digital Stereo (HDMI) Output

Easy.

From:

[http://www.kubuntuguide.info/index.php/Natty#HDMI_with_PulseAudio](http://www.kubuntuguide.info/index.php/Natty#HDMI_with_PulseAudio)

or

[http://ubuntuguide.org/wiki/Ubuntu:Natty#HDMI_with_PulseAudio](http://ubuntuguide.org/wiki/Ubuntu:Natty#HDMI_with_PulseAudio)

What I used to do (before HDMI) was to have a separate S/PDIF cable (or whatever you call the round connector) for video and then merely an audio cable from the headphone jack to the RCA connector on the TV. That can usually be done with any TV whatsoever and takes no special setup for sound (except for choosing the external video monitor).

I have never played with DVI and don't know if DVI is video only. If it is, then the separate audio connection can be used with it, too. DVI to HDMI convertors are dicey business, I have heard.

---

### Post by lucazade on 2011-09-22
I use an HDMI connection for a Nvidia 250gts card (w/ blob drivers) and a Samsung 24'' LCD.
Audio and video work like a charm, I had just to connect video card to the internal motherboard audio connector and to rename lcd source from hdmi to hdmi-pc (i hope to find an explanation one day for this strange behaviour!)

---

### Post by cariboo on 2011-09-22
I use a DVI to HDMI cable on my media center PC, with a separate audio cable from the speaker output on the motherboard. With an EVGA 6250LE PCI graphics card I get the full 1920X1080 resolutiuon on my 32" Samsung LCD TV with this setup. I didn't have to do any extra setup, I just connected the cable and turned everything on.

---

### Post by seeker5528 on 2011-09-22
> **technosysind said:**
> Its the Receiver that is giving you great sound. If you use DMI cable directly to the LCD, sound will not be gr8.

HDMI is digital so assuming you are talking LCD TV and the TV is hooked to the receiver, sound should be good, if it's not good it's a software thing not a hardware thing.

I've only had the opportunity to play around with HDMI to the TV in Windows since the computer next to the TV is not mine, but with ATI hardware and XP, sound wasn't so good, with the same ATI hardware and Vista/Win 7, sound is pretty good.

Later, Seeker

---

### Post by Yumi on 2011-09-23
To the original question, I have a HDMI socket on my Acer laptop and it is working with windows (no hardware problem).

But with 11.10 no picture. I tried System-Settings - Displays but it does not find anything apart from the laptop monitor.

There must be a setting somewhere or a additional piece of software.

Michael

---

### Post by seeker5528 on 2011-09-23
> **Yumi said:**
> To the original question, I have a HDMI socket on my Acer laptop and it is working with windows (no hardware problem).

But with 11.10 no picture. I tried System-Settings - Displays but it does not find anything apart from the laptop monitor.

I think with ATI and NVIDA there are additional utilities supplied for managing these things. I think with the open source drivers it theoretically should be managed by 'System Settings --> Displays'.

Since you have a laptop the extra variable is that they usually have a key combination 'Fn'+'Some other key' to switch between usage options for the displays the laptop's display, external display, or both. 

Outside of that you probably need to be more specific about your hardware to get better help.

The model number of the laptop and the output from opening a terminal window and typing ```
lspci -v
``` in particular the stuff that gets listed for the devices that are identified as 'VGA compatible controller' or 'Display controller'. 

Later, Seeker

---

### Post by dava4444 on 2011-09-23
i have used headphones in the past in this context, and some wireless ones with good sound would emerse you more in the movie!

i have done audio work before.. and unless your defo on speakers n such.. the best thing you can get for personal sound is good headphones ;) you'll hear soo much more.

peace

---

