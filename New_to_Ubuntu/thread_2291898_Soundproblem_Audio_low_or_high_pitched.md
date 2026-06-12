---
title: "Soundproblem: Audio low or high pitched"
date: 2015-08-23
forum: New to Ubuntu
---

### Post by Merwco on 2015-08-23
Hello everyone.

I'm new to Ubuntu and Linux and I have a very strange problem with my Audio.
I'm using an audio Interface, which works as a dedicated USB sound card (PreSonus AudioBox 22VSL)
where my Headphones and Microphone are plugged in. At system start my Audio is fine, but after a while
the Sound gets pitched up or down. For example while playing music it's like playing 10% too fast or slow.
But every Sound is pitched like this.
Another way to reproduce the problem savely is the following: I have a webcam with a build in mic 
(which I don't use) but although my audiointerface is chosen as the default device the webcam get's
treated as the default device. If I change the input device with the menu of the Speaker Icon in the top
right corner to my audiointerface the sound gets low pitched instantly.
Another problem occured: after I started pavucontrol to change the device the sound got instantly low pitched.
But then I used the build in Menu of Ubuntu to change my input device and my Sound is normal. But now
my Input Sound is low pitched.

A temporary workaround is to use the command "pulseaudio -k" in the terminal, but it does not help for a long time.

I hope you guys could help me to solve this problem. Here are my system specs as I think they can be important:

CPU: Intel Core i7 3770k
RAM: 16GiB Corsair Vengeance LP, DDR3 1600mhz CL9-9-9-24. 4 memory modules, 4GiB for each module
Mainboard: Asus P8Z77-V
Graphicscard: nVidia Geforce GTX 680: Gainward Phantom version with 2GiB VRAM
3 1TB HDDs, no SSD
PreSonus Audiobox 22VSL audiointerface and a Microsoft Lifecam HD3000

If you need any more Information I try to give them.

---

### Post by tgalati4 on 2015-08-24
If your sound card is switching from 44.1 kHz to 48 kHz decoding, then that will result in an 8.8% pitch increase or decrease.  You will have to research what the default decoding values are for your Presonus card and what config settings to lock them in pulseaudio.

---

### Post by Merwco on 2015-08-24
Chaning the encoding from 16bit to 24bit (the AudioBox seems to only support 24bit) in the Pulseaudio config fixed the problem, thanks!

---

### Post by Merwco on 2015-08-24
After reboot the problem is back. The changes in the config still exist.

---

### Post by NM5TF on 2015-08-24
have you installed the excellent "pulseaudio-equalizer" yet ??? 

if not....

open a terminal & key in:

```
sudo apt-get install pulseaudio-equalizer
```

I looked the PreSonus web site & noticed that their software only works with MAC or WIN....

it seems that you are just using it as a pre-amp/mixer ??? unless you are using WINE....

you might take a look at "Audacity" for some of your processing applications...

of course, YMMV....

tommy

---

### Post by Merwco on 2015-08-25
Ok I'm going to try to install it and look if it fixes the problem.

> [COLOR=#000000]I looked the PreSonus web site & noticed that their software only works with MAC or WIN....[/COLOR]

[COLOR=#000000]it seems that you are just using it as a pre-amp/mixer ??? unless you are using WINE....[/COLOR]

[COLOR=#000000]you might take a look at "Audacity" for some of your processing applications...[/COLOR]

The Interface has headphone pre-amps and pre-amps for my microphone (Rhode NT2-A). I even don't use the software
under Windows. It's more like an external soundcard, because the headphone preamp has a much better quality then
my onboard soundcard.

---

### Post by NM5TF on 2015-08-25
OK...got it...

have you tried an equalizer at all ???

pulseaudio-equalizer is a good starting point...it comes with many pre-sets, or you can make a custom
preset & save it to a file...here is an article with installation info:

[http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html](http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html)

tommy

---

### Post by Merwco on 2015-08-26
I installed the equalizer and it didn't help in any way with my problem. it's still there.
At system start the wrong microphone is chosen (my webcam microphone although the audio interface
is set as standard) and by opening the audiosettings in the upper right corner the audio gets low
pitched.
I don't even understand how an equalizer should fix that...??

---

### Post by NM5TF on 2015-08-27
well....you first start out saying you have problems with audio quality....an equalizer could fix that....

now you are saying that it is selecting the wrong mic input...of course an eq won't fix that....

good luck

---

### Post by Merwco on 2015-08-27
I didn't say I have problems with audio _quality, _I said my audio is pitched.
And I don't think an EQ could fix that. Well... not in that specific case. And with pitched I mean
that the audio is played too slow or too fast, but system wide.

---

### Post by tgalati4 on 2015-08-27
Start playing with the *pulseaudio* configuration.  Look in /etc/pulse.  Change one value at a time and take notes.

You need to restart *pulseaudio* after each change.

```
man pulse-daemon.conf
```

You may need some fancy configuration to get everything to work correctly:  [http://askubuntu.com/questions/147397/pulse-audio-volume-control-forgets-settings](http://askubuntu.com/questions/147397/pulse-audio-volume-control-forgets-settings)

---

