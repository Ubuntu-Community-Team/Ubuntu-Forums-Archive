---
title: "HOWTO: Fix low surround sound on audigy 2 cards"
date: 2006-10-26
forum: Outdated Tutorials &amp; Tips
---

### Post by cyriq on 2006-10-26
Sources that i've used and that you may read for more information:
[alsa-minihowto]("http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml")
[template i used]("http://www.ubuntuforums.org/showthread.php?t=217953")

This setups Alsa for 5.1 and for audigy cards (and can work for other soundcards). What i know this works for all audigy cards. The sample rate is set to 48000 tho can be edited (however is with alsa always resampled to 48k). 
I used the notes from the template and added some of my own. I more or less putted those 2 guides above into one and tested these settings. This is also what I use tho i take no responsibility if this guide some how doesnt work or destroys something.
This more or less got all settings, and much can be removed (like 4.1 if you dont use it and such). I just want to pretty much cover most things.

Notice this guide have putted your soundcard to hw0:0. If you have several soundcards you need to find out which card is at hw0:0. To do this type into the terminal:
> aplay -l
you should get a long list with devices, your audigycard might not be in hw0:0 and if not you need to change that. Its also possible to setup alsa for several soundcards in .asounrc.

in your home folder create a file named .asoundrc and past in the text below

```

# Override the default output used by ALSA.
# If you do not override the default, your default
# device is identical to the (unmixed) analog device
# shown below.  If you prefer mixed and/or digital
# output, uncomment the appropriate four lines below
# (only one slave.pcm line).
### Currently set w/digital-hw as the default output,
### comment out this entire section to use unmixed
pcm.!default {
  type plug
## Uncomment the following to use mixed analog by default
#  slave.pcm "dmix-analog"
## Uncomment the following to use unmixed digital by default
  slave.pcm "digital-hw"
## Uncomment the following to use mixed digital by default
  #slave.pcm "dmix-digital"
}

# Alias for analog output on the Audigy (hw:0,0)
# - This is identical to the device named "default"--which
# always exists and refers to hw:0,0 (unless overridden)
# - Therefore, we can specify "hw:0,0", "default", or "analog"
# to access analog output on the Audigy
pcm.analog {
 type plug
 slave.pcm "analog-hw"
}

# Control device (mixer, etc.) for the Audigy card
ctl.analog {
 type hw
 card 0
}

# Alias for (rate-converted) mixed analog output on the
# Audigy (hw:0,0)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the dmix plugin
# (in this case 48000Hz)
pcm.mixed-analog {
 type plug
 slave.pcm "dmix-analog"
}

# Control device (mixer, etc.) for the Audigy card
ctl.mixed-analog {
 type hw
 card 0
}

# Alias for (rate-converted) digital (S/PDIF) output on the
# Audigy (hw:0,0)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the S/PDIF hardware
# (in this case 48000Hz)
pcm.digital {
 type plug
 slave.pcm "digital-hw"
}

# Control device (mixer, etc.) for the Audigy card
ctl.digital {
 type hw
 card 0
}

# Alias for mixed (rate-converted) digital (S/PDIF) output on the
# Audigy (hw:0,0)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the S/PDIF hardware
# (in this case 48000Hz)
pcm.mixed-digital {
 type plug
 slave.pcm "dmix-digital"
}

# Control device (mixer, etc.) for the Audigy card
ctl.mixed-digital {
 type hw
 card 0
}

# The following devices are not useful by themselves.  They
# require specific rates, channels, and formats.  Therefore,
# you probably do not want to use them directly.  Instead use
# of of the devices defined above.

# Alias for analog output on the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.analog-hw {
 type hw
 card 0
 # The default value for device is 0, so no need to specify
}

# Control device (mixer, etc.) for the Audigy card
ctl.analog-hw {
 type hw
 card 0
}

# Alias for digital (S/PDIF) output on the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.digital-hw {
 type hw
 card 0
 device 0
}

# Control device (mixer, etc.) for the Audigy card
ctl.digital-hw {
 type hw
 card 0
}

# Direct software mixing plugin for analog output on
# the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format. You can edit the rate to use 
# another sampe rate like 9600
pcm.dmix-analog {
 type dmix
 ipc_key 1234
 slave {
   pcm "analog-hw"
   period_time 0
   period_size 1024
   buffer_size 4096
   rate 48000
 }
}

# Control device (mixer, etc.) for the Audigy card
ctl.dmix-analog {
 type hw
 card 0
}

# Direct software mixing plugin for digital (S/PDIF) output
# on the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format. You can edit the rate to use 
# another sampe rate like 9600
pcm.dmix-digital {
 type dmix
 ipc_key 1235
 slave {
   pcm "digital-hw"
   period_time 0
   period_size 1024
   buffer_size 4096
   rate 48000
 }
}

# Control device (mixer, etc.) for the Audigy card
ctl.dmix-digital {
 type hw
 card 0
}

# setups the speakers for 5.1 and 4.1, shouldnt be needed as its already preconfigured 
# but if you got problems with the speaker setup this is needed.

pcm.ch51dup {
         slave.pcm surround51
         slave.channels 6
         type route
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 0.5
         ttable.1.4 0.5
         ttable.0.5 0.5
         ttable.1.5 0.5
}

# for 4.1 speakers
pcm.ch41dup {
         type route
         slave.pcm surround41
         slave.channels 5
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 0.5
         ttable.1.4 0.5
}
```

