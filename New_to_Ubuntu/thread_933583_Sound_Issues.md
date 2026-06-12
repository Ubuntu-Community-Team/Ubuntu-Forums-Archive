---
title: "Sound Issues"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by Sparty26 on 2008-09-29
Hey, I am a complete newb here, not just to this site but to Kubuntu as well. I just installed it on Gateway 7330gz notebook yesterday, and things have been going great except for one thing: there is no sound on my computer now! My sound was working fine before I installed kubuntu, so it wasn't a preexisting condition. Also, everything else seems to be working just fine. I have been reading all over the web to try and find a solution but I have come up empty handed so far. Any help would be much appreciated, thanks!

-Adam

---

### Post by lapubell on 2008-09-29
sometimes the little speaker icon in the bottom doesn't work quite right in kubuntu.

try this:

open the terminal and type

alsamixer

then use the arrow keys to adjust the volume for the main output.  when you are done hit CTRL+C to exit.

did that help?

---

### Post by kansasnoob on 2008-09-29
If you want to get back to pure gnome look here:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

In the gnome desktop I like to install gnome-alsmixer:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Applications > Sound and Video:

[ATTACH]86752[/ATTACH]

[ATTACH]86753[/ATTACH]

---

### Post by Sparty26 on 2008-09-29
Thanks for responding. I did what you said, but I still can't hear anything, even with teh sound turned all the way up?! Any more ideas?

---

### Post by Sparty26 on 2008-09-30
I tried running alsamixer and it said that everything was fine, so that didn't work. I tried checking my computer's bios, and there was nothing in htere that seemed to be out of place. Does anyone else have any suggestions?

---

### Post by shifty_powers on 2008-09-30
> **lapubell said:**
> sometimes the little speaker icon in the bottom doesn't work quite right in kubuntu.

try this:

open the terminal and type

alsamixer

then use the arrow keys to adjust the volume for the main output.  when you are done hit CTRL+C to exit.

did that help?

dude, you are a star...

the sound on my laptop has been sounding low for a little while and it has been bugging the hell out of me!

just goes to show no matter how long you use kubuntu, you can still learn...

