---
title: "XBMC Reciever HD TV Problems and solutions"
date: 2014-05-20
forum: New to Ubuntu
---

### Post by HSken on 2014-05-20
[FONT=Liberation Sans][B]
[SIZE=5]INTRO[/SIZE][/B][/FONT]
About a month ago I decided to install Ubuntu 14.04 on an old pc and connect it to my Receiver using hdmi as a media center.
Also I wanted to useXBMC, for the movies, but also wanted the full Ubuntu desktop.
[LEFT]Also like listening to music using [Deezer]("http://www.deezer.com/"),there is a nice Android app, to remote control Deezer so you don't need to keep the TV switched on: [Deemotefor Deezer]("https://play.google.com/store/apps/details?id=com.nodria.deemote") And install [chrome]("https://www.google.com/chrome/browser/") and its [extension]("https://chrome.google.com/webstore/detail/deemote/lghkcfbokldgebkkkhiflfjcfceabegp").[/LEFT]

But I ran into quit some problems](*,), mainly with the sound: no pass through audio, cracks,extreme distortion, ...
I tried lots of tutorials and guide some helped, some broke the installation completely.

SOLUTION: &#8220;disable pulseaudio&#8221;, not remove pulseaudio, use ALSA: 
**Howto disable pulseaudio**** (scroll down)**

Secondary problem with sound, as I like to listen to music, my receiver [ONKYO TX-SR608 ]("http://www.uk.onkyo.com/en/products/tx-sr608-35325.html")only supports ANALOG input for ZONE 2, which in my case provides the dining-room of music.
SOLUTION: Output the sound twice, once to HDMI and once to onboard ANALOG jacks output in stereo: 

**Howto configure ALSA for dual sound output (scroll down)**