Now to restart alsa type in the terminal:
> sudo /etc/init.d/alsa-utils restart

and thats it.
to test type this into the terminal (5.1):
> speaker-test -c 6 -D surround51
or for 4.1:
> speaker-test -c 5 -D surround41
or for 7.1:
> speaker-test -c 8 -D surround71

 If something gets wrong delete or rename the file .asoundrc and then restart alsa and you resets your alsa mixer back to normal.
the alsa mini howto link in top of this guide also contains how to setup xmms, mplayer plug-in and gaim. It also contains how to set defualt volumes which havent been needed for me.
I also want to say thanks to the orginal authors for their guides.

---

### Post by kuleali on 2006-10-26
good guide

---

### Post by marx2k on 2006-10-30
I have an Audigy 2 with a 6.1 surround system... How do I modify this to use 6.1 instead of 5.1?

Also, I wonder if there is a GUI program that calibrates the speakers like SB releases for Windows?

---

### Post by cyriq on 2006-11-01
> **marx2k said:**
> I have an Audigy 2 with a 6.1 surround system... How do I modify this to use 6.1 instead of 5.1?

Also, I wonder if there is a GUI program that calibrates the speakers like SB releases for Windows?

I don't know of anyone that got 6.1 to work correctly under alsa as it aint supported either. 4.1, 5.1 and 7.1 is however and should be preconfigured, however i have as a very few others needed to set up the speakers in .asoundrc to 5.1 or 4.1 for some strange reason. Try searching on google, I have tho couldn't find anything to help you.

Im not aware of a gui program that calibrates the speakers as in windows. There is an alsamixer gui to set the volume for alsamixer tho what follows with ubuntu should be enough and is basicly the same either way.

---

### Post by costa_g on 2007-03-09
Hi there this seems to work really well, thanks.
[B]
One small problem[/B] I do not seem to be getting any sound from my rear right speaker, any ideas on how to fix??

---

### Post by rezpekt on 2007-06-01
Very nice. Thanks! :KS

---

### Post by marx2k on 2007-06-05
Thank you for this guide. It helped me out a great deal!

---

### Post by Anonii on 2007-06-18
That did it for my Sound Blaster Audigy LS.

---

### Post by costa_g on 2007-06-21
Just a side not, it turned out this was caused by a bend in the speaker cable, I have now replaced and all is well.

---

### Post by hfranco75 on 2007-07-15
I followed the proposed steps but it didn't work.for me in Ubuntu Feisty 7.04 AMD64. I've got an Audigy LS card, but it seems that I cannot load dmix and surround plugins together. Why?

Thanx

Hugo

---

### Post by yianniscy84 on 2007-10-06
Hello,
can you help me please?

> yiannis@yiannis-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NX [SB Audigy 2 NX], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

where is my audigy nx hw1:0 or hw0:1 or sth else.
I get this error when i follow this guide:> 
yiannis@yiannis-laptop:~$ speaker-test -c 5 -D surround41

speaker-test 1.0.13

Playback device is surround41
Stream parameters are 48000Hz, S16_LE, 5 channels
Using 16 octaves of pink noise
Broken configuration for playback: no configurations available: Invalid argument
Setting of hwparams failed: Invalid argument

---