(heh, guess i'm still a knowledgeable amateur and no expert...)

---

### Post by bobnutfield on 2008-09-30
Open a terminal and type:

> sudo lspci

so that we can take a look at what sound chipset you have.  We can advise better with this information. On laptops, sometimes a little editing is necessary in /etc/modprobe/alsa-base.  Post the output of lspci.

---

### Post by Sparty26 on 2008-09-30
When I ran > sudo lspci, this is what I got:


> 00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:05.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
01:06.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
01:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by bobnutfield on 2008-09-30
OK, I believe that your soundcard uses the snd-hda-intel module.  But to be sure, type:

> sudo lsmod | grep snd

Look for snd-hda-intel in the list.  If it is not, post what was returned.  Just need to know what module it uses to see if the /etc/modprobe.d/alsa-base needs to be edited.

---

### Post by shifty_powers on 2008-09-30
have a look at this thread, may help

[http://ubuntuforums.org/showthread.php?t=897185&highlight=82801DB&page=2](http://ubuntuforums.org/showthread.php?t=897185&highlight=82801DB&page=2)

---

### Post by Sparty26 on 2008-09-30
I tried it, and it returned:

> snd_intel8x0           35356  1
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_m                                                                                                   idi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmi                                                                                                   di,snd_seq
snd                    56996  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mix                                                                                                   er_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_d                                                                                                   evice
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

I didn't see the snd-hda-intel in that order in that list, but maybe you can see something that I don't.

---

### Post by bobnutfield on 2008-09-30
> snd_pcm 78596 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss

No, I was incorrect.  snd_intel8x0 is the module your card is using.  Have you checked in System>Preferneces>Sound to check thatin the box that says "Default Device" your correct card or ALSA is showing?  The snd_intel8x0 usually works right out of the box.

---

### Post by shifty_powers on 2008-09-30
what was the output of

```
cat /proc/asound/card0/codec#* | grep Codec
```

?

---

### Post by bobnutfield on 2008-09-30
There is a sound troubleshooting guide here.  It is a couple of years old, but the information is generally still relevant for Hardy.  We could guide you through all of these commands, but it is all contained in this thread:

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

There is no need at this point in trying to attempt the "Install from a fresh kernel" as this is not necessary for now.

---

### Post by Sparty26 on 2008-09-30
> **shifty_powers said:**
> what was the output of

```
cat /proc/asound/card0/codec#* | grep Codec
```

?

The result was:

> No such file or directory.

Also,

> Have you checked in System>Preferneces>Sound to check thatin the box that says "Default Device" your correct card or ALSA is showing?

This is a completely stupid question to ask, but how do I get to my preferences? As I said, I am a completely new to this system... :oops: I went to "System Settings" and then "SOund System," but I didn't see a "Default Device" box...

---

### Post by markbuntu on 2008-09-30
Look in this file on your computer, there are a lot of different drivers for the AC'97 and a lot of explaining about the options available for the zillion different ways OEMs tweaked that sound chip:

/user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz

---

### Post by bobnutfield on 2008-10-01
> **Sparty26 said:**
> The result was:



Also,



This is a completely stupid question to ask, but how do I get to my preferences? As I said, I am a completely new to this system... :oops: I went to "System Settings" and then "SOund System," but I didn't see a "Default Device" box...

Sorry, I failed to remember that you were using Kubuntu and the I was instructing about the Gnome desktop.  Just open a terminal and type:

> aplay -l

just to see if your card shows up.  If it does then I think that maybe just adding a short line to the end of your /etc/modprobe.d/alsa-base file might get it working.

---

### Post by Sparty26 on 2008-10-01
> aplay -l returns:

> aplay: device_list:205: no soundcards found.

---

### Post by Sparty26 on 2008-10-02
I am bumping this back up. I still haven't had any success in fixing this sound problem, although I have found out that it seems to be a common problem among Gateway notebooks. Anyway, I don't know if this helps at all, but when I tried opening "Amarok" for the first time, I got a message saying "xine was unable to initialize any audio drivers."

---

### Post by bobnutfield on 2008-10-02
> **Sparty26 said:**
> returns:

This is troubling.  Your lspci results show that the system is recognizing the sound card and lsmod shows that you have sound modules loaded.  I need to check a couple of threads for that card.  I will get back to you.

---

### Post by bobnutfield on 2008-10-02
Open a terminal and type:

> modinfo soundcore

Post the results.  We need to see if the modules are loaded, even though lsmod says they are.

---

### Post by Sparty26 on 2008-10-05
modinfo soundcore returns:

> filename:       /lib/modules/2.6.24-19-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:
vermagic:       2.6.24-19-generic SMP mod_unload 586

---

### Post by Sparty26 on 2008-10-07
I appreciate all of the help you guys are giving me. I feel bad bumping a thread, but I would really like to solve this issue...

---

### Post by Sparty26 on 2008-10-09
I'll bump this one more time in the hope that maybe somebody knows something about this issue. I can't find much help anywhere else I go, you guys have been great, but I would really like to have the sound back on my computer. ANy help is appreciated.

---

### Post by Sparty26 on 2008-11-03
One last ditch bump. Does anybody have any solutions?

---

### Post by mcheshpants on 2008-12-04
I believe i have the answer your looking for....

I also have a gateway 7330gz...
download alsamixergui from synaptic package manager and mute "external amplifier" by clicking the speaker above it "they will turn white when muted" this made my sound work

lemme know if this helped man...

---

### Post by Sparty26 on 2009-02-04
I downloaded the alsamixergui, but every time I open it, it only shows master and capture?

---

### Post by Sparty26 on 2009-02-04
Did you do anything else to get the external amplifier to show up? I can't get it to work still...

---

### Post by Sparty26 on 2009-02-19
Okay, I figured it out, it was the external amplifier problem. I can't be certain this was the issue when I was running Kubuntu, but I was finally able to get it to work after checking the box next to "External Amplifier," exiting out, and then going back in and unchecking it. Thanks for teh help guys. If anyone in the future reads this and needs help understanding what I just said, just send me a message.

---