Secondary, no proper hardware acceleration for video in XBMC, I had a ATI/AMD Radeon 5700 card and followed this guide:[http://forum.xbmc.org/showthread.php?tid=174854](http://forum.xbmc.org/showthread.php?tid=174854)


[SIZE=5][B]Howto disable pulseaudio
[/B][/SIZE]
If your tried removing pulseaudio completely, it probably broke your &#8220;System Settings&#8221;, it will be missing a lot of icons, this you can fix simply by this, in terminal:

```
    sudo apt-get install ubuntu-desktop
    sudo reboot

```

Once rebooted, the best trick is to disable in staid of removing pulseaudio, in terminal:
Delete or move user pulse settings
```

Backup
sudo mv [COLOR=#000000]~/.pulse [/COLOR][COLOR=#000000]~/.pulse-backup
[/COLOR]Delete
sudo rm -rf [COLOR=#000000]~/.pulse[/COLOR]

``` 
```

sudo gedit/etc/pulse/client.conf

```    
Add the following two lines to this document, this will disable pulseaudio
```
    autospawn = no
    daemon-binary =/bin/true 

```Save & Reboot.
source & more info:[http://askubuntu.com/questions/8425/how-to-temporarily-disable-pulseaudio](http://askubuntu.com/questions/8425/how-to-temporarily-disable-pulseaudio)


Configure ALSA to use the your sound card, in terminal:
```
    aplay -l

```Look for the soundcard you want to use and look for card number and device number, in my case **card = 1** and **device = 3**
The output in my case:
> **** List ofPLAYBACK Hardware Devices ****
card 0: Intel [HDAIntel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0:subdevice #0
card 0: Intel [HDAIntel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0:subdevice #0
**card 1**:HDMI [HDA ATI HDMI], **device 3**:HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0:subdevice #0


Now open the ALSA config file, using the terminal: 
    
```
 sudo gedit/etc/asound.conf
```

Copy & Paste the following and don't forget to change the card and device id:
```
pcm.!default {
    type hw
  [B]  card 1
    device 3[/B]
}
ctl.!default {
    type hw
[B]    card 1
    device 3[/B]
}

```Save & exit this file.


Now we will need to install a ALSA sound mixer, open terminal:
    sudo apt-get install gnome-alsamixer
    gnome-alsamixer
source & more info:[http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/](http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/)(DO NOT DELETE ALSA!)

Now test your audio using and hold your fingers crossed:
    ```
speaker-test -t wav-c 6
```

If everything went well you should hear sound :).

[FONT=Liberation Sans][B][SIZE=5]Howto configure ALSA for dual sound output[/SIZE]

[/B][/FONT]Be sure to successfully disable pulseaudio first using the guide above, then  open the alsa config file, using the terminal again: 
    ```
sudo gedit/etc/asound.conf
```


And paste the following and  don't forget to update the device and card id according your system!
Look for "pcm.digital-hw " and "pcm.analog-hw", use ```
aplay -l
``` to look them up.
My file: [ATTACH]253318[/ATTACH]
```
pcm.!default {
    type plug
    slave.pcm "8channel_expander"
    hint {
        show on
        description "Multichannel output to both analog and hdmi - for use with XBMC"
    }
}


ctl.!default {
    type plug
    slave.pcm "8channel_expander"
    hint {
        show on
        description "Multichannel output to both analog and hdmi - for use with XBMC"
    }
}


pcm.xbmc {
    type plug
    slave.pcm "8channel_expander"
    hint {
        show on
        description "Multichannel output to both analog and hdmi - for use with XBMC"
    }
}


pcm.analog-hw {
    type hw
[B]    card 0
    device 0[/B]
}




pcm.digital-hw {
    type hw
[B]    card 1
    device 3[/B]
}


pcm.multi {
    type multi
    slaves.a.pcm "digital-hw"
    slaves.a.channels 6
    slaves.b.pcm "analog-hw"
    slaves.b.channels 2


    # digital (hdmi) bindings
    bindings.0.slave a
    bindings.0.channel 0    # bind alsa channel 0 to front left
    bindings.1.slave a
    bindings.1.channel 1    # bind alsa channel 1 to front right
    bindings.2.slave a
    bindings.2.channel 2    # bind alsa channel 2 to rear left
    bindings.3.slave a
    bindings.3.channel 3    # bind alsa channel 3 to rear right
    bindings.4.slave a
    bindings.4.channel 4    # bind alsa channel 4 to center
    bindings.5.slave a
    bindings.5.channel 5    # bind alsa channel 5 to LFE (subwoofer)


    # analog bindings
    bindings.6.slave b
    bindings.6.channel 0    # bind alsa channel 6 to front left
    bindings.7.slave b
    bindings.7.channel 1    # bind alsa channel 7 to front right
}


pcm.8channel_expander {
    type route
    slave.pcm "multi"
    slave.channels 8


    # syntax for ttable is "ttable.inputchannel.outputchannel volume"
    # digital mixing
    ttable.0.0 1    # copy front left  to front left  digital @ 100%
    ttable.1.1 1    # copy front right to front right digital @ 100%
    ttable.2.2 1    # copy rear left  to rear left  digital @ 100%
    ttable.3.3 1    # copy rear right to rear right digital @ 100%
    ttable.4.4 1    # copy center to center digital @ 100%
    ttable.5.5 1    # copy LFE (subwoofer) to LFE (subwoofer) digital @ 100%


    # analog mixing
    ttable.0.6 1    # copy front left  to front left  analog  @ 100%
    ttable.1.7 1    # copy front right to front right analog  @ 100%
    #ttable.2.6 1    # copy rear left  to front left  analog  @ 100%
    #ttable.3.7 1    # copy rear right to front right analog  @ 100%
    ttable.4.6 0.5  # copy center to front left  analog  @ 50%
    ttable.4.7 0.5  # copy center to front right analog  @ 50%


}

```

Now test soundagain, terminal:
  ```
speaker-test -t wav -c 6
``` 
**Don't forget to configure XBMC again, more info in the link.**
source & more info: [http://ehelion.net/projects/alsa/alsa.html](http://ehelion.net/projects/alsa/alsa.html)


I hope this makes a lot of people happy, it cost me over 3 weeks to completely figure this out by my self and was very happy, most of the credit has to goto the other people in the links above!
:popcorn:

---

### Post by squakie on 2014-05-20
I *think* the card and device number are dependent on how many cards there actually are - i.e., on-board versus discreet, etc..  There is a command which will show such devices - cards and devices but I am unable to locate it right now.  I just had to reload my entire system so I was waiting a couple of days before adding Ubuntu back in for dual-boot.  Guess I should do that now.  I'll post back as soon as I find that command again!

---

### Post by squakie on 2014-05-20
OK, I *think* I found it again:

cat /proc/asound/pcm

it shows leading number - the first is the card, the device is second.  So if it starts with 02-00, it's card 2 device 0.

---

### Post by richard55 on 2014-05-20
@HSKen,
Thanks for the pointers, I've been beating my head against a wall since upgrading my mythbuntu 12.04 to 14.04.
I lost my dual audio (HDMI 5.1 + Stereo Analogue for wireless headphones). Will test your solution tonight!


@squakie
```
aplay -l
```
lists all soundcards and digital devices

or 

```
aplay -L
```
lists all PCM devices (i.e. what you configure is /etc/asound.cond or ~/.asoundrc)

---

### Post by richard55 on 2014-05-21
Tested and mostly works.

Disabling pulseaudio effectively breaks alsa.

Turns out, things sprang into life when I deleted (renamed first)  ~/.pulse and reloaded alsa.

I've even adopted your asound.conf in favour of the one I used previously (it's much simpler) from [here]("http://forum.xbmc.org/showthread.php?tid=145430").

---

### Post by HSken on 2014-05-21
> **richard55 said:**
> Tested and mostly works.

Disabling pulseaudio effectively breaks alsa.

Turns out, things sprang into life when I deleted (renamed first)  ~/.pulse and reloaded alsa.



Good point, will update this in the post, you need to delete the  ~/.pulse folder or rename it if you want to backup it.

> **richard55 said:**
> I've even adopted your asound.conf in favour of the one I used previously (it's much simpler) from [here]("http://forum.xbmc.org/showthread.php?tid=145430").
I tried that one also but with no succes.

---

### Post by sikemo on 2014-08-14
I have tried the asound.conf file for dual audio from this post and ALSA does not seem to be reading it. Any ideas as to why? I have passthrough working in XBMC, but the modified dual audio version is not showing up. The file is in the /etc folder.

---

