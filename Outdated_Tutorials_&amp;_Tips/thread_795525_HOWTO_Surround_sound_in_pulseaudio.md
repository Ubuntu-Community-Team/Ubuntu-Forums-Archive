---
title: "HOWTO: Surround sound in pulseaudio"
date: 2008-05-15
forum: Outdated Tutorials &amp; Tips
---

### Post by sammydee on 2008-05-15
[SIZE="5"][COLOR="Red"]**Update 05/11/09: Attention everyone. This guide is now OUTDATED and no longer necessary. Configuring surround sound is now ridiculously easy in Ubuntu 9.10 (Karmic) - just go into the hardware tab in sound preferences, click the device to configure, then select a surround sound profile from the drop down box. There is NO NEED to use this guide at all any more!**[/COLOR][/SIZE]





**Note: This guide has undergone a major revision. It does not suggest editing system-wide configuration files any more, and HAL based auto-detection should still work even if you do it the "hard way".**


Hi everyone.

I have an m-audio revolution 7.1 sound card and after struggling for a while to get surround sound, I thought that now I've succeeded it would be a good idea to post my experiences here. If you somehow mess up your sound following this guide, don't worry, if you followed my commands you will have taken backups. To restore these, skip to the end of the guide.

This guide assumes you actually have surround sound speakers :-) and have them all plugged into the appropriate sockets on the sound card. If you have a standard 2.1 setup, it will in 99% of cases only have one 3.5mm jack and will appear to the computer as 2.0 speakers. Following the guide in this case is probably quite a bad idea. A good rule of thumb is, if it works in windows, you have the right hardware and all the plugs are in the right places.

First things first: **PULSEAUDIO DEFAULTS TO ONLY TWO CHANNELS!**

The above is important to note before you go messing up your asoundrc or anything like that. It is probably VERY EASY to get surround sound working just by changing one config option.

First copy the system config files to your home directory, we want to change these settings on a per user basis. **If you have already modified the config files in ~/.pulse, you don't need to do this, it will erase your modified user settings.**

```
cp /etc/pulse/daemon.conf /etc/pulse/default.pa -t ~/.pulse/
```

**_[SIZE="5"]The Easy Way[/SIZE]_**

If you have one of the following combinations of speakers, you are in luck, you can do it the easy way. If you have some other combination, skip to the next section.

2.0, 4.0, 5.0, 5.1, 7.1

Simply open a terminal and do:

```
gedit ~/.pulse/daemon.conf
```

Scroll through until you find the lines that say:

```
; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2

```

Uncomment the default-sample-channels line (remove the ; symbol) and change the number to however many channels you have. If you have 5.1, change it to 6. If you have 4.0, change it to 4 etc... Save and exit.

Now restart pulseaudio (easiest way is to restart ubuntu) and bingo, surround sound should be perfectly working.

If you have a surround sound setup not listed here, you need to do it the hard way. Sorry!

**_[SIZE="5"]The Hard Way[/SIZE]_**

You will need to use this method if you have one of the following speaker configurations:

2.1, 4.1, 6.0

Or pretty much anything else that isn't listed in the easy method above.

WARNING: This method is a bit hackish and more likely to cause problems than the officially sanctioned "easy way".

_Why is it harder?_

Pulseaudio has a somewhat weird way for users to define what channels they want. There are essentially two ways of doing it as far as I can gather. The easy way is the method outlined further above, where pulseaudio allocates the number of channels you tell it to, but in a set order. The order goes:

FL, FR, RL, RR, CEN, LFE, SL, SR

So if you have a subwoofer and four speakers you're really in a bit of trouble here, because if you tell pulseaudio to use 6 channels, you get low frequency subwoofer sound, but surround sound movies send sound to a centre speaker that doesn't exist, and you don't get any voice on the front speakers. But if you tell pulseaudio that you have four channels, the subwoofer gets no sound. In this case you must define what channels to use manually.

Open a terminal and type:

```
gedit ~/.pulse/default.pa
```

Ok, skip to line 32. It's the bit that looks like:

```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
.endif

```

Now, you need to uncomment "load-module module-alsa-sink" and change it to something resembling the following:

```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)

### Manual config for configuring surround sound. Comment out line below to revert to defaults.
load-module module-alsa-sink device_id=0 channels=5 channel_map=front-left,front-right,rear-left,rear-right,lfe

#load-module module-alsa-source device=hw:1,0
.endif

```

Ok, you can see above that I have used my own manual channel configuration as an example. In my setup, I have 4.1 speakers and one sound card.

You can configure your own system by replacing my configuration line with the following template. It's important to note here that the order of these channels makes a difference. If you find that some channels are reversed, eg centre/sub is swapped with rear right/left, then you can simply change the order they are allocated to swap them back round again. Most sound cards will want these channels allocated in the usual way.

```
load-module module-alsa-sink device_id=X channels=X channel_map=x,x,x,x,x,x,x
```

[I]NOTE: One user reports:
> I have to point out only one thing: in my default.pa, when manually loading sink and source, I had to specify device=hw:0, not device=hw:0,0, nor device_id=0, otherwise I got alsa_ctl complaining about extra parameters, or surround51 unavailable (launching PA from terminal)
[/I]
[I]For reasons why this is a problem, see [this link,]("http://www.pulseaudio.org/wiki/PerfectSetup#ALSAApplications") quoted below:

> If you select the default ALSA device to be "pulse", you need to make sure that PA doesn't try to open the "default" device for its own audio output. If you previously were loading module-alsa-sink without special device argument this means you have to change it to the raw "hw:0" devices. Example:

[quote]load-module module-alsa-sink device=hw:0
load-module module-alsa-source device=hw:0

This obviously only applies to you if you have previously modified your asoundrc to make pulse your default alsa device.[/quote][/I]

[LIST]
[*]device_id - This is of course the id of your card. If you have one sound card, this is likely to be 0, but might be different if you have more than one card.
[*]channels=X - The X should be replaced by the total number of channels you wish to use
[*]channel_map=x,x,x,x,x,x,x - This is a comma separated list of values that tell pulseaudio which channels to use. It's probably a good idea to stick to the same order that pulseaudio uses (listed at the beginning of the guide) but skip out which channels you don't want. Here is an exhaustive list of valid channel names:

The currently defined channel names are: left, right, mono, center, front-left, front-right, front-center, rear-center, rear-left, rear-right, lfe, subwoofer, front-left-of-center, front-right-of-center, side-left, side-right, aux0, aux1 to aux15, top-center, top-front-left, top-front-right, top-front-center, top-rear-left, top-rear-right, top-rear-center, (Default depends on the number of channels and the driver)

It's probably best to stick to some combination of the following:

front-left, front-right, front-center, rear-center, rear-left, rear-right, lfe, side-left, side-right
[/LIST]

NOTE: If you have a subwoofer, it's almost certainly more desirable to load it as "lfe", NOT "subwoofer". "Lfe" means low frequency effects. This may seem counterintuitive, but as far as I can tell, the subwoofer channel is almost always labelled "lfe".

When you have finished, save and exit the file. You will need to restart pulseaudio for the changes to take effect. The easiest way to do this is to restart ubuntu.

[SIZE="5"]_Finished!_[/SIZE]

When you boot up, you should have surround sound on all the channels you specified, and output channels for which there is no corresponding output device should be automagically upmixed into the other speakers. Try it out with a surround sound movie or music track. If this works, well done, you've done it. Alternatively, if you have added the pulseaudio device in your asoundrc, you can use the command:

```
speaker-test -c #channels
```

Replace #channels with the number of channels you have, eg for a 5.1 channel system, put 6 here.

If you don't get surround sound, first check the channels aren't actually muted. Open a terminal and type

```
alsamixer
```

Make sure all the volumes for the channels you want are up. If your alsamixer looks like this:

[IMG]http://www.schaeben.info/alsamixer.jpg[/IMG]

You may need to try shared or independent surround, and make sure surround is unmuted. (If anyone has more information about this, I'll include it here).

*NOTE: If you have swapped channels (eg centre/sub is swapped with rear right/left) then it's pretty easy to swap these back. This is a common problem with ICH4 and ICH5 cards, and the solution is explained on page 2 of this thread.*

If you have no sound, or it's all gone horribly wrong somehow, don't panic! Open a terminal and type the following:

```
cp /etc/pulse/default.pa ~/.pulse/default.pa && cp /etc/pulse/daemon.conf ~./pulse/daemon.conf
```

Reboot ubuntu, and sound will be back how it was before.

I hope this guide was helpful! If you have problems, please post in this thread and include the contents of ~/.asoundrc, ~/.pulse/daemon.conf and ~/.pulse/default.pa. Also useful would be the result of:

```
aplay -L && aplay -l
```

You should also open a terminal and type the following:

```
pulseaudio -k && pulseaudio -vv
```

then post the output here along with your configuration files. Please post the contents of the files in a text file attachment, otherwise it makes the thread very long and unreadable, thanks! Please also bear in mind I am not a developer, just a normal user, but I've got a bit of experience with pulseaudio and I'll do my best to help.

Sam

---

### Post by chris.peplin on 2008-05-15
Thank you very much, sammydee - I hadn't found that tidbit about pulseaudio defaulting to 2 channel, which was the ticket I needed to surround sound on my Revolution 5.1. Your just saved me additional hours of headache (or maybe gave me one, since I'll be blaring music on all four speakers once again).

---

### Post by sammydee on 2008-05-16
Thanks Chris, glad I could save someone else the two days of searching it took me to figure this out :-)

I asked on the irc channel yesterday, and it appears that some time in the future this mess with the surround channels will be reolved, and sound card will be visibile in pavumeter with a list of "ports" that can be enabled and disabled at will, so you can point and click to get any combination of speakers you want. That won't be out until at least the next ubuntu release though.

---

### Post by MeURi on 2008-05-16
Good guide, sammydee :)

I only have one problem: my center and rear channels are swapped (compared to Windows), so I hear center and lfe coming out, respectively, from rear-left and rear-right. And vice versa.

Since I still need Windows, and there everything works correctly (drivers tell me to put some jacks here and there, and sound comes out from where it's supposed to come out), I just don't want to swap rear and center jacks everytime I boot into Ubuntu.

I tried to remap my channels using PA's *module-remap-sink*, but if I choose the remapped sink as output, PA dies horribly.

Do you know, by chance, how could I fix that? (I mean remapping channels, not PA :-P)

EDIT: My sound card is a Realtek ALC650, integrated into my motherboard; lspci gives
```

[m3ur1@Daemia: ~]$ lspci | grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)

```

Here's my configuration

/etc/pulse/default.pa (I removed comments)
```

.nofail

load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav

.fail

load-module module-alsa-sink device=hw:0,0 sink_name=AC97 channels=6 channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe
load-module module-remap-sink sink_name=RealtekALC650.Playback master=AC97 channels=6 master_channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe channel_map=front-left,front-right,front-center,lfe,rear-left,rear-right
load-module module-alsa-source device=hw:0,0 source_name=RealtekALC650.Capture channels=2

.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

load-module module-volume-restore

load-module module-default-device-restore

load-module module-rescue-streams

load-module module-suspend-on-idle

.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

```

/etc/pulse/daemon.conf (again I removed comments)
```

default-sample-rate = 48000
default-sample-channels = 6

```

and, finally, my /etc/asound.conf
```

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

Using paplay from the console, if I choose RealtekALC650.Playback as output sink, I get this (and then PA dies)
```

[m3ur1@Daemia: ~]$ paplay --device=RealtekALC650.Playback sample.wav
Connection failure: Connection terminated
Stream errror: Connection terminated
[m3ur1@Daemia: ~]$

```

Any ideas? :)

---

### Post by sammydee on 2008-05-16
Aside from the obvious suggestion of switching the physical jacks around and just leaving them in the wrong sockets (hey, if it works...), I'm not sure what to suggest.

I've found the #pulseaudio channel on irc.freenode.net to be helpful sometimes, however it seems to be a bit sporadic that someone actually replies to your question.

module-remap-sink documentation is [here]("http://www.pulseaudio.org/wiki/Modules") but it is pretty sparse. It's probably a good idea to leave comments in when you paste config files here, it makes it easier to read :-).

Now I haven't tried using the remap sink function yet, but to switch lfe and centre with front left and front right you used:

```
load-module module-alsa-sink device=hw:0,0 sink_name=AC97 channels=6 channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe
load-module module-remap-sink sink_name=RealtekALC650.Playback master=AC97 channels=6 master_channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe channel_map=front-left,front-right,front-center,lfe,rear-left,rear-right
load-module module-alsa-source device=hw:0,0 source_name=RealtekALC650.Capture channels=2

```

First, it might actually work if you just tell pulseaudio the channels in a different order and forget module-remap-sink:

```
#load sink
load-module module-alsa-sink device=hw:0,0 sink_name=AC97 channels=6 channel_map=front-left,front-right,front-center,lfe,rear-left,rear-right
#load source
load-module module-alsa-source device=hw:0,0 source_name=RealtekALC650.Capture channels=2
```


Failing that, I would suggest using something more like this:

```
#load sink
load-module module-alsa-sink device=hw:0,0 sink_name=AC97 channels=6 channel_map=aux0,aux1,aux2,aux3,aux4,aux5
# load virtual swapped sink
load-module module-remap-sink sink_name=RealtekALC650-Playback master=AC97 channels=6 master_channel_map=aux0,aux1,aux2,aux3,aux4,aux5 channel_map=front-left,front-right,front-center,lfe,rear-left,rear-right
# load source
load-module module-alsa-source device=hw:0,0 source_name=RealtekALC650.Capture channels=2
```

It looks a bit dirty but I think it will work. The problem I think, it that you already assigned all the channels on the first card to actual used channels, so then the virtual sink couldn't use it. I substituted aux channels in place of the real channels then remapped them with module-remap-sink.

Let me know if you have any luck.

sam

---

### Post by MeURi on 2008-05-16
Thanks for the quick reply

I created my remapped configuration looking at PA official docs (the same link you posted), yet I kept original channels name instead of aux# because I tried something more human-readable like fl,fr,rl,rr and so on, but PA failed to start (maybe I was doing something wrong elsewhere, but changing them to the original names solved the problem)

Well, using your naming suggestion didn't help, sadly (but PA starts without complaining)... I mean, the remapped sink should be ok, yet I got the same error using paplay, and PA dies (the same happens if I use any other app trying to reproduce sounds)

The main issue with exchanging jacks is that I should go under my desk every time I boot into Ubuntu, watching out for dust and cables, and then again if I reboot into Windows... I mean, it's not that pleasant :-D

I'll try to use a different channel order and see if it works, without remap-sink

Stay tuned :-)

---

### Post by MeURi on 2008-05-16
Ok, PA starts without complaining, but it still seems to me that I have swapped channels :(

Maybe it's just an impression, but if I use MPlayer and remap channels within it, it gives me a better feeling (better than Totem and VLC when playing 5.1 audio in DVDs or whatever)

I tried also doing a speaker test, but I got the following:
```

[m3ur1@Daemia: ~]$ speaker-test -Dpulse -c6 -twav

speaker-test 1.0.15

Playback device is pulse
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 43 to 349525
Period size range from 21 to 87382
Using max buffer size 349524
Periods = 4
was set period_size = 87381
was set buffer_size = 349524
*** PULSEAUDIO: Unable to create stream.
Unable to set hw params for playback: Input/output error
Setting of hwparams failed: Input/output error
speaker-test: pcm_pulse.c:115: pulse_stop: Assertion `pcm->stream' failed.
Aborted

```
:confused:

---

### Post by sammydee on 2008-05-16
I think the reversed channel order is a common problem with intel ich4 and ich5 chipsets, do you have one of these (try lspci | grep ICH)?

It is also possible that windows has it wrong - can you swap the channels round in windows?

Sam

---

### Post by MeURi on 2008-05-16
I edited my first post inserting my hardware information, but you had already replied, so I think you missed it... well, no problem

Yes, I have an ICH4 chipset, and I'm using the onboard audio controller. I hoped to get it working Windows-like with PA... maybe it's just a matter of trial-and-error before getting it to work properly

Under Windows I don't think I can swap channels, but I have to check; anyway, my 'problem' is posted here because I come from Windows (and still use it), if I tried Windows coming from Ubuntu, I'd probably say that Windows swaps my channels :)

As far as I can use MPlayer to have a 'correct' output, I don't complain too much (since I notice channel swapping only with real 5.1 audio, not with upmixed stereo); but one question arises: if the channel swapping is a common problem, why doesn't it get corrected? No flaming purpose, here, I just wonder...

Thanks for your replies

---

### Post by sammydee on 2008-05-16
It'd probably a good idea to check out the irc channel to see if they have a solution MeUri. I'll have a look now and see if I can get anything out of them.

Sam

---

### Post by MemoryDump on 2008-05-16
Hi sammydee, thanks for the great guide! :D

few questions for you: how do you determine the audio card ID?
I'm asking cause I have 2 sound cards. 1 for speakers and 1 for headset.
Perhaps you can help me out with the setup I'm trying to configure:
see this post: [http://ubuntuforums.org/showpost.php?p=4965992&postcount=61](http://ubuntuforums.org/showpost.php?p=4965992&postcount=61)
now using [nstamoul's paconfig tool]("http://ubuntuforums.org/showthread.php?t=759147") I did manage to get get both sound cards recognized in the Pulse Manager.
I have a 4.1 speaker setup too so I already added the same settings as you mentioned in your post. :)
thanks

---

### Post by sammydee on 2008-05-16
> **MeURi said:**
> I edited my first post inserting my hardware information, but you had already replied, so I think you missed it... well, no problem

Yes, I have an ICH4 chipset, and I'm using the onboard audio controller. I hoped to get it working Windows-like with PA... maybe it's just a matter of trial-and-error before getting it to work properly

Under Windows I don't think I can swap channels, but I have to check; anyway, my 'problem' is posted here because I come from Windows (and still use it), if I tried Windows coming from Ubuntu, I'd probably say that Windows swaps my channels :)

As far as I can use MPlayer to have a 'correct' output, I don't complain too much (since I notice channel swapping only with real 5.1 audio, not with upmixed stereo); but one question arises: if the channel swapping is a common problem, why doesn't it get corrected? No flaming purpose, here, I just wonder...

Thanks for your replies


Right, I have chatted with the bods on IRC and apparently I was right, you have to do it like this. This is what you had:

```
load-module module-alsa-sink device=hw:0,0 sink_name=AC97 channels=6 channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe
load-module module-remap-sink sink_name=RealtekALC650.Playback master=AC97 channels=6 master_channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe channel_map=front-left,front-right,front-center,lfe,rear-left,rear-right
load-module module-alsa-source device=hw:0,0 source_name=RealtekALC650.Capture channels=2
```

You must replace that with:

```
## load sink
load-module module-alsa-sink device=hw:0,0 sink_name=AC97 channels=6 channel_map=front-left,front-right,front-center,lfe,rear-left,rear-right
## load source
load-module module-alsa-source device=hw:0,0 source_name=RealtekALC650.Capture channels=2
```

and forget module-remap-sink completely, it isn't needed.

This SHOULD work. Let me know if it does.

Sam

---

### Post by sammydee on 2008-05-16
By the way, I find I get the best results using totem-gstreamer rather than mplayer. You can test by opening the pulseaudio volume control and muting all the output channels of the stream, then unmuting one at a time to see if it comes out of the correct speaker.

Sam

---

### Post by sammydee on 2008-05-16
> **MemoryDump said:**
> Hi sammydee, thanks for the great guide! :D

few questions for you: how do you determine the audio card ID?
I'm asking cause I have 2 sound cards. 1 for speakers and 1 for headset.
Perhaps you can help me out with the setup I'm trying to configure:
see this post: [http://ubuntuforums.org/showpost.php?p=4965992&postcount=61](http://ubuntuforums.org/showpost.php?p=4965992&postcount=61)
now using [nstamoul's paconfig tool]("http://ubuntuforums.org/showthread.php?t=759147") I did manage to get get both sound cards recognized in the Pulse Manager.
I have a 4.1 speaker setup too so I already added the same settings as you mentioned in your post. :)
thanks

If you go to the pulseaudio manager (command: paman) you can see which sound cards are available and what id_number they have.

Sam

---

### Post by MeURi on 2008-05-19
Thanks for your help, sammydee

I've been busy these days, so I haven't tried much... I promise to test thoroughly my setup in these days :-)

Anyway, one thing for sure: Windows has no easy way to swap channels

I'll let you know what I come up with

---

### Post by MeURi on 2008-05-19
Back on Ubuntu, and finally got my setup to work correctly \\:D/

Obviously, thanks to you

I have to point out only one thing: in my default.pa, when manually loading sink and source, I had to specify *device=hw:0*, not *device=hw:0,0*, nor *device_id=0*, otherwise I got alsa_ctl complaining about extra parameters, or surround51 unavailable (launching PA from terminal)

So, in the end, my default.pa looks like this
```

#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
load-module module-alsa-sink device=hw:0 sink_name=RealtekALC650.Playback channels=6 channel_map=front-left,front-right,front-center,lfe,rear-left,rear-right
load-module module-alsa-source device=hw:0 source_name=RealtekALC650.Capture channels=2
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
#.ifexists module-hal-detect.so
#load-module module-hal-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
#load-module module-detect
#.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnome-session
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Publish connection data in the X11 root window
.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

### Make some devices default
#set-default-sink output
#set-default-source input

```

As a suggestion, you could insert the channel remapping thing in your first post ;)

Thanks again, sammydee

---

### Post by Adrastos on 2008-05-21
Thanks a lot sammydee. I spent 3 days in searching how to configure the sound settings of my system so that my 4.1 speakers could work but got nothing. You have really done a great favour for everybody.
Thank you very much.

---

### Post by DoritosBR on 2008-05-22
The "Easy way" worked like a charm for me.
Thanks

---

### Post by fooman on 2008-05-22
easy way worked for me as well! 

don't know if its actual 5.1 surround, or just the same 2 channels being shared throughout...but it *is* sound and it *is* coming from all 6 speakers!  

and for this abit an8sli's onboard CK804....that is a first!  :guitar:

---

### Post by sammydee on 2008-05-23
I'm glad I've been able to help so many people, this problem was driving me up the wall when I had it.

Here is a sound file I just made that should test surround sound for you. All of the channels should say which channel they are, and the subwoofer should just boom at you. It's available on my webserver [here.]("http://137.222.225.69:8008/Multichannel%20test.flac")

I'm surprised Ubuntu doesn't come with a proper multichannel test file to be honest.

Sam

---

### Post by MeURi on 2008-05-23
You know what, sammydee?

I played you file under windows, and I got swapped channels, like I used to have under Ubuntu...

There's something wicked :-D

I should boot into Ubuntu soon, I'll let you know what happens :-)

EDIT:

Under Ubuntu, everything plays fine... (except for side channels which I do not have :-P)

Now, I don't know how it's possible, I mean: DVDs play correctly, and they have multichannel sound; moreover, they play the same under Windows and Ubuntu, so how do I get swapped channels in Windows, now? :confused:

Well, I'll take it as that, but it surely is strange

---

### Post by sammydee on 2008-05-23
Ok, I've tested it myself, and the channel order played in that flac file seems to differ depending on the media player playing it :-S

Gstreamer and mplayer play it the right way round, but winamp doesn't...? Not sure why this is.

Either way, probably best not to assume the file is correct for the moment until I have time to work out what is going on.

Sam

EDIT: Ok I'm fairly sure both mplayer AND gstreamer handle flacs badly in this respect, they both have the channel order wrong. So that flac file I specified will play fine in gstreamer and mplayer, but has a non-standard channel order so will sound reversed in windows players (which presumably follow the spec properly). I am reporting bugs to both players now. Phew that took a while to track down.

---

### Post by guyster on 2008-05-23
OK, I'm confused.  I followed this howto, and when I rebooted, I only had sound out of two channels.  When I look at pavucontrol, under the playback devices tab, it shows no sinks available, then a box for ALSA PCM on hw:0 with only two channels (front left, and front right).  I have a Sound blaster Audigy SE, and an altek Lansing 5.1 channel speaker system where the speakers plug directly into the sub.  Any help would be greatly appreciated.

Thanks,
Guy

---

### Post by sammydee on 2008-05-23
Hi guyster.

Which part of the howto did you follow, the easy way or the hard way? Have you tried the test flac file?

Sam

---

### Post by togume on 2008-05-23
Great discussion you guys have going on here.

Here's my issue. I started with the easy guide since I have an integrated Realtek850 (5.1) card. Rebooted, but nothing happened (still only sound from the front two speakers), except that when I did a sudo pactl stat it said I had 6ch...).

I then read the whole thread, and saw that MeURi had a similar card (Realtek 650), and got it working. I copied his setup, but only changed the name. Rebooted, but again, only sound from the front two.

BTW I tested this using the surround audio test (thanks for that!).

Any ideas?

Thanks,

Tomás

---

### Post by sammydee on 2008-05-23
togume (and any others with problems):

It's much easier to help you if you post your daemon.conf and default.pa files here so we can see what you have done.

Sam

---

### Post by togume on 2008-05-25
Hey Sam,

Here are my files:

daemon.conf
```
; daemonize = no
; fail = yes
; disallow-module-loading = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = -1
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; default-script-file = 

; log-target = auto
; log-level = notice

; resample-method = speex-float-3
; disable-remixing = no

; no-cpu-limit = no

; rlimit-as = -1
; rlimit-core = -1
; rlimit-data = -1
; rlimit-fsize = -1
; rlimit-nofile = 256
; rlimit-stack = -1
; rlimit-nproc = -1
; rlimit-memlock = -1
; rlimit-nice = 31
; rlimit-rtprio = 9

; default-sample-format = s16le
; default-sample-rate = 44100
default-sample-channels = 6

; default-fragments = 4
; default-fragment-size-msec = 25
```


default.pa
```
.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
#.ifexists module-hal-detect.so
#load-module module-hal-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
#load-module module-detect
#.endif

load-module module-alsa-sink device_id=0 channels=6 channel_map=front-left,front-right,front-center,rear-left,rear-right,lfe

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnome-session
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Publish connection data in the X11 root window
.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```

I'm only getting sound on my front two. My setup is 5.1 (Front L,R,C, Rear L,R, and subwoofer).

Any ideas welcome.

Thanks again,

Tomás

---

### Post by sammydee on 2008-05-26
Hi Tomas

What is the output if you start pulseaudio from the terminal? Do:

```
pulseaudio -k && pulseaudio -vv
```

Sam

---

### Post by togume on 2008-05-26
Hrm, interesting. I don't know what I'm looking at, but does not look pretty.

```
I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: alsa-util.c: Trying surround71:0...
ALSA lib setup.c:334:(snd_config_get_ctl_elem_value) bad value type
I: alsa-util.c: PCM device surround71:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround51:0...
W: alsa-util.c: Device surround51:0 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-sink.c: Successfully opened device surround51:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL surround51:0
I: alsa-util.c: Unable to attach to mixer surround51:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.surround51_0" with sample spec "s16le 6ch 48000Hz"
I: source.c: Created source 0 "alsa_output.surround51_0.monitor" with sample spec "s16le 6ch 48000Hz"
I: module-alsa-sink.c: Using 4 fragments of size 13224 bytes.
I: alsa-util.c: ALSA device lacks separate volumes control for channel 'rear-left', falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 channels=6 channel_map=front-left,front-right,front-center,lfe,side-left,side-right").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #1; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #2; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #3; argument: "").
D: module-default-device-restore.c: No previous default sink setting, ignoring.
D: module-default-device-restore.c: No previous default source setting, ignoring.
I: module.c: Loaded "module-default-device-restore" (index: #4; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #5; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.surround51_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.surround51_0.monitor becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #6; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
E: x11wrap.c: XOpenDisplay() failed
E: module.c: Failed to load  module "module-x11-publish" (argument: ""): initialization failed.
E: main.c: Module load failed.
I: main.c: Daemon startup complete.
I: module-suspend-on-idle.c: Sink alsa_output.surround51_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.surround51_0.monitor idle for too long, suspending ...

```

Thanks,

Tomás

---

### Post by MeURi on 2008-05-27
Hi Thomas

From the first lines of your output, it seems that your user is not in the *pulse-rt* group

Check that every user who needs to use audio is in the right groups, as specified [here](https://wiki.ubuntu.com/PulseAudio) in section "Adding Users to the PulseAudio groups" (assuming you're using Gnome)

See if this solves part of your issues

For the error you get while loading the *module-x11-publish*, I can't tell right now since I'm on Windows... I'll check when I reboot into Ubuntu

---

### Post by MeURi on 2008-05-27
Ok, maybe I figured out what your problem is

When you specify the *module-alsa-sink* parameters, you miss the *sink_name*, so the error (I presume) while loading the *module-x11-publish*

Your *default.pa* should then have a line like this:
```

load-module module-alsa-sink device_id=0 sink_name=RealtekALC850 channels=6 channel_map=front-left,front-right,front-center,rear-left,rear-right,lfe

```
Change the sink name to whatever you prefer

That should do it :-)

---

### Post by togume on 2008-05-28
You got me so excited; I totally though it was going to work :)!

Still the same, only stereo in the front two speakers.

Here is the output of pulseaudio -vv:

```
I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: alsa-util.c: Trying surround51:0...
W: alsa-util.c: Device surround51:0 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-sink.c: Successfully opened device surround51:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL surround51:0
I: alsa-util.c: Unable to attach to mixer surround51:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "RealtekALC850" with sample spec "s16le 6ch 48000Hz"
I: source.c: Created source 0 "RealtekALC850.monitor" with sample spec "s16le 6ch 48000Hz"
I: module-alsa-sink.c: Using 4 fragments of size 13224 bytes.
I: alsa-util.c: ALSA device lacks separate volumes control for channel 'rear-left', falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=RealtekALC850 channels=6 channel_map=front-left,front-right,front-center,rear-left,rear-right,lfe").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #1; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #2; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #3; argument: "").
D: module-default-device-restore.c: Restored default sink 'RealtekALC850'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'RealtekALC850.monitor'.
I: module.c: Loaded "module-default-device-restore" (index: #4; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #5; argument: "").
D: module-suspend-on-idle.c: Sink RealtekALC850 becomes idle.
D: module-suspend-on-idle.c: Source RealtekALC850.monitor becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #6; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
E: x11wrap.c: XOpenDisplay() failed
E: module.c: Failed to load  module "module-x11-publish" (argument: ""): initialization failed.
E: main.c: Module load failed.
I: main.c: Daemon startup complete.
I: module-suspend-on-idle.c: Sink RealtekALC850 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source RealtekALC850.monitor idle for too long, suspending ...

```

Thanks again for helping me through this!

Tomás

---

### Post by MeURi on 2008-05-28
Hi Tomás

I'm finally on Ubuntu (and I remembered to check for new posts :-P)

Here is my *pulseaudio -vv* output
```

[m3ur1@Daemia: ~]$ pulseaudio -vv 
I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: module-alsa-sink.c: Successfully opened device hw:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "RealtekALC650.Playback" with sample spec "s16le 6ch 48000Hz"
I: source.c: Created source 0 "RealtekALC650.Playback.monitor" with sample spec "s16le 6ch 48000Hz"
I: module-alsa-sink.c: Using 4 fragments of size 14388 bytes.
I: alsa-util.c: ALSA device lacks separate volumes control for channel 'front-center', falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device=hw:0 sink_name=RealtekALC650.Playback channels=6 channel_map=front-left,front-right,front-center,lfe,rear-left,rear-right").
I: module-alsa-source.c: Successfully opened device hw:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "RealtekALC650.Capture" with sample spec "s16le 2ch 48000Hz"
I: module-alsa-source.c: Using 4 fragments of size 4796 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device=hw:0 source_name=RealtekALC650.Capture channels=2").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #2; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #3; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #4; argument: "").
D: module-default-device-restore.c: Restored default sink 'RealtekALC650.Playback'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'RealtekALC650.Capture'.
I: module.c: Loaded "module-default-device-restore" (index: #5; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #6; argument: "").
D: module-suspend-on-idle.c: Sink RealtekALC650.Playback becomes idle.
D: module-suspend-on-idle.c: Source RealtekALC650.Playback.monitor becomes idle.
D: module-suspend-on-idle.c: Source RealtekALC650.Capture becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
D: module-gconf.c: Loading module 'module-combine' with args '' due to GConf configuration.
I: sink.c: Created sink 1 "combined" with sample spec "s16le 6ch 48000Hz"
I: source.c: Created source 2 "combined.monitor" with sample spec "s16le 6ch 48000Hz"
D: memblockq.c: memblockq requested: maxlength=174080, tlength=174080, base=12, prebuf=1, minreq=0
D: memblockq.c: memblockq sanitized: maxlength=174084, tlength=174084, base=12, prebuf=12, minreq=12
D: module-suspend-on-idle.c: Sink RealtekALC650.Playback becomes busy.
D: resampler.c: Channel matrix:
D: resampler.c:        I00   I01   I02   I03   I04   I05 
D: resampler.c:     +------------------------------------
D: resampler.c: O00 | 1.000 0.000 0.000 0.000 0.000 0.000
D: resampler.c: O01 | 0.000 0.000 0.000 1.000 0.000 0.000
D: resampler.c: O02 | 0.000 0.000 1.000 0.000 0.000 0.000
D: resampler.c: O03 | 0.000 0.000 0.000 0.000 0.000 1.000
D: resampler.c: O04 | 0.500 0.500 0.000 0.000 0.000 0.000
D: resampler.c: O05 | 0.000 0.000 0.000 0.500 0.500 0.000
I: resampler.c: Using resampler 'trivial'
I: resampler.c: Using s16le as working format.
I: sink-input.c: Created input 0 "Simultaneous output on ALSA PCM on hw:0 (Intel 82801DB-ICH4) via DMA" on RealtekALC650.Playback with sample spec s16le 6ch 48000Hz and channel map front-left,side-left,front-center,front-right,side-right,lfe
I: module-combine.c: Master sink is now 'RealtekALC650.Playback'
D: module-combine.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
D: module-suspend-on-idle.c: Source combined.monitor becomes idle.
D: module-suspend-on-idle.c: Sink combined becomes idle.
I: module.c: Loaded "module-combine" (index: #8; argument: "").
I: module.c: Loaded "module-gconf" (index: #9; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #10; argument: "").
I: main.c: Daemon startup complete.
I: module-suspend-on-idle.c: Source RealtekALC650.Capture idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source RealtekALC650.Playback.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink combined idle for too long, suspending ...
D: module-suspend-on-idle.c: Sink RealtekALC650.Playback becomes idle.
D: module-suspend-on-idle.c: Sink RealtekALC650.Playback becomes idle.
I: sink-input.c: Freeing output 0 "Simultaneous output on ALSA PCM on hw:0 (Intel 82801DB-ICH4) via DMA"
I: module-combine.c: No master selected, lacking suitable outputs.
I: module-combine.c: Device suspended...
I: module-suspend-on-idle.c: Source combined.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink RealtekALC650.Playback idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...

```

So, I got no errors...

One thing I can think of is */etc/asound.conf*; mine looks like this
```

[m3ur1@Daemia: ~]$ cat /etc/asound.conf 
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

I created this file following what is written [here](http://pulseaudio.org/wiki/PerfectSetup#ALSAApplications)

And this could fix your problems related to surround51 not available

Then you get that evil "E: x11wrap.c: XOpenDisplay() failed", but I actually have no clue about that, since I don't have that error

I start PulseAudio with Gnome, using esdcompat, as specified [here](http://pulseaudio.org/wiki/PerfectSetup#GNOME) (mind that the correct path is */usr/bin/esdcompat*); and you have to enable ESD in Gnome sound preferences, of course (in the Devices section I have every playback device set up to use PulseAudio, also)

You can install that by issuing a *sudo apt-get install pulseaudio-esound-compat* from the terminal

Hope it helps :-)

---

### Post by sammydee on 2008-05-28
togume:

Before trying anything else, and possibly making the problem even worse, I would recommend asking on the IRC channel first for advice. It is #pulseaudio on irc.freenode.net.

sam

---

### Post by MeURi on 2008-05-28
I think I figured out what the problem is ^.^

This afternoon I decided to play with Ubuntu, and came up with a disaster... so I reformatted (way too windows-ish approach, I know...)

Well, I set up my system to use PulseAudio using my backed up files, and I got sound only from the front speakers!

Something familiar, some would say...

Then I started playing around, and I noticed that something was still getting between me and my perfect surround setup :-P

So, in the end, this is how I solved it:
[LIST]
[*]open *gnome-volume-control* from the terminal, or from the applet in the panel
[*] under Preferences, I enabled everything; what I really needed were just Surround, Surround Jack Mode, Center, LFE, Channel Mode, Duplicate Front
[*] in the Playback tab, I unmuted and raised the volumes of the sections I needed
[*] in the Switches tab, I enabled the Duplicate Front thing
[*] finally, in the Options tab, I set the Surround Jack Mode to Shared (this is correct with my ICH4 integrated card, may change for others), and set the Channel Mode to 6ch
[/LIST]
Then I was back with my beautiful surround sound, even for 2-channels streams :mrgreen:\\:D/

Could be the same issue togume is experiencing...

Hope it solves that :-)

EDIT:

I forgot togume has also some errors launching PulseAudio... my procedure could be a good check, though

---

### Post by togume on 2008-05-29
lol. I think I've tied myself in a knot now. Fortunately I have backups of everything.

If this is what I have to go through to get my last home pc (HTPC) off Windows, so be it!

So, MeURi, I tried what you suggested, and enabled all the settings using gnome-volume-control. I played the test file, and I got sound from my two REAR speakers! Huge win. However, neither the center nor lfe worked...

Out of curiosity, I decided which of all the changes was the one that made it work, and I first started setting everything back to zeroes (default config before all this started). Upon rebooting PA, and to my surprise, I now had front left, front right, and center. Interestingly enough, with rear L&R, side L&R, and LFE, the front speakers would reproduce the sound very lightly.

I also tried manually mapping the channels, and that again gave me 4 channels. However, it seems the order is not important.

I'm now getting a much different output from pulseaudio -v without errors.

I'm currently waiting for the IRC people to be available. It seems I need to catch them at better times...

Thanks for all your help again,

Tomás

---

### Post by MeURi on 2008-05-29
Glad you got rid of your errors

Yet, I think that channel order IS important (otherwise I could not have remapped my channels); maybe your 7.1 channels are mapped by default in a different way (so maybe you got side speakers coming out from front)... but I'm just guessing

Anyway, I found out that duplicating front channel with gnome-volume-control is not mandatory, whereas it is mandatory to enable all the channels you plan to use

I'm still having issues with VLC and DVDs, though... only stereo upmixed :-?

I'm gonna investigate :-)

---

### Post by sammydee on 2008-05-29
MeUri:

I have never managed to get vlc to output surround sound in pulseaudio on linux. Try using mplayer or gstreamer (totem) instead.

Also, for anybody having problems with only a few channels playing, do check that they are unmuted in alsamixer. Alsa likes to mute channels by default :-). gnome-volume-control is actually just a frontend for alsamixer I think.

It is unnecessary to duplicate any channels at all in gnome-volume-control, pulseaudio handles it all automagically.

Sam

Togume: Restore all the backups and start again, reset all the settings in gnome-volume-control. Follow the guide from the beginning again, also following the newly added section about alsamixer, as I think that your problem is a lot simpler than you think.

---

### Post by MeURi on 2008-05-29
Sam:

I was just thinking about sticking to Totem :-)
VLC 0.9 doesn't work either with PA, so I'm givin' up (for now)

About the gnome-volume-control thing, I used that because alsamixer doesn't work like it used to when I had only ALSA: it shows me only 4 master channels (yep, all of them) for playback, and one master for capture, so I could not change channel mode and other things

Apart from that, everything works great :-)

Hope that togume fixes his problems, starting over (and besides, everyone who has issues)

---

### Post by togume on 2008-05-29
I will be starting over tonight and following the guide after work, and squash, and dinner :).

Will report back...

---

### Post by s_spiff on 2008-05-30
I have a doubt here. The whole how to seems to be based on the fact that each of those surround sound speakers enter a port on the back side of the cpu. 
In my case, I have a Creative 4.1 speaker set, where only two jacks enter the CPU ( which are connected to the sub-woofer) and the 4 smaller speakers have their input coming from from the subwoofer. So does this how-to work for me?

---

### Post by MeURi on 2008-05-30
Hi, s_spiff

I have a Creative Inspire T6060 5.1 Speaker System; subwoofer has 3 jacks connected to the sound card, and every speaker connects to the subwoofer

If that was your concern, I assure you that you won't have any problem :-)

Note: I don't think your jacks are connected to the CPU... maybe you meant your pc case ;-)

---

### Post by mrth on 2008-05-31
> **MeURi said:**
> Glad you got rid of your errors

I'm still having issues with VLC and DVDs, though... only stereo upmixed :-?

I'm gonna investigate :-)

Hi
as I know vlc pulseaudio plugin does not have implemented support for any thing else than stereo. I should be easy to implement it.

---

### Post by MeURi on 2008-06-03
I could have the skills to implement that (optimistic view :-)), but sure I don't have the time, right now :-P

---

### Post by togume on 2008-06-04
Reporting back. I have achieved success. 

I rolled everything back, and then the only thing I modified was the daemon.conf. Reloaded PA, and still the same issue. I had front, center, and sub...

I then opened up alsamixer, and played around with all the permutations I could think of. Finally, all it took was to select the surround mode as not "shared" (sorry, not in front of my HTPC, I'll have to double check).

After I made this change, I had full 5.1. Perfect.

All is well now :).

Thanks for the support; this is why we love Linux.

Tomás

---

### Post by MeURi on 2008-06-04
Glad you solved it ^.^

---

### Post by sammydee on 2008-06-04
> **togume said:**
> Reporting back. I have achieved success. 

I rolled everything back, and then the only thing I modified was the daemon.conf. Reloaded PA, and still the same issue. I had front, center, and sub...

I then opened up alsamixer, and played around with all the permutations I could think of. Finally, all it took was to select the surround mode as not "shared" (sorry, not in front of my HTPC, I'll have to double check).

Where did you see this option for surround sound mode? In alsamixer?

Can you let me know so I can put it in the howto?

Sam

---

### Post by MeURi on 2008-06-05
Yep, Sam, it's in alsamixer (or gnome-volume-control, under *Switches*)

I had to specify "shared", while Tomás had to specify "independent"; so it depends on the hardware, from what I can tell

---

### Post by MemoryDump on 2008-06-05
moved..

---

### Post by sammydee on 2008-06-05
MemoryDump:

That sort of usage of pulseaudio is way out of the scope of this guide - I haven't got the foggiest on how to help you I'm afraid :-)

For that sort of thing, you will probably have better luck asking on IRC, or possibly starting a new thread.

Sam

---

### Post by MemoryDump on 2008-06-05
> **sammydee said:**
> MemoryDump:

That sort of usage of pulseaudio is way out of the scope of this guide - I haven't got the foggiest on how to help you I'm afraid :-)

For that sort of thing, you will probably have better luck asking on IRC, or possibly starting a new thread.

Sam
Thanks Sam! I'll start a new post.. thanks :)

---

### Post by neymac on 2008-06-05
I did the easy way and for test I did

```
speaker-test -Dplug:surround51 -c6 -l1 -twav
```

and worked all the six channels.

---

### Post by parthibanbls on 2008-06-05
Hi,
   I have an **NVidia 7.1 Sound Card** and a **2.1 Speaker System**. I'm able to get **sound on only one speaker** (and the subwoofer works). 

I tried changing the channel_map in /etc/pulse/default.pa but haven't been able to get any sound on the other speaker.

Changing the channel_map from 'left,right' to 'right,left' outputs the other channel (previously missing) on the same speaker. So, basically I've been able to get both channels (not at the same time) on one speaker, while nothing comes out of the other speaker.

Tested the speakers on a windows laptop and they worked fine.

Any help is greatly appreciated.

Thanks,
Partho.

---

### Post by parthibanbls on 2008-06-05
> Hi,
I have an NVidia 7.1 Sound Card and a 2.1 Speaker System. I'm able to get sound on only one speaker (and the subwoofer works).

I tried changing the channel_map in /etc/pulse/default.pa but haven't been able to get any sound on the other speaker.

Changing the channel_map from 'left,right' to 'right,left' outputs the other channel (previously missing) on the same speaker. So, basically I've been able to get both channels (not at the same time) on one speaker, while nothing comes out of the other speaker.

Tested the speakers on a windows laptop and they worked fine.

Any help is greatly appreciated.

Thanks,
Partho.


**Here's what I changed in default.pa**

[I]### Automatically load driver modules depending on the hardware available
#.ifexists module-hal-detect.so
#load-module module-hal-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
#load-module module-detect
#.endif

### Load manual channel config. Uncomment the above and recomment the below to go back to defaults.

load-module module-alsa-sink device=hw:0 channels=2 channel_map=left,right
[/I]

Setting channels=3 made pulseaudio fail to load.

**aplay -L** gave:

[I]front:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
[/I]

---

### Post by sammydee on 2008-06-06
parthibanbls:

Has your sound ever worked in stereo?

This thread is really meant to specifically help people with more than two speakers get surround sound working. If pulseaudio doesn't even work in standard stereo mode, I think you probably need to make a new thread - that's a completely different problem. (Note: My sound card outputs only on one channel sometimes on startup, it is solved by changing just one volume in alsamixer - I think it's some sort of stupid bug).

I think some confusion may be arising here - if you have a standard 2.1 setup, you DON'T need this guide. This guide is only useful for people with at least four speakers. The standard 2.1 speaker sets that you get only have ONE stereo input jack - they can't accept more than two channels at all, even in windows!

Sam

---

### Post by sammydee on 2008-06-06
> **neymac said:**
> I did the easy way and for test I did

```
speaker-test -Dplug:surround51 -c6 -l1 -twav
```

and worked all the six channels.

neymac - I think that command tests surround sound with alsa rather than pulseaudio specifically, that's why I didn't recommend it in the guide. Believe it or not, there are scenarios where alsa will not work with surround sound but pulseaudio will. Actually this is the case in my setup - I access my 7.1 sound card across the network from another computer most of the time, but alsa only has access to the local two channel sound card.

It's a better idea for most people to use the flac test file (unfortunately I had to give it non-standard channel mapping to force gstreamer to play it properly, but that's gstreamer being non-standard, so that file won't play properly on flac decoders that use standards-compliant channel mapping ie winamp or foobar2000 on windows.)

Sam

---

### Post by parthibanbls on 2008-06-06
hi sammydee,
   Thanks for the reply. 

I know I only have a 2.1 speaker setup, but it seems like the problem is due to the sound card being 7.1. And that pulseaudio is not sending sound over the correct channels (out of the eight available).

I think the problem can be solved if I can there's a way to find which of the 8 channels are played by my 2.1 speakers, and have pulseaudio choose those channels.
Is there a way to find that?

I tried 'speaker-test -c8' (with pulseaudio shut down) but that too produced sound on only one speaker.

Thanks,
Partho.

---

### Post by sammydee on 2008-06-06
parthinabls:

Hmm if sound isn't working even in stereo that's a fairly major problem - if I was you I'd start a new thread with that, or ask on irc. This guide is really to help people get surround sound working once they already have stereo - you'll get more and better help if you ask on another thread I think. See if a search turns up anybody else with a similar card.

sam

---

### Post by neymac on 2008-06-06
I used the flac test file with totem-gstreamer and all speakers worked.
But with mplayer there was no sound when I select pulseaudio as audio output (mplayer -ao pulse Multichannel_test_flac_nonstandard_8.flac).
Is there any way to allow mplayer to play pulse?
There is a "pulse" option when I select preferences in mplayer, but if I select it => no sound.
By the way, at the terminal it looks like the file was playing (no error message), but no sound.

---

### Post by sammydee on 2008-06-07
neymac: This looks like a problem with mplayer, not a problem with pulseaudio afaik. I use smplayer as a frontend - set the channels to 5.1 and it works great for me.

Sam

---

### Post by neymac on 2008-06-07
> **sammydee said:**
> neymac: This looks like a problem with mplayer, not a problem with pulseaudio afaik. I use smplayer as a frontend - set the channels to 5.1 and it works great for me.

Sam
Thanks, sammydee.
Pulse audio was sending the mplayer sound to the on board sound card and the totem sound to another sound card. I changed the default sink using pulseaudio manager and now I got 5.1 sound everywhere.

---

### Post by s_spiff on 2008-06-22
ok this has pretty much worked. Only issue is, out of the 4 speakers and 1 subwoofer, one speaker doesn't produce an output.. which is the left rear one. Any idea why? i've put in the same config as the one provided on the first page howto.

---

### Post by hakanka on 2008-06-22
sammydee thank you very much, it solved my problem.

Now the sound i get much better then windows.

Thanks thanks thanks..

---

### Post by atz on 2008-06-22
Thanks alot this really solved it for me :) .

---

### Post by sammydee on 2008-06-22
> **s_spiff said:**
> ok this has pretty much worked. Only issue is, out of the 4 speakers and 1 subwoofer, one speaker doesn't produce an output.. which is the left rear one. Any idea why? i've put in the same config as the one provided on the first page howto.

spiff:

Ok, what sound card are you using. Can you please post your /etc/pulse/default.pa and /etc/pulse/daemon.conf here?

What sounds are you using to test it and how are you playing them?

Sam

---

### Post by s_spiff on 2008-06-22
the default.pa output :

> 
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
#.ifexists module-hal-detect.so
#load-module module-hal-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
#load-module module-detect
#.endif

### Load manual channel config. Uncomment the above and recomment the below to go back to defaults.
load-module module-alsa-sink device_id=0 channels=5 channel_map=front-left,front-right,rear-left,rear-right,lfe

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnome-session
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Publish connection data in the X11 root window
.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

### Make some devices default
#set-default-sink output
#set-default-source input

tje daemon.conf output ::

> 
# $Id: daemon.conf.in 2175 2008-03-27 23:39:10Z lennart $
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; disallow-module-loading = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = -1
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; default-script-file = 

; log-target = auto
; log-level = notice

; resample-method = speex-float-3
; disable-remixing = no

; no-cpu-limit = no

; rlimit-as = -1
; rlimit-core = -1
; rlimit-data = -1
; rlimit-fsize = -1
; rlimit-nofile = 256
; rlimit-stack = -1
; rlimit-nproc = -1
; rlimit-memlock = -1
; rlimit-nice = 31
; rlimit-rtprio = 9

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2

; default-fragments = 4
; default-fragment-size-msec = 25


umm.. dunno what soundcard i'm using. the onboard 6 channel one. i got a a gigabyte motherboard with nvidia chipset.

---

### Post by s_spiff on 2008-06-30
*bump*

---

### Post by sammydee on 2008-07-01
Well I can't see anything wrong with your config files. I recommend asking on IRC on #pulseaudio for help.

I do recall reading that some very old alsa drivers had issues with the left rear channel but not sure if that relates to your problem...

Sam

---

### Post by jerome1232 on 2008-07-16
Okay so this works for me except that:

pulseaudio crashes about 10 - 20 minutes after log in leaving all audio programs hanging/crashed.

I have noticed this message in my user.log files
```
Jul 14 16:00:10 ubuntu pulseaudio[5910]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
```

this is on a Sound Blaster Audigy 2 ZS which does in fact support 5.1 surround sound, pulse audio doesn't exhibit this behavior when changed back to 2 channels.

this is /etc/pulse/daemon.conf
```
# $Id: daemon.conf.in 2175 2008-03-27 23:39:10Z lennart $
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; disallow-module-loading = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = -1
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; default-script-file = 

; log-target = auto
; log-level = notice

; resample-method = speex-float-3
; disable-remixing = no

; no-cpu-limit = no

; rlimit-as = -1
; rlimit-core = -1
; rlimit-data = -1
; rlimit-fsize = -1
; rlimit-nofile = 256
; rlimit-stack = -1
; rlimit-nproc = -1
; rlimit-memlock = -1
; rlimit-nice = 31
; rlimit-rtprio = 9

; default-sample-format = s16le
; default-sample-rate = 44100
default-sample-channels = 6

; default-fragments = 4
; default-fragment-size-msec = 25
```

this is /etc/pulse/default.pa
```
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnome-session
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Publish connection data in the X11 root window
.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```

any thoughts would be appreciated

---

### Post by sammydee on 2008-07-18
Looks like an alsa bug, the creative cards are notoriously badly supported because they refuse to release specs or decent drivers. Either way it's far beyond my knowledge to help you, I suggest #pulseaudio or #alsa on irc.freenode.net, or you could submit a bug report on the [pulseaudio website]("http://pulseaudio.org").

---

### Post by matthewbpt on 2008-07-18
hey all!
I want to get an external sound card connected via usb for my laptop to use with 5.1 speakers. Would an external sound card work with the setup on this thread? and if so can you recommend one that is known to work?
Great guide btw, even though I haven't tested it out yet it all seems pretty well explained, good job!

Matt

---

### Post by sammydee on 2008-07-19
I'm sure an external sound card would work fine. As for specific recommendations, this is the wrong place to ask. Try the alsa wiki or #alsa on irc.freenode.net. Or google it?

Sam

---

### Post by alphahour on 2008-07-20
Hi

I've done the steps written in this how to but I still get 2.0 sound.

Here is the content of my files:

daemon.conf:

> # $Id: daemon.conf.in 2175 2008-03-27 23:39:10Z lennart $
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; disallow-module-loading = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = -1
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; default-script-file = 

; log-target = auto
; log-level = notice

; resample-method = speex-float-3
; disable-remixing = no

; no-cpu-limit = no

; rlimit-as = -1
; rlimit-core = -1
; rlimit-data = -1
; rlimit-fsize = -1
; rlimit-nofile = 256
; rlimit-stack = -1
; rlimit-nproc = -1
; rlimit-memlock = -1
; rlimit-nice = 31
; rlimit-rtprio = 9

; default-sample-format = s16le
; default-sample-rate = 44100
 default-sample-channels = 6

; default-fragments = 4
; default-fragment-size-msec = 25


default.pa:

> #!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
#.ifexists module-hal-detect.so
#load-module module-hal-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
#load-module module-detect
#.endif

### Load manual channel config. Uncomment the above and recomment the below to go back to defaults.

load-module module-alsa-sink device_id=0 channels=6 channel_map=front-left,front-center,front-right,rear-left,rear-right,lfe


### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnome-session
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Publish connection data in the X11 root window
.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

### Make some devices default
#set-default-sink output
#set-default-source input

My sound card is on board and the chipset is the ALC650D.

I'm using Ubuntu Studio (8.04).

Can you help me please?

Thanks in advance.
André.

---

### Post by sammydee on 2008-07-21
Andre:

Open a terminal and type:

```
pulseaudio -k && pulseaudio -vv
```

What does it say?

Sam

---

### Post by alphahour on 2008-07-21
It says this:

> **andre@andre:~$ pulseaudio -k && pulseaudio -vv**
I: main.c: Called SUID root and real-time/high-priority scheduling was reque
 in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us p
liges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate 
cyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_N
RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally requ
. If you experience crackling or other sound anomalies, consider one or more
the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed
policy. Disabling forcibly.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operação não permitida
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: alsa-util.c: Trying surround51:0...
I: module-alsa-sink.c: Successfully opened device surround51:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909: (snd_ctl_open_noupdate) Invalid CTL surround51:0
I: alsa-util.c: Unable to attach to mixer surround51:0: Ficheiro ou director
nexistente
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.surround51_0" with sample spec "s16le
 44100Hz"
I: source.c: Created source 0 "alsa_output.surround51_0.monitor" with sample
c "s16le 6ch 44100Hz"
I: module-alsa-sink.c: Using 4 fragments of size 13224 bytes.
I: alsa-util.c: ALSA device lacks separate volumes control for channel 'rear
t', falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 ch
ls=6 channel_map=front-left,front-center,front-right,rear-left,rear-right,lf
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/modu
sound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #1; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #2; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #3; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.surro
1_0'.
D: module-default-device-restore.c: No previous default source setting, igno
.
I: module.c: Loaded "module-default-device-restore" (index: #4; argument: ""
I: module.c: Loaded "module-rescue-streams" (index: #5; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.surround51_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.surround51_0.monitor becomes
e.
I: module.c: Loaded "module-suspend-on-idle" (index: #6; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/modu
conf.so': success
I: module.c: Loaded "module-gconf" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/modu
11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #8; argument: "").
I: main.c: Daemon startup complete.
I: module-suspend-on-idle.c: Sink alsa_output.surround51_0 idle for too long
spending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.surround51_0.monitor idle fo
o long, suspending ...
I: client.c: Created 0 "EsounD client (UNIX socket client)"
I: client.c: Created 1 "EsounD client (UNIX socket client)"

and it just stops (I think) at that line.

---

### Post by sammydee on 2008-07-22
Try renaming this line in your default.pa:

load-module module-alsa-sink device_id=0 channels=6 channel_map=front-left,front-center,front-right,rear-left,rear-right,lfe

to:

load-module module-alsa-sink device_id=hw:0 channels=6 channel_map=front-left,front-center,front-right,rear-left,rear-right,lfe

---

### Post by MeURi on 2008-07-25
Alphahour, you should also add your running user to the groups *pulse-access* and *pulse-rt*, and maybe even to *pulse* (I don't remember properly if the latter was needed)

Bye

---

### Post by alphahour on 2008-08-10
sorry for the late reply but I had problems with my external drive so these last weeks I was mostly concerned about recovering data and I forgot this 5.1 issue.

I tried the last two suggestions but nothing happen. I keep having the 2 channel system :s

Is there anything more I can try?

thanks again.
André.

---

### Post by sammydee on 2008-08-10
alphahour: Meuri's suggestion won't help, that just allows pulseaudio to run with realtime privileges.

I'm out of suggestions. Ask on irc, that's where the people that really know what's going on hang out. Or you could try the mailing list.

Sam

---

### Post by alphahour on 2008-08-10
ok. thanks anyway sammydee ;)

---

### Post by dageng1 on 2008-08-10
This is my audio controller, it's the onboard one on the Asus P5Q-E:
[QUOTE="lspci | grep Audio"]00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller[/QUOTE]

This is the only line I changed in this file (the only line that isn't commented out):
[QUOTE="/etc/pulse/daemon.conf"]default-sample-channels = 6[/QUOTE]

My two front speakers work, but I'm unable to get my center, sub and the two rear ones to work.

When I run alsamixer I don't see any extra channels, I'm only able to change the volume of the "Master", "PCM" and "Digital".

I've tried both the methods, and none of them worked. I'm running a 5.1 system, and yes, surround works in Windows XP.

This is the 64 bit version of Ubuntu Hardy Heron.

Ps. Apparently my post was too long, so I've included the "pulseaudio -k && pulseaudio -vv" content, in a file. Hope that's okay with everyone.

Thanks in advance!

---

### Post by b-george on 2008-08-11
Hello friends, last time i used ubuntu was for 2 years ago and now i'm back to the 8.04 this version rocks:guitar: i'm pleased with it. I have problem with my speakers i only get sound from the two front speakers.

> I have 5.1 speakers

> Card: Intel ICH5                                                             &#9474;
&#9474; Chip: Analog Devices AD1980                                                  &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00, 0.00]

default.pa

> #!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnome-session
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Publish connection data in the X11 root window
.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

### Make some devices default
#set-default-sink output
#set-default-source input

daemon.conf

> # $Id: daemon.conf.in 2175 2008-03-27 23:39:10Z lennart $
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; disallow-module-loading = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = -1
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; default-script-file = 

; log-target = auto
; log-level = notice

; resample-method = speex-float-3
; disable-remixing = no

; no-cpu-limit = no

; rlimit-as = -1
; rlimit-core = -1
; rlimit-data = -1
; rlimit-fsize = -1
; rlimit-nofile = 256
; rlimit-stack = -1
; rlimit-nproc = -1
; rlimit-memlock = -1
; rlimit-nice = 31
; rlimit-rtprio = 9

; default-sample-format = s16le
; default-sample-rate = 44100
 default-sample-channels = 6

; default-fragments = 4
; default-fragment-size-msec = 25

pulseaudio -k && pulseaudio -vv

> I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operationen inte tillåten
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operationen inte tillåten
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_24d5_sound_card_0_alsa_playback_4
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_24d5_sound_card_0_alsa_capture_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_24d5_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_24d5_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying surround51:0...
I: module-alsa-sink.c: Successfully opened device surround51:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL surround51:0
I: alsa-util.c: Unable to attach to mixer surround51:0: Filen eller katalogen finns inte
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0" with sample spec "s16le 6ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 6ch 44100Hz"
I: module-alsa-sink.c: Using 4 fragments of size 13224 bytes.
I: alsa-util.c: ALSA device lacks separate volumes control for channel 'rear-left', falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying surround51:0...
I: alsa-util.c: PCM device surround51:0 refused our hw parameters: Ogiltigt argument
D: alsa-util.c: Trying surround71:0...
ALSA lib conf.c:3952:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM surround71:0
I: alsa-util.c: Couldn't open PCM device surround71:0: Ogiltigt argument
D: alsa-util.c: Trying surround50:0...
I: alsa-util.c: PCM device surround50:0 refused our hw parameters: Ogiltigt argument
D: alsa-util.c: Trying surround41:0...
I: alsa-util.c: PCM device surround41:0 refused our hw parameters: Ogiltigt argument
D: alsa-util.c: Trying surround40:0...
I: alsa-util.c: PCM device surround40:0 refused our hw parameters: Ogiltigt argument
D: alsa-util.c: Trying front:0...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: Filen eller katalogen finns inte
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 4 fragments of size 4408 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_24d5_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #5; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0'.
D: module-default-device-restore.c: No previous default source setting, ignoring.
I: module.c: Loaded "module-default-device-restore" (index: #6; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #7; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #8; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #9; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #10; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...



when i play music file and movies i get sound from all 5.1 speakers. 
when i watch flash videos i only get sound from my 2 front speakers.

when i play this file 
> speaker-test -c 6

it comes only from my two front speakers.

all the sound is unmuted from alsanixer...


please help:(

---

### Post by sammydee on 2008-08-12
> **dageng1 said:**
> This is my audio controller, it's the onboard one on the Asus P5Q-E:


This is the only line I changed in this file (the only line that isn't commented out):


My two front speakers work, but I'm unable to get my center, sub and the two rear ones to work.

When I run alsamixer I don't see any extra channels, I'm only able to change the volume of the "Master", "PCM" and "Digital".

I've tried both the methods, and none of them worked. I'm running a 5.1 system, and yes, surround works in Windows XP.

This is the 64 bit version of Ubuntu Hardy Heron.

Ps. Apparently my post was too long, so I've included the "pulseaudio -k && pulseaudio -vv" content, in a file. Hope that's okay with everyone.

Thanks in advance!

I had a good look at the text file and it looks like alsa is not exposing more than two channels to pulseaudio for whatever reason.

I have no idea why this is, it could be incomplete alsa drivers (is your computer very new?) or a bug. Either way, the best place to report this is the pulseaudio bug tracker, the devs there should point you in the right direction if it is an alsa problem.

Sam

---

### Post by sammydee on 2008-08-12
> **b-george said:**
> Hello friends, last time i used ubuntu was for 2 years ago and now i'm back to the 8.04 this version rocks:guitar: i'm pleased with it. I have problem with my speakers i only get sound from the two front speakers.

when i play music file and movies i get sound from all 5.1 speakers. 
when i watch flash videos i only get sound from my 2 front speakers.

when i play this file 


it comes only from my two front speakers.

all the sound is unmuted from alsanixer...


please help:(

Hi George.

This is actually working perfectly. All pulseaudio applications are fully 5.1 capable as they should be. The reason the sound test and flash are only two channels is because they are using alsa, which is directly accessing the sound card in it's own way. If you REALLY want alsa aware applications like flash to work as well, you need to follow part A in [this guide]("http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+fix").

Be advised that I don't think this is an ideal solution for a number of reasons. If I were you I'd leave it the way it is. All music and movies will work find, only flash and very few other applications that are not pulseaudio aware will only use two channels.

There is a third option, which involves editing ~/.asoundrc. I can't help with this, you need to get on the #alsa irc channel and get a guru to help you if you want to expose 5.1 surround sound directly to alsa aware applications.

Sam

---

### Post by b-george on 2008-08-12
> **sammydee said:**
> Hi George.

This is actually working perfectly. All pulseaudio applications are fully 5.1 capable as they should be. The reason the sound test and flash are only two channels is because they are using alsa, which is directly accessing the sound card in it's own way. If you REALLY want alsa aware applications like flash to work as well, you need to follow part A in [this guide]("http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+fix").

Be advised that I don't think this is an ideal solution for a number of reasons. If I were you I'd leave it the way it is. All music and movies will work find, only flash and very few other applications that are not pulseaudio aware will only use two channels.

There is a third option, which involves editing ~/.asoundrc. I can't help with this, you need to get on the #alsa irc channel and get a guru to help you if you want to expose 5.1 surround sound directly to alsa aware applications.

Sam

thank u sam!

it's not necessary i will leave it like it's. thanks for the great support.

//George

---

### Post by dageng1 on 2008-08-12
Thanks Sam!
From what I know the SoundMAX Audio chip on my motherboard is fairly new, so it's probably incomplete ALSA drivers.

Should I report this as a bug, or should I just wait for the next Ubuntu release (and hope for it to be fixed)?

Dag

---

### Post by tarunjindal on 2008-08-13
Hi,

I tried all i can but unable to get my 5.1 channel audio working i m sending you my configuration files please see to it.
Thanks

My default.pa

#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
load-module module-alsa-sink device=hw:0 channels=6 channel_map=front-left,front-right,rear-left,rear-right,center,lfe

load-module module-alsa-source device=hw:0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnome-session
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Publish connection data in the X11 root window
.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

### Make some devices default
#set-default-sink output
#set-default-source input

My daemon.conf

# $Id: daemon.conf.in 2175 2008-03-27 23:39:10Z lennart $
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; disallow-module-loading = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = -1
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; default-script-file = 

; log-target = auto
; log-level = notice

; resample-method = speex-float-3
; disable-remixing = no

; no-cpu-limit = no

; rlimit-as = -1
; rlimit-core = -1
; rlimit-data = -1
; rlimit-fsize = -1
; rlimit-nofile = 256
; rlimit-stack = -1
; rlimit-nproc = -1
; rlimit-memlock = -1
; rlimit-nice = 31
; rlimit-rtprio = 9

; default-sample-format = s16le
; default-sample-rate = 44100
default-sample-channels = 6

; default-fragments = 4
; default-fragment-size-msec = 25

Output after pulseaudio -k && pulseaudio -vv


I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
W: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
I: module-alsa-sink.c: Successfully opened device hw:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.hw_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.hw_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 4 fragments of size 4352 bytes.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel, falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device=hw:0 channels=6 channel_map=front-left,front-right,rear-left,rear-right,center,lfe").
W: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
I: module-alsa-source.c: Successfully opened device hw:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.hw_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 4 fragments of size 4352 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device=hw:0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_7fc_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_10de_7fc_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying surround51:0...
I: alsa-util.c: Couldn't open PCM device surround51:0: Device or resource busy
D: alsa-util.c: Trying surround71:0...
I: alsa-util.c: Couldn't open PCM device surround71:0: Device or resource busy
D: alsa-util.c: Trying surround50:0...
I: alsa-util.c: Couldn't open PCM device surround50:0: Device or resource busy
D: alsa-util.c: Trying surround41:0...
I: alsa-util.c: Couldn't open PCM device surround41:0: Device or resource busy
D: alsa-util.c: Trying surround40:0...
I: alsa-util.c: Couldn't open PCM device surround40:0: Device or resource busy
D: alsa-util.c: Trying front:0...
I: alsa-util.c: Couldn't open PCM device front:0: Device or resource busy
D: alsa-util.c: Trying hw:0 as last resort...
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_10de_7fc_sound_card_0_alsa_playback_0"): initialization failed.
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_7fc_sound_card_0_alsa_playback_0
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_10de_7fc_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying surround51:0...
I: alsa-util.c: Couldn't open PCM device surround51:0: Device or resource busy
D: alsa-util.c: Trying surround71:0...
I: alsa-util.c: Couldn't open PCM device surround71:0: Device or resource busy
D: alsa-util.c: Trying surround50:0...
I: alsa-util.c: Couldn't open PCM device surround50:0: Device or resource busy
D: alsa-util.c: Trying surround41:0...
I: alsa-util.c: Couldn't open PCM device surround41:0: Device or resource busy
D: alsa-util.c: Trying surround40:0...
I: alsa-util.c: Couldn't open PCM device surround40:0: Device or resource busy
D: alsa-util.c: Trying front:0...
I: alsa-util.c: Couldn't open PCM device front:0: Device or resource busy
D: alsa-util.c: Trying hw:0 as last resort...
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-source" (argument: "device_id=0 source_name=alsa_input.pci_10de_7fc_sound_card_0_alsa_capture_0"): initialization failed.
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_7fc_sound_card_0_alsa_capture_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_7fc_sound_card_0_alsa_hw_specific_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_7fc_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 0 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #5; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.hw_0'.
D: module-default-device-restore.c: No previous default source setting, ignoring.
I: module.c: Loaded "module-default-device-restore" (index: #6; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #7; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.hw_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.hw_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.hw_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #8; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #9; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #10; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.hw_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.hw_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.hw_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: main.c: Got signal SIGINT.
I: main.c: Exiting.
I: main.c: Daemon shutdown initiated.
I: module.c: Unloading "module-alsa-sink" (index: #0).
D: module-rescue-streams.c: No sink inputs to move away.
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "alsa_output.hw_0"
I: source.c: Freeing source 0 "alsa_output.hw_0.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #0).
I: module.c: Unloading "module-alsa-source" (index: #1).
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.hw_0"
I: module.c: Unloaded "module-alsa-source" (index: #1).
I: module.c: Unloading "module-hal-detect" (index: #2).
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus.Local, path=/org/freedesktop/DBus/Local, member=Disconnected
I: module.c: Unloaded "module-hal-detect" (index: #2).
I: module.c: Unloading "module-esound-protocol-unix" (index: #3).
I: module.c: Unloaded "module-esound-protocol-unix" (index: #3).
I: module.c: Unloading "module-native-protocol-unix" (index: #4).
I: module.c: Unloaded "module-native-protocol-unix" (index: #4).
I: module.c: Unloading "module-volume-restore" (index: #5).
I: module.c: Unloaded "module-volume-restore" (index: #5).
I: module.c: Unloading "module-default-device-restore" (index: #6).
I: module.c: Unloaded "module-default-device-restore" (index: #6).
I: module.c: Unloading "module-rescue-streams" (index: #7).
I: module.c: Unloaded "module-rescue-streams" (index: #7).
I: module.c: Unloading "module-suspend-on-idle" (index: #8).
I: module.c: Unloaded "module-suspend-on-idle" (index: #8).
I: module.c: Unloading "module-gconf" (index: #9).
I: module.c: Unloaded "module-gconf" (index: #9).
I: module.c: Unloading "module-x11-publish" (index: #10).
I: module.c: Unloaded "module-x11-publish" (index: #10).
I: main.c: Daemon terminated.
This stopped responding here so i had to press ctrl+c.

---

### Post by sammydee on 2008-08-13
> **dageng1 said:**
> Thanks Sam!
From what I know the SoundMAX Audio chip on my motherboard is fairly new, so it's probably incomplete ALSA drivers.

Should I report this as a bug, or should I just wait for the next Ubuntu release (and hope for it to be fixed)?

Dag

I'd report it as a bug to the pulseaudio website. First though, can you please post your ~/.asoundrc here, I just wanna confirm something.

Sam

---

### Post by sammydee on 2008-08-13
Tarunjindal:

I'm a little confused, why have you specified your card manually in your default.pa? You should let HAL autodetect it instead, try commenting out these lines:

```
load-module module-alsa-sink device=hw:0 channels=6 channel_map=front-left,front-right,rear-left,rear-right,center,lfe

load-module module-alsa-source device=hw:0
```

and then run pulseaudio -k && pulseaudio -vv again and post the output here.


Do you have more than one sound card in your pc? What make is it/are they?

Sam

---

### Post by dageng1 on 2008-08-13
@sammydee:
It doesn't seem like I have that file :confused:
I don't find one in my home directory, and not in the /etc path either...

Thanks for being som helpful :)

---

### Post by sammydee on 2008-08-13
> **dageng1 said:**
> @sammydee:
It doesn't seem like I have that file :confused:
I don't find one in my home directory, and not in the /etc path either...

Thanks for being som helpful :)

Ok that's fine, I thought you might have specified the pulseaudio device in .asoundrc but you obviously haven't.

Erm, bug report to pulseaudio then I suppose.

Sam

---

### Post by someonestolemyname on 2008-08-15
Thank you Sammy for your guide! That, combined with Meuri's advice on opening gnome-volume-control and unmuting all of the channels (how could i forget that!) have allowed me to get full surround sound. Including from stereo sources even!

Daniel

---

### Post by ravindran.k on 2008-08-18
Greetings!! 
Excellent How to!!!!!
Whomever having issues with PulseAudio server itself, fist check this [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

### Post by sammydee on 2008-08-18
> **ravindran.k said:**
> Greetings!! 
Excellent How to!!!!!
Whomever having issues with PulseAudio server itself, fist check this [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

The wiki is ok but a lot of the information there is actually a bit outdated now.

Sam

---

### Post by kanazky on 2008-08-19
Hey Sammy, I am having trouble configuring the pulse audio for my 2.1 computer speaker system.

I have a left and a right, seem to be configured correctly. and a subwoofer which has audio come out of it, but it sounds really bad.

when I ran a audio test it continuously did:

Front-Left (worked)
Front-Right (worked)
Rear-Left (nothing)

over and over, and I configured the Default.pa as such:

> ### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
load-module module-alsa-sink device_id=0 channels=3 channel_map=left,right,lfe
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

hope you can help me out :D

P.S. not sure it matters but I use Amarok for audio :D

~jake

---

### Post by sammydee on 2008-08-19
> **kanazky said:**
> Hey Sammy, I am having trouble configuring the pulse audio for my 2.1 computer speaker system.

I have a left and a right, seem to be configured correctly. and a subwoofer which has audio come out of it, but it sounds really bad.

when I ran a audio test it continuously did:

Front-Left (worked)
Front-Right (worked)
Rear-Left (nothing)

over and over, and I configured the Default.pa as such:



hope you can help me out :D

P.S. not sure it matters but I use Amarok for audio :D

~jake


Firstly, is your sound system ACTUALLY 3 channels? How many jacks plug into your computer from it? The vast VAST majority of 2.1 systems present themselves to the computer as 2.0 and perform internal filtering to get the sound to the subwoofer. If this is the case, you DON'T need this guide, and you should restore from the backups you made to get back to the original setup.

I also refer you to this part of the howto:

> This guide assumes you actually have surround sound speakers and have them all plugged into the appropriate sockets on the sound card. If you have a standard 2.1 setup, it will in 99% of cases only have one 3.5mm jack and will appear to the computer as 2.0 speakers. Following the guide in this case is probably quite a bad idea. A good rule of thumb is, if it works in windows, you have the right hardware and all the plugs are in the right places.

If on the other hand your subwoofer is actually separate, and you have two jacks plugging into the computer, one from the speakers and one from the sub, let me know and I'll try and help.

Sam

---

### Post by kanazky on 2008-08-20
Ok Sammy Change of plans, 

I have a car where I plug my laptop into the front dash, I have 2 front, 2 rear, 2 mini subs, and 2 large subs can I use this guide to create a surround sound in my car?

---

### Post by sammydee on 2008-08-20
> **kanazky said:**
> Ok Sammy Change of plans, 

I have a car where I plug my laptop into the front dash, I have 2 front, 2 rear, 2 mini subs, and 2 large subs can I use this guide to create a surround sound in my car?

Whoa, FOUR subwoofers :guitar:. That's mental.

Yes you can use pulseaudio to do this, however it will NOT filter the subwoofer sound to make it low frequency, you will need an external filter to do this.

If you are playing 4.1 surround sound, follow my guide (you will have to do it "the hard way").

If you are only playing two channel sound (eg practically all music) then you don't need to make it surround sound at all, just send all the left channel to the left two speakers, all the right channel to the right two speakers and mix the two together for the subs.

sam

---

### Post by raashell on 2008-08-25
I've a tale of inconsolable woe.  I used SammyDee's very simple and effective technique to get 5.1 surround sound working for my computer.  Life was sweet until this morning when, in trying to get the gnome-volume-control to work, I switched it to control a different device.  Immediately, I went from all five speakers and the sub to the front two speakers, the center, and the sub.

It's weird, like I flicked a switch that I can't figure out how to undo.

Since then I've spent the day trying numerous combinations in the volume control, erasing and re-copying the files to ~/.pulse, trying an .asoundrc, re-installing pulse and etc.  About everything I've been able to find on the web, I've tried.

Notes:

*Alsamixer shows four bars, with only mute/unmute capability for the first bar.

*The surround sound is from my motherboard, an Asus M2N SLI .  Paman identifies it as, "alsa_output.usb_device_d8c_201_noserial_if0_sound_card_0_alsa_playback_0"

*My user is in all 3 pulse groups.

I've attached my default.pa, daemon.conf, and the output of pulseaudio -k && pulseaudio -vv

Any help would be greatly appreciated- thanks, John

---

### Post by sammydee on 2008-08-26
raashell:

Do you have more than one sound card? Can you post the output of lspci here please?

It certainly looks as if it should be working fine, pulseaudio has successfully recognised a 6 channel sound card and is playing sound on all channels. I know it's stupid, but have you double checked that the jack hasn't come unplugged from the back of your pc and that the speakers are actually working on that channel?

Try:

```
alsamixer -c 0
```

See if any of the channels there are muted. Also, if there is a "surround sound" switch, try switching it from shared to independant or vice versa (I'm not actually sure what this does, but it seems to have an effect).

Let me know if this helps.
Sam

---

### Post by raashell on 2008-08-26
Hey Sammydee, thanks for the interest.  There is no other sound card in my computer-- just built in surround sound on the motherboard.  And your original solution worked great until I tried to alter what gnome-volume-control was controlling.  All the speakers are still plugged in tight and I haven't seen any surround sound switch in the volume control, sound preferences, or anywhere else.  Also, ESD is checked in my sound preferences.

lspci:

```
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
```

alsamixer -c 0 gets, "wrong 'c' argument."

alsmixer -c 1 gets:

[IMG]http://www.oneuglyduck.com/pulse/alsamxier.png[/IMG]

Here is my paman modules...

[IMG]http://www.oneuglyduck.com/pulse/modules.png[/IMG]

and sinks..

[IMG]http://www.oneuglyduck.com/pulse/sinks.png[/IMG]

---

### Post by sammydee on 2008-08-26
I was wondering for a while why the sound card wasn't showing up in lspci, then I saw your alsamixer -  it looks like it's a usb sound card, can you post the output of lsusb please?

Try going into system/preferences/sound and make sure all the different types of sound are using pulseaudio, not alsa or anything else.

Sam

---

### Post by raashell on 2008-08-26
My lsusb is:

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0d8c:0201 C-Media Electronics, Inc. 
Bus 001 Device 002: ID 045e:0063 Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000

Volume preferences lists: autodetect, usb audio, alsa, oss, and pulseaudio sound server.  I had everything on autodetect, but switched it to pulseaudio with no noticeable difference.

It's weird that I get surround out of the front two speakers, but not the rear ones.  I had considered removing and reinstalling alsa also, but I was worried about losing other programs by removing it.

---

### Post by sammydee on 2008-08-26
Do you currently have a ~/.asoundrc?

I'm struggling a bit to understand what is happening here. I think pulseaudio succesfully opened the card as a 5.1 surround sound card, and you can see here:

I: resampler.c: Forcing resampler 'copy', because of fixed, identical sample rates.
D: resampler.c: Channel matrix:
D: resampler.c:        I00   I01 
D: resampler.c:     +------------
D: resampler.c: O00 | 1.000 0.000
D: resampler.c: O01 | 0.000 1.000
D: resampler.c: O02 | 1.000 0.000
D: resampler.c: O03 | 0.000 1.000
D: resampler.c: O04 | 0.500 0.500
D: resampler.c: O05 | 0.500 0.500
I: resampler.c: Using resampler 'copy'

That it thinks it is outputting to six channels. But you only get sound out of four? What happens if while you are playing music, you execute the command: "pavumeter". How many channels does it show?

Sam

---

### Post by raashell on 2008-08-26
I do have an .asoundrc that is automatically generated, and I think, points to another file.  Here they are:

.asoundrc:

```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/john/.asoundrc.asoundconf>
```

.asoundrc.asoundconf:

```
# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card default
defaults.ctl.card default
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format S16_LE
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
defaults.namehint.showall off
defaults.namehint.basic on
defaults.namehint.extended off
pcm.!default { type pulse }
ctl.!default { type pulse }
```

Here is a shot of pavumeter with music playing:

[IMG]http://www.oneuglyduck.com/pulse/pavumeter.png[/IMG]

---

### Post by sammydee on 2008-08-26
Well pulseaudio certainly thinks it has six channels open and all are working just fine...

Try renaming your .asoundrc to .asoundrc.bak, so that it won't be loaded at all (you really shouldn't need one) and restart ubuntu.

Sam

---

### Post by raashell on 2008-08-26
Yeah, no dice.  I have zero understanding of how pulse and alsa work together if, at all, and how gnome-volume-control might affect it.  It seems bizarre, but I might be forced to do a fresh install of hardy just to get my sound back.

When I do speaker-test I get some error messages, but I don't know if it's supposed to work with pulse anyways...

```
Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -2,No such file or directory
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
```

---

### Post by ralyon on 2008-09-19
I've spent the last 5 hours searching and changing settings in my .pulse folder as well as .asoundrc and I keep getting the same error in pulseaudio when it doesn't fail all together:
```
...
W: alsa-util.c: Device hw:0,1 doesn't support 6 channels, changed to 2.
...
```

aplay -l gives me
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

In my default.pa I have "load-module module-alsa-sink device=hw:0,1" which enables the optical output and I have tried adding "channels=6 channel_map=front-left,front-right,front-center,rear-left,rear-right,lfe" to that with no change. I have also tried ...hw:0, ...hw:1, device_id=0, ...id=1, ...id=0,1 and ...alsa_output.pci_10de_371_sound_card_0_alsa_playback_1.

I also have "default-sample-rate = 48000" and "default-sample-channels = 6" in my daemon.conf file and the analog is showing 6 channels although I don't have anything attached to them.

I am using the [_Logitech Z-5500 Digital speakers_]("http://www.logitech.com/index.cfm/speakers_audio/home_pc_speakers/devices/224&cl=us,en") connected with an optical cable and I can get the 5.1 working with ALSA DTS passthrough in Mythtv so I know the speakers and cables are set correctly, I just can't get pulseaudio to see its capability.

Can anyone please help me with getting pulseaudio to see all 6 channels? Thanks in advance.

ralyon

---

### Post by sammydee on 2008-09-20
Hi Ralyon

DTS passthrough is a funny thing, it uses a normal two channel digital audio connection to send compressed 6 channel sound.

The digital connection is two channel ONLY and will only ever work with 6 channels with DTS passthrough. The only way to make surround sound work without DTS passthroguh is if pulseaudio dynamically encoded the surround sound into DTS on the fly. I'm pretty sure pulseaudio doesn't support DTS passthrough at all at this time, so you may not be able to get pulseaudio to see six channels at all for now.

I will check up on this, I could be wrong.

Sam

EDIT: DOH I am so stupid!

Here is the fix: [http://ubuntuforums.org/showthread.php?t=714712](http://ubuntuforums.org/showthread.php?t=714712)

---

### Post by PRGUY85 on 2008-09-21
I can't get any sound after following the link you provided: [http://ubuntuforums.org/showthread.php?t=714712](http://ubuntuforums.org/showthread.php?t=714712). 

I think the "make" command didn't do what its supposed to do:

```
make
make  all-recursive
make[1]: Entering directory `/home/manolo/alsa-plugins-1.0.15'
Making all in oss
make[2]: Entering directory `/home/manolo/alsa-plugins-1.0.15/oss'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/manolo/alsa-plugins-1.0.15/oss'
Making all in mix
make[2]: Entering directory `/home/manolo/alsa-plugins-1.0.15/mix'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/manolo/alsa-plugins-1.0.15/mix'
Making all in pph
make[2]: Entering directory `/home/manolo/alsa-plugins-1.0.15/pph'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/manolo/alsa-plugins-1.0.15/pph'
Making all in pulse
make[2]: Entering directory `/home/manolo/alsa-plugins-1.0.15/pulse'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/manolo/alsa-plugins-1.0.15/pulse'
Making all in rate
make[2]: Entering directory `/home/manolo/alsa-plugins-1.0.15/rate'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/manolo/alsa-plugins-1.0.15/rate'
Making all in a52
make[2]: Entering directory `/home/manolo/alsa-plugins-1.0.15/a52'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/manolo/alsa-plugins-1.0.15/a52'
Making all in rate-lavc
make[2]: Entering directory `/home/manolo/alsa-plugins-1.0.15/rate-lavc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/manolo/alsa-plugins-1.0.15/rate-lavc'
Making all in maemo
make[2]: Entering directory `/home/manolo/alsa-plugins-1.0.15/maemo'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/manolo/alsa-plugins-1.0.15/maemo'
Making all in doc
make[2]: Entering directory `/home/manolo/alsa-plugins-1.0.15/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/manolo/alsa-plugins-1.0.15/doc'
make[2]: Entering directory `/home/manolo/alsa-plugins-1.0.15'
make[2]: Leaving directory `/home/manolo/alsa-plugins-1.0.15'
make[1]: Leaving directory `/home/manolo/alsa-plugins-1.0.15'

```

I've got an onboard snd-hda-intel sound on my Gygabyte GA-P35-DS3L with Logitech 5.1 speakers connected through ANALOG jacks.  I could get sound out of all speakers before but not true surround sound, just same sound through all speakers, example: voice on movies came out of rear speakers all the time.

---

### Post by sammydee on 2008-09-21
I didn't read through the whole of that link I sent you, it was just a guy that had exactly the same issue that posted a fix.

If his method didn't work for you it's probably a better idea to pm the original author or post in the other thread.

Sam

---

### Post by sammydee on 2008-09-21
dupe post

---

### Post by ponchomx on 2008-10-21
Follow the howto, but I still can not sound 5.1. Any idea?

daemon.conf
> # $Id: daemon.conf.in 2175 2008-03-27 23:39:10Z lennart $
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; disallow-module-loading = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = -1
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; default-script-file = 

; log-target = auto
; log-level = notice

; resample-method = speex-float-3
; disable-remixing = no

; no-cpu-limit = no

; rlimit-as = -1
; rlimit-core = -1
; rlimit-data = -1
; rlimit-fsize = -1
; rlimit-nofile = 256
; rlimit-stack = -1
; rlimit-nproc = -1
; rlimit-memlock = -1
; rlimit-nice = 31
; rlimit-rtprio = 9

; default-sample-format = s16le
; default-sample-rate = 44100
default-sample-channels = 6

; default-fragments = 4
; default-fragment-size-msec = 25

default.code

> #!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)

### Manual config for configuring surround sound. Comment out line below to revert to defaults.
load-module module-alsa-sink device_id=0 channels=6 channel_map=front-left,front-right,center,rear-left,rear-right,lfe

#load-module module-alsa-source device=hw:1,0
.endif
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnome-session
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Publish connection data in the X11 root window
.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

### Make some devices default
#set-default-sink output
#set-default-source input

lspci
> 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)


:confused:

---

### Post by Evil Wayz on 2008-10-24
How many channels do I input for 2.1?  I tried three and the computer thinks pulse is working cuz my audio shows oscilloscope activity, but when i try to use alsamixer it doesn't work and when i try the test it tells me it can't connect.

---

### Post by kewlito on 2008-11-01
Thanks a lot sammy, you helped me fix my swapped channels on ALC888

---

### Post by sammydee on 2008-11-03
> **Evil Wayz said:**
> How many channels do I input for 2.1?  I tried three and the computer thinks pulse is working cuz my audio shows oscilloscope activity, but when i try to use alsamixer it doesn't work and when i try the test it tells me it can't connect.

Read the guide carefully, you CANNOT specify 3 channels to pulseaudio doing it "the easy way".

Also make sure you actually have three channels, most 2.1 systems take only a stereo input and extract low frequency information internally.

Sam

---

### Post by sammydee on 2008-11-03
> **ponchomx said:**
> Follow the howto, but I still can not sound 5.1. Any idea?

daemon.conf


default.code



lspci


:confused:

pulseaudio -vv output please.

Sam

---

### Post by Vinno on 2008-11-03
This shows on my sys log
```
ov  4 00:37:03 skynet pulseaudio[5941]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  4 00:37:03 skynet pulseaudio[5941]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  4 00:37:03 skynet pulseaudio[5941]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov  4 00:37:03 skynet pulseaudio[5941]: alsa-util.c: Device surround51:0 doesn't support 44100 Hz, changed to 48000 Hz.
Nov  4 00:37:04 skynet pulseaudio[5941]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Nov  4 00:37:04 skynet pulseaudio[5941]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
Nov  4 00:37:04 skynet pulseaudio[5941]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 1.
Nov  4 00:41:46 skynet anacron[5548]: Job `cron.daily' started
Nov  4 00:41:47 skynet anacron[6299]: Updated timestamp for job `cron.daily' to 2008-11-04
Nov  4 00:55:04 skynet pulseaudio[5941]: module-alsa-sink.c: Error opening PCM device surround51:0: Device or resource busy

```

Any ideas whats going wrong?

```
vinno@skynet:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
05:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1)

```

---

### Post by hhh81 on 2008-11-09
Hi i have tried to change this:

; default-sample-format = s16le
default-sample-rate = 48000
default-sample-channels = 5

in daemon.conf and works very well with 4.1 SOUND BLASTER LIVE! 1024 PLAYER WITH CREATIVE CSW FOUR POINT SURROUND 4.1 also for voices from movies, while the method 

load-module module-alsa-sink device_id=0 sink_name=SBLive1024 channels=5 channel_map=front-left,front-right,rear-left,rear-right,lfe
(also with device=hw:0)
in default.pa DOESN'T WORK!!!!! ONLY THE 2 FRONT SPEAKERS WORKS even selecting SBLive1024 from default server -> other -> SBLive1024
why did you write those 8Ull5H1T??!!

moreover i need help for setup flash 9 ,it crashes browsers also with libflashsupport-pulse
i have 9,0,48,0 flash version and the version 10 is worse..
please help
i have xubuntu hardy

---

### Post by sammydee on 2008-11-09
> **hhh81 said:**
> Hi i have tried to change this:

; default-sample-format = s16le
default-sample-rate = 48000
default-sample-channels = 5

in daemon.conf and works very well with 4.1 SOUND BLASTER LIVE! 1024 PLAYER WITH CREATIVE CSW FOUR POINT SURROUND 4.1 also for voices from movies, while the method 

This method gives you 5.0 surround, not 4.1. Please read the pulseaudio documentation or ask on IRC if you don't believe me on this point.

> load-module module-alsa-sink device_id=0 sink_name=SBLive1024 channels=5 channel_map=front-left,front-right,rear-left,rear-right,lfe
(also with device=hw:0)
in default.pa DOESN'T WORK!!!!! ONLY THE 2 FRONT SPEAKERS WORKS even selecting SBLive1024 from default server -> other -> SBLive1024
why did you write those 8Ull5H1T??!!

Excuse me? I'd like to just make a point here. I am not paid to post on these forums, I am not a developer and it certainly isn't my fault that your setup isn't working. I posted this guide in the hope that it might help someone, and reading the comments in this thread it seems as if it has helped a lot of people.

> moreover i need help for setup flash 9 ,it crashes browsers also with libflashsupport-pulse
i have 9,0,48,0 flash version and the version 10 is worse..
please help
i have xubuntu hardy

Firstly, this problem is totally unrelated to surround sound and doesn't belong in this thread, use the search function, there are multiple threads around explaining how to deal with this problem.

Secondly, I'm not sure how you can expect help from me after you've just insulted me saying my post is ********. Please post in this thread again with your problem when you're less inclined to throw my offer of help back in my face.

Sam

---

### Post by sammydee on 2008-11-09
> **Vinno said:**
> This shows on my sys log
```
ov  4 00:37:03 skynet pulseaudio[5941]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  4 00:37:03 skynet pulseaudio[5941]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  4 00:37:03 skynet pulseaudio[5941]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov  4 00:37:03 skynet pulseaudio[5941]: alsa-util.c: Device surround51:0 doesn't support 44100 Hz, changed to 48000 Hz.
Nov  4 00:37:04 skynet pulseaudio[5941]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Nov  4 00:37:04 skynet pulseaudio[5941]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
Nov  4 00:37:04 skynet pulseaudio[5941]: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 1.
Nov  4 00:41:46 skynet anacron[5548]: Job `cron.daily' started
Nov  4 00:41:47 skynet anacron[6299]: Updated timestamp for job `cron.daily' to 2008-11-04
Nov  4 00:55:04 skynet pulseaudio[5941]: module-alsa-sink.c: Error opening PCM device surround51:0: Device or resource busy

```

Any ideas whats going wrong?


Looks like you specified hw:1 somewhere in the config file but it looks like you only have one sound card. Try again but with hw:0

---

### Post by hhh81 on 2008-11-09
with

; default-sample-format = s16le
default-sample-rate = 48000
default-sample-channels = 5

for 4.1 work also subwoofer basses 
there is bass and low frequency effect from subwoofer that is enabled
and i haven't tried 4.1 in 'default-sample-channels ='

---

### Post by Vinno on 2008-11-10
> **sammydee said:**
> Looks like you specified hw:1 somewhere in the config file but it looks like you only have one sound card. Try again but with hw:0

I never edited any config that has the lines of 'hw'

---

### Post by apollo23 on 2008-11-13
I am currently using a Creative X-fi XtremeMusic sound card and I am trying to get sound using a 5.1 speaker configuration. I can currently hear sound just find out of 2 of my speakers but the other 3 and sub-woofer are not making any sound. Here are the files I have tried to mess with..

My: gedit ~/.asoundrc is blank

I have also tried my gedit ~/.asoundrc:

> 
# my shared device with 5.1 upmix

pcm.shared_surround {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}

# make the default device use pulse (all alsa apps will use it and mix)

pcm.!default {
type pulse
}

ctl.!default {
type pulse
}
My: gedit ~/.pulse/daemon.conf
> 
# $Id: daemon.conf.in 2175 2008-03-27 23:39:10Z lennart $
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out. Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; disallow-module-loading = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = -1
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; default-script-file =

; log-target = auto
; log-level = notice

resample-method = speex-float-1
; disable-remixing = no

; no-cpu-limit = no

; rlimit-as = -1
; rlimit-core = -1
; rlimit-data = -1
; rlimit-fsize = -1
; rlimit-nofile = 256
; rlimit-stack = -1
; rlimit-nproc = -1
; rlimit-memlock = -1
; rlimit-nice = 31
; rlimit-rtprio = 9

; default-sample-format = s16le
; default-sample-rate = 44100
default-sample-channels = 6

default-fragments = 8
default-fragment-size-msec = 10
and finally my gedit ~/.pulse/default.pa is:

> 
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnome-session
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Publish connection data in the X11 root window
.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

### Make some devices default
#set-default-sink output
#set-default-source input
I am not really sure what Pulse Audio is but I haven't installed any pulse programs (or at least I don't think I did). If you have any ideas on how I can get 5.1 sound I would greatly appreciate it. Thank you for all of your help.

---

### Post by oldsoundguy on 2008-11-13
Alsa set for 5.1 did the trick for me .. it's in the synaptic package manager.  On 8,10 it will automatically install Pulse audio. (you need to launch the Alsa mixer to set your system up)

Earlier builds gave you a choice and did not install Pulse. (earlier versions of Pulse were dodgy at best .. but works fine now!)

IF you are running digital out to a digital amp, however, the MASTER VOLUME control on the desktop and in the Alsa mixer is dead as a doornail (never has worked).. totally useless.  You have to rely on the volume control of the individual programs to keep a lid on it.

HOWEVER X-Fi now has a new open source driver from Creative itself and it may be your answer.  Check their site.  (won't work on legacy stuff such as Live Drive)

---

### Post by speedsix on 2008-11-14
Seeing as pulse doesn't support passthrough yet, I'm considering swapping the digital connection to my amp for analogue ones. What I am concerned about which I haven't seen anyone mention is the ability to route low frequencies from main channels to the sub.

I assume by specifying the 'LFE' channel this will only play the discrete .1 LFE track whereas most surround receivers are capable of routing bass from the main channels to the sub aswell as the lfe track. My amp has a small/large setting for each channel, large being full range and small being anything above a preset crossover frequency with lows going to the sub.

This isn't too much of a big deal but I'm guessing if you play a source which doesn't have a discrete .1 LFE track(2ch music for example) you won't get any bass routed to the sub?


I've asked this on the pulse mailing list but no reply yet.



Thanks

Dom

---

### Post by SR_ELPIRATA on 2008-11-15
Hey Sammy:

MANY THANKS

Finally I have the onboard audio on this Abit NF7-S2 to work using the analog inputs. Too bad I still need to upgrade the rig so that I can play 1080 files but this is a great step to acomplish the HTPC without windows :)

Again, thanks man.

ELP

---

### Post by pcozzy on 2008-11-19
thank you simply worked for me hda-intel stac9221 azalia 5.1 surround sound, the easy method worked for me.

---

### Post by lordyosch on 2008-11-20
Thanks for this how-to I've looked through a few and got nowhere!

I was missing the Sub woofer, my music was sounding awfully flat!

Once I'd adjusted the settings in the config files all I needed to do was choose the correct device from a seemingly long list of variations.


Thanks again!!

(Now if someone wants to write a driver for my multi-function printer I'll delete windows entirely!!)

Jay

---

### Post by iamojuve on 2008-12-10
Finally got my set-up working. Thought others might be interested.

Installed 8.10 on AMD64 with ATI graphics and Creative Audigy 2 ZS audio card. Audio kinda worked out of the box Rythmbox and thats about it. Installed pulseaudio to get Flash 10 audio working and allow multiple streams at once.

Pulseaudio killed the Audigy card but finally with this forum and some tinkering got my system working. Have front port connected to power amp to power my mirage left and right towers then have center/sub port connected to wonderful mirage sub (with crossover filter). Connected this to 1080p tv and now its better than any movie theatre :popcorn: (well some rear speakers would be nice but its more about the power):p

important part of default.pa:
```

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink device_id=0 channels=3 channel_map=front-left,front-right,lfe
load-module module-alsa-sink device_id=0 channels=3 channel_map=front-left,front-right,front-center
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
#.ifexists module-hal-detect.so
#load-module module-hal-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
#load-module module-detect
#.endif
```

and didn't touch anything in daemon.conf

Interesting thing is that with this setting the surround sound port works (but didn't test if it is true surround) and pulseaudio connection doesn't crash like when I use channels=6...

hope this helps someone! And if anyone has any suggestions on how to send only the LFE sound to the shared center/LFE port on the audigy card that would be great

bestest

lodo

---

### Post by BmoreFerris on 2009-03-12
I only get sound from the rear left and rear right speakers and ubuntu thinks they are the front two.  When i go into alsamixer (from command and GUI) there is only master and capture options for me.  I have tried everything I could to fix the problem.  Please help me.  Also I tried to ttach the files told me invalid files.

Hers is aplay -L && aplay -l
front:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=SB,DEV=0
    HDA ATI SB
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=HDMI
    HDA ATI HDMI
    Front speakers
surround40:CARD=HDMI
    HDA ATI HDMI
    4.0 Surround output to Front and Rear speakers
surround41:CARD=HDMI
    HDA ATI HDMI
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=HDMI
    HDA ATI HDMI
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=HDMI
    HDA ATI HDMI
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=HDMI
    HDA ATI HDMI
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And then  pulseaudio -k && pulseaudio -vv

visual@visual:~$ pulseaudio -k && pulseaudio -vv
W: ltdl-bind-now.c: Failed to find original dlopen loader.

---

### Post by BmoreFerris on 2009-03-14
Here is daemon.conf:

# $Id: daemon.conf.in 2175 2008-03-27 23:39:10Z lennart $
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; disallow-module-loading = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = -1
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; default-script-file = 

; log-target = auto
; log-level = notice

resample-method = speex-float-1
; disable-remixing = no

; no-cpu-limit = no

; rlimit-as = -1
; rlimit-core = -1
; rlimit-data = -1
; rlimit-fsize = -1
; rlimit-nofile = 256
; rlimit-stack = -1
; rlimit-nproc = -1
; rlimit-memlock = -1
; rlimit-nice = 31
; rlimit-rtprio = 9

; default-sample-format = s16le
; default-sample-rate = 44100
 default-sample-channels = 6

default-fragments = 8
default-fragment-size-msec = 10

And default.pa:

#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnome-session
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Publish connection data in the X11 root window
.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

### Make some devices default
#set-default-sink output
#set-default-source input

please help.  I still only have sound from my back speakers

---

### Post by sammydee on 2009-03-14
> **BmoreFerris said:**
> And then  pulseaudio -k && pulseaudio -vv

visual@visual:~$ pulseaudio -k && pulseaudio -vv
W: ltdl-bind-now.c: Failed to find original dlopen loader.

It should say a lot more than this?

try killall pulseaudio && pulseaudio -vv

Sam

---

### Post by BmoreFerris on 2009-03-14
visual@visual:~$ pulseaudio && pulseaudio -vv
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Then it hangs

---

### Post by sammydee on 2009-03-15
> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
Subdevices: 0/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0

As far as I can tell, alsa thinks you only have two channels...

I know it sounds stupid, are you sure you actually HAVE a surround sound card?

Sam

---

### Post by BmoreFerris on 2009-03-16
I am sure.  The Motherboard I have is an M4A78 PRO,  This is a custom built machine.  The book that came with it says I have a:
VIA1708S 8-channel Hidh Definition Audio CODEC
   - Supports Jack-Detection and Multi-Streaming
   - Optical S/PDIF Out port at back I/O
   - ASUS Noise Filter
If you need more info just let me know what to give you.

---

### Post by BmoreFerris on 2009-03-16
I just reinstalled the drivers and now have all the speakers but the rear two.

---

### Post by dr_dred5 on 2009-03-16
Hi there. Thanks for this guide. After tinkering with 5.1 sound for over two years and 4 versions of Ubuntu, I finally have it almost working.

My issue now is that some of my channels are being duplicated. My FL and FR work, but both also come through the centre channel. My centre channel only comes through the FL and LFE comes through both the sub and the FR channel.

I haven't tried remaping yet, as I'm not sure if this is the issue. It's probably something basic that I've missed in the previous posts.

I'm using Ubuntu 8.10
Soundblaster Live 5.1 Analog 3 plugs.
Logitec 5.1 speakers.

Any insight would be greatly appreciated! Thanks in advance!

Here is the info.

Daemon.conf
```

; daemonize = no
; fail = yes
; disallow-module-loading = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = -1
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; default-script-file = 

; log-target = auto
; log-level = notice

resample-method = speex-float-1
; disable-remixing = no

; no-cpu-limit = no

; rlimit-as = -1
; rlimit-core = -1
; rlimit-data = -1
; rlimit-fsize = -1
; rlimit-nofile = 256
; rlimit-stack = -1
; rlimit-nproc = -1
; rlimit-memlock = -1
; rlimit-nice = 31
; rlimit-rtprio = 9

; default-sample-format = s16le
; default-sample-rate = 44100
default-sample-channels = 6

default-fragments = 8
default-fragment-size-msec = 10
```

default.pa
```
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnome-session
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Publish connection data in the X11 root window
.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```

aplay -L && aplay -l

```
neil@neil-desktop:~$ aplay -L && aplay -l
default:CARD=Live
    SB Live 5.1, ADC Capture/Standard PCM Playback
    Default Audio Device
front:CARD=Live,DEV=0
    SB Live 5.1, ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Live,DEV=0
    SB Live 5.1, ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Live,DEV=0
    SB Live 5.1, ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
surround40:CARD=Live,DEV=0
    SB Live 5.1, ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Live,DEV=0
    SB Live 5.1, ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Live,DEV=0
    SB Live 5.1, ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Live,DEV=0
    SB Live 5.1, ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=Live,DEV=0
    SB Live 5.1, Multichannel Capture/PT Playback
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SB Live 5.1], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Live [SB Live 5.1], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SB Live 5.1], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

And the interesting one.

pulseaudio -k && pulseaudio -vv

```
neil@neil-desktop:~$ pulseaudio -k && pulseaudio -vv
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: Failed to kill daemon.

```

Edit. I should also mention that after this message pulse seems to crash and I get no sound at all unless I reboot.

---

### Post by dr_dred5 on 2009-03-29
Bump.

---

### Post by one51 on 2009-04-14
Got it *mostly* working with the info here, thanks!

One problem: although I get the proper channels in sound test mode (including sub, working fine)
speaker-test -c 6  [in my case for 5.1]

the subwoofer is not used during playback.  For example watching a movie with heavy bass, nothing comes to the LFE channel.  Could this be a problem with the default parameter,

; disable-lfe-remixing = yes

??

I don't fully understand that parameter so didn't want to just change it randomly (and maybe I didn't fully understand the help text I found online describing it).  Maybe it's default mixing my LFE into other channels for some unknown reason?

---

### Post by Jakey_TheSnake on 2009-04-14
Hey, 

I have been trying to get surround sound to work for quite a while now, I have got it to work before on 7.10 Hardy Heron, though. All I had to do that time was your "easy way", but this time - no joy! 

```
jake@jake-desktop:~$ lspci -v | grep audio
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)

```
I noticed that there *were* some linux drivers for nForce chipsets here: [http://www.nvidia.co.uk/Download/index.aspx?lang=en-uk](http://www.nvidia.co.uk/Download/index.aspx?lang=en-uk), but I don't know the exact model of mine as lspci doesn't tell me(?). However, the only two available for linux are Professional 2000/3000, and I don't think I have that. Regardless, I didn't have to install any drivers for it to work last time. 

Basically, I am only getting sound out of my front two channels. I am not completely sure how I'm supposed to have the stuff set up in the Volume Control, but I have unmuted and maxed out the volumes for Surround, Center and LFE. I also have it on 6 channel mode, with independent jacks (I assume this means you have 3? I have one for front, one for rear, and one for center/LFE - please confirm).

My daemon.conf:
```
; daemonize = no
; fail = yes
; disallow-module-loading = no
; disallow-exit = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = 20
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice

resample-method = src-linear
; disable-remixing = no
; disable-lfe-remixing = yes

; no-cpu-limit = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rtttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 6

default-fragments = 8
default-fragment-size-msec = 10
```

My default.pa:
```
.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav
load-sample-dir-lazy /usr/share/sounds/ubuntu/stereo

.fail

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif


### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect tsched=0
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

### Automatically load driver modules for Bluetooth hardware
#.ifexists module-bluetooth-discover.so
#load-module module-bluetooth-discover
#.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
load-module module-console-kit

### Enable positioned event sounds
load-module module-position-event-sounds

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```

aplay -L && aplay -l:
```
jake@jake-desktop:~$ aplay -L && aplay -l
front:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2
    Front speakers
surround40:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2
    4.0 Surround output to Front and Rear speakers
surround41:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=nForce2,DEV=0
    NVidia nForce2, NVidia nForce2 - IEC958
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


pulseaudio -k && pulseaudio -vv:
```
jake@jake-desktop:~$ pulseaudio -k && pulseaudio -vv
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: PolicyKit refuses acquire-high-priority privilege.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: main.c: Can realtime: no, can high-priority: no
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.14
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux i686 2.6.28-11-generic #37-Ubuntu SMP Mon Mar 23 16:40:23 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is d2bf25482c15efe0969ec1e949e4875c.
I: main.c: Using runtime directory /home/jake/.pulse/d2bf25482c15efe0969ec1e949e4875c:runtime.
I: main.c: Using state directory /home/jake/.pulse.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
```

This last output looks fairly promising, so if you could please offer any assistance I would be eternally obliged :) 

I almost forgot, my asound.conf:
```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```
NB - I did not have an asound.conf for my system before this, the file was blank, so I copy and pasted someone's from the first page - it made no difference after reboot. This is the one in /etc/, I don't have one in ~/. 

Oh, and I should probably mention I am trying to run 5.1 (I believe) - in that I have two rear, two front, one center and one LFE channel. I also had them working fine in XP when I still had it (damn things came with drivers and software for Windows, though).

---

### Post by timzak on 2009-04-15
On my Xubuntu 8.04 install, there is no /etc/pulse/daemon.conf file!  So how do I enable rear channels?  Does Xubuntu not have Pulse installed, or is it an incomplete Pulse?

---

### Post by deephurt on 2009-04-18
Hi!

I have 4.1 system on my MSI gx720 laptop. The problem is that only the subwoofer works. When I plug in headphones, they work, but the subwoofer does also. I run ubuntu 9.04.
I tried the 'Hard Way' with exactly the same config (device_id=0 channels=5). I even tried the device=hw:0 instead... After restart, the sound was the same. 
I wonder if the config in jaunty should be somehow modified, or smthing.
Thanks in advance for any help.

So here it goes:

daemon.conf:
```

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; disallow-module-loading = no
; disallow-exit = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = 20
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice

resample-method = src-linear
; disable-remixing = no
; disable-lfe-remixing = yes

; no-cpu-limit = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rtttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2

default-fragments = 8
default-fragment-size-msec = 10

```

default.pa:
```

#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav
load-sample-dir-lazy /usr/share/sounds/ubuntu/stereo

.fail

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif


### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
load-module module-alsa-sink device_id=0 channels=5 channel_map=front-left,front-right,rear-left,rear-right,lfe
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect tsched=0
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

### Automatically load driver modules for Bluetooth hardware
#.ifexists module-bluetooth-discover.so
#load-module module-bluetooth-discover
#.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
load-module module-console-kit

### Enable positioned event sounds
load-module module-position-event-sounds

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input

```

aplay -L && aplay -l
```

front:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

pulseaudio -k && pulseaudio -vv
```

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: PolicyKit refuses acquire-high-priority privilege.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: main.c: Can realtime: no, can high-priority: no
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.14
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux x86_64 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is 9100861badf512eb83f8f7a549e8fc85.
I: main.c: Using runtime directory /home/branoz/.pulse/9100861badf512eb83f8f7a549e8fc85:runtime.
I: main.c: Using state directory /home/branoz/.pulse.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

```

btw, I have no asound.conf or asoundrc in /etc or /home

---

### Post by mikeize on 2009-04-25
Grr Ubuntu, grrrrrrrr.  EVERY time I am forced to reinstall, my sound is broken, and it takes me a week of pulling my hair out before some indecipherable combination of 20 different tutorials results magically in my sound working!  Yay!  Thanks Ubuntu!

Well, I'll give you credit that sound works -at all-.  But surround sound just refuses.  I've tried 3 or 4 different tutorials now, starting from scratch each time, yet I still only have 2 channel sound.  All configuration points to a working 5.1 system, but I get not a peep from my rear speakers.  This was all working fine before my fresh install of Jaunty.

Ubuntu, I love you but you piss me the eff off.  The worst part is that I KNOW that this is possible, so I HAVE to keep trying... but like all too many things, the solution is FAR from discoverable. (System>Sound>Enable 5.1 Surround Sound).

---

### Post by one51 on 2009-04-26
> **mikeize said:**
> All configuration points to a working 5.1 system, but I get not a peep from my rear speakers.

me: Asus M5A78 Pro with Via 1708S integrated sound.  + Jaunty and Alsa xxx.18 (the package manager version, not the latest Alsa).

mikeize, this sounds similar to my problem (one page back on this thread).  The problems I have:
=> It seems that everything found in both L+R is routed to Center, even for stereo music (which should be played in L+R only, no center).  Why does it re-route?  The purpose of 5.1 is that those who mastered the DVD already decided what goes to Center!
=> "Master" volume control only controls L+R, meaning if I used the PC volume (which I'd like to via a remote), I would have to manually adjust Center, Rear, and Sub volume separately from master.  WTF!  How do I get one volume that controls all channels?
=> Even though everything works in the speaker-test output including LFE and Rear (sounds the same as you?), the LFE channel is empty on every other method of output I've tried (movies in 3 different programs, music / MP3's, etc).  Not a peep from my subwoofer during actual use.  I can only get test whitenoise out of it.

Seems there is some program which is playing around with what virtual channels go to what actual channels.  But I don't want to have some additional layer re-routing what the application (VLC, Rhythmbox, etc) tells it!  And I'd prefer not to spend weeks trying random combinations of asound.conf or whatever.

If you find a solution, please let me know.  So far since I posted, this HOWTO has just been filled with new problems... so I'm not confident... but I've got time.

---

### Post by markitoxs on 2009-04-26
I also recommend checking on the irc.

---

### Post by one51 on 2009-04-26
Thanks, will look on the IRC channel--did not know about that.  Cheers

---

### Post by mikeize on 2009-04-26
one51:  I don't even get sound from the rear speakers during 'test'.

---

### Post by one51 on 2009-04-26
mikeize: OK, mine worked in test when I changed to the proper channels (6 in my case) in ~/.pulse/default.pa as described at the top page of this thread.  But if you still have no sound after that, I don't know any other tips...

I was on the IRC channel for like an hour, ended up giving tips to 3 or 4 people but no one gave any feedback at all about my question.  Meh.

---

### Post by mikeize on 2009-04-26
Are you using Jaunty?  I don't even have that file (well, i just created it-but it's empty).

---

### Post by one51 on 2009-04-27
Args, sorry, mis-copy/paste.  It is this file,

/etc/pulse/daemon.conf

Which the original Howto post describes editing.

(Yes, definitely Jaunty).

---

### Post by sammydee on 2009-04-27
Check the first post again guys, a solution is on it's way, I need to be sure it works ok for me before I write it up though. Give it a week or so, it should be up here.

Sam

---

### Post by one51 on 2009-04-27
Thanks!  I am happy to be a "beta tester" if you have some simple changes to try out.

Today figured out the volume control issue: have to link the main system slider to the Pulseaudio mixer (not Alsa), where the surround channels can be linked.  Alsa doesn't seem to allow linking all channels, only L+R (at least in the default setup).

So what I am dealing with now, I have confirmed: some layer or hardware (NOT the sound-producing app) is rerouting channels.
* Stereo sound is (not as desired) reformatted to surround
* Subwoofer is mixed into front channels, even when playing 5.1 DVDs

Pulseaudio volume meter and mixer show that app input in stereo is converted to five channels somehow (minus sub, even though the sub works in speaker-test).

Looking forward to the fix  :-)

---

### Post by sammydee on 2009-04-27
If you are willing to "beta test" the new method, then follow these steps:

You need to add this ppa:

[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

And upgrade to the latest pulseaudio/alsa. This has flat volume support as well as sound card configuration. run pavucontrol, you should see a new tab called configuration. Have a quick play with that, let me know if it works for you.

You will need to revert any changes you made to your daemon.conf or default.pa as well, this relies on HAL detecting your cards.

WARNING: I have not tested this, I have no idea how well it might or might not work. I am also not sure of whether it is possible to revert these changes properly, so please only try this method on a non-critical system.

I'd appreciate feedback on this, positive or negative.

Sam

---

### Post by one51 on 2009-04-29
Hi Sam, I completed my backup and tried this out today.  Nothing catastrophically bad, but I noticed a few things:

1) Config section of the PulseAudio volume control GUI can set 5.1 surround, but it reverts to 2-ch on logout/login or on restart
2) When the Rhythmbox track changes to the next mp3, the volume of the PulseAudio mixer sometimes gets adjusted (!), happens more frequently when volume of the track is high
3) Volume slider on taskbar no longer actually controls anything (even if I have "Sound" preferences set to PulseAudio playback mixer, which fixed my previous problem with this slider).  So before I had a config error (between chair and keyboard), but this time I think it's Pulseaudio or something.
4) A problem that I also had before this upgrade that didn't go away: at very low (but non-zero) volume settings, there is a loud static noise that suddenly appears.  Something must be interfering at low volume levels, perhaps a noise filter of some kind?

I changed my daemon.conf back to the old one (with channels = 6 hard set) and then it at least solved problem 1) on re-login.  But it shows that something is not correctly detecting, and the manual config in the GUI is not being saved.

Most annoying: even though speaker-test still works (sound outputs properly from the correct 6 speakers): LFE still doesn't output anything when I run applications, stereo tracks are still remixed to surround, and I'm not convinced that 5.1 is even playing correctly on the 5 (minus 1) channels.  I suspect it's also a stereo signal that is being remixed to "false" surround (echo added, and equal signals in L+R sent to Center).

My guess is that my sound chip, the Via 1708S (not listed as supported on Alsa website?) is being interpreted as another VIA chip and isn't getting the correct configuration.  The chip and/or some software layer is remixing things in a wrong way.  How can I report this bug or request this functionality?  (longtime computer geek, new to Linux, because such problems as this put me off Linux for the last 6 years).

---

### Post by arbrandes on 2009-05-03
Instead of using themuso's PPA, I'm going to give a shot to this other one, which has Hardy packages:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Funny thing, the problem I'm having with libasound 1.0.15 is a recognized bug in Hardy, version 1.0.16 actually got uploaded to -proposed, but later deleted due to regressions:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/221673](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/221673)

Wish me luck!

Adolfo

---

### Post by arbrandes on 2009-05-03
Ok, everything went smoothly with psyke's PPA.  Still had to change daemon.conf according to this howto, but now basically everything works, especially my personal holy grail (which I hadn't achieved as of yet):  

1) Upmixing stereo sources automatically and transparently...

2) ... while playing 5.1 sources normally,

3) all the while with an Alsa-compatible master volume control for all channels.

  Only glitch left is with MythTV, which for some godforsaken reason cannot control the volume.  Probably something to do with the fact that until a few days ago the svn version wouldn't work with pulseaudio at all!

Adolfo

---

### Post by ceylonerana on 2009-05-04
Thank you for your great post. I have one thing to ask from you. I use Kubuntu Intrepid. But there is no daemon.conf file to edit. It has client.conf file. So how can I go through that :)
Thanks....

---

### Post by mikeize on 2009-05-04
Thank you Arbrandes!  I too have made progress with the method you describe.  The only thing wrong now, is that both rear channels are getting mixed together as "rear lfe".  That is, neither rear left or rear right works during the speaker test, but they seem to both work during the "rear lfe" test.  Still, this development gives me hope!

-mike

---

### Post by one51 on 2009-05-04
After PulseAudio started giving me occasional dropouts (pops and crackles), starting after I tried the PPA and then (painfully) deinstalled it... I decided to disable PulseAudio.  Alsa is still able to play multiple sources at once, and do surround (when I manually select correct audio stream in VLC or MPlayer).  Even found a method to properly play stereo PCM sound on L+R speakers.

If PulseAudio improves so that there aren't so many 100+reply threads of people with problems, I'll try it again on Ubuntu "Sprightly Sparrow" or whenever that occurs.  Good luck to all...

Now if only I could get SPDIF to work properly on my VT1708S.

---

### Post by swankcr on 2009-05-20
All, 

First I'm going to say I'm a Fedora user -- sorry to break ranks :)  

I've been trying to get my 4.1 channel speakers to work in F10 for a few days now, with limited (ok, no) success.  I'm hoping you all can help.  If there's anything you can suggest I'd appreciate it.  My alsamixer (no matter what I do) seems shows only two channels. 

Here's the output from aplay -l  
```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1                                           
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```aplay -L
```

front:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default
    Default
hdmi:CARD=HDMI
    HDA ATI HDMI, ATI HDMI
    HDMI Audio Output

```
This is my sink config line:
```

load-module module-alsa-sink device=hw:0 channels=5 channel_map=front-left,front-right,rear-left,rear-right,lfe

```Output from pulseaudio -vvv: 
```

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.                                                                                               
I: caps.c: Dropping root privileges.                                                                                                                        
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.                                                                                               
D: main.c: Started as real root: no, suid root: yes                                                                                                         
I: main.c: PolicyKit refuses acquire-high-priority privilege.                                                                                               
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:    
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.                                                                                                                                                     
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.                                                                                              
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted                                                                                 
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted                                                                                 
D: main.c: Can realtime: no, can high-priority: no                                                                                                          
D: main.c: Can realtime: no, can high-priority: no                                                                                                          
I: main.c: This is PulseAudio 0.9.14                                                                                                                        
D: main.c: Compilation host: x86_64-redhat-linux-gnu                                                                                                        
D: main.c: Compilation CFLAGS: -ggdb -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math                                                                                                                              
D: main.c: Running on host: Linux x86_64 2.6.27.21-170.2.56.fc10.x86_64 #1 SMP Mon Mar 23 23:08:10 EDT 2009                                                 
I: main.c: Page size is 4096 bytes                                                                                                                          
D: main.c: Compiled with Valgrind support: no                                                                                                               
D: main.c: Running in valgrind mode: no                                                                                                                     
D: main.c: Optimized build: no                                                                                                                              
I: main.c: Machine ID is 74399f08d460f8c169be514e49fdd77e.                                                                                                  
I: main.c: Using runtime directory /home/swankcr/.pulse/74399f08d460f8c169be514e49fdd77e:runtime.                                                           
I: main.c: Using state directory /home/swankcr/.pulse.                                                                                                      
I: main.c: Running in system mode: no                                                                                                                       
I: main.c: Fresh high-resolution timers available! Bon appetit!                                                                                             
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65472                    
I: module-device-restore.c: Sucessfully opened database file '/home/swankcr/.pulse/74399f08d460f8c169be514e49fdd77e:device-volumes.x86_64-redhat-linux-gnu.gdbm'.                                                                                                                                                       
I: module.c: Loaded "module-device-restore" (index: #0; argument: "").                                                                                      
I: module-stream-restore.c: Sucessfully opened database file '/home/swankcr/.pulse/74399f08d460f8c169be514e49fdd77e:stream-volumes.x86_64-redhat-linux-gnu.gdbm'.                                                                                                                                                       
I: module.c: Loaded "module-stream-restore" (index: #1; argument: "").                                                                                      
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...                                                                                                 
D: alsa-util.c: Maximum hw buffer size is 371 ms                                                                                                            
W: alsa-util.c: Device hw:0 doesn't support 5 channels, changed to 2.                                                                                       
I: module-alsa-sink.c: Successfully opened device hw:0.                                                                                                     
I: module-alsa-sink.c: Successfully enabled mmap() mode.                                                                                                    
I: module-alsa-sink.c: Successfully enabled timer-based scheduling mode.                                                                                    
I: alsa-util.c: Successfully attached to mixer 'hw:0'                                                                                                       
I: alsa-util.c: Cannot find mixer control "Master" or mixer control is no combination of switch/volume.                                                     
W: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.                                               
I: alsa-util.c: Using mixer control "PCM".                                                                                                                  
I: module-device-restore.c: Restoring volume for sink alsa_output.hw_0.                                                                                     
I: module-device-restore.c: Restoring mute state for sink alsa_output.hw_0.                                                                                 
I: sink.c: Created sink 0 "alsa_output.hw_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right                                      
I: module-device-restore.c: Restoring volume for source alsa_output.hw_0.monitor.                                                                           
I: module-device-restore.c: Restoring mute state for source alsa_output.hw_0.monitor.                                                                       
I: source.c: Created source 0 "alsa_output.hw_0.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right                          
I: module-alsa-sink.c: Using 2 fragments of size 32768 bytes, buffer time is 371.52ms                                                                       
I: module-alsa-sink.c: Time scheduling watermark is 50.00ms                                                                                                 
D: module-alsa-sink.c: hwbuf_unused_frames=0                                                                                                                
D: module-alsa-sink.c: setting avail_min=56713                                                                                                              
I: module-alsa-sink.c: Volume ranges from 0 to 42.                                                                                                          
I: module-alsa-sink.c: Volume ranges from -63.00 dB to 0.00 dB.                                                                                             
I: alsa-util.c: All 2 channels can be mapped to mixer channels.                                                                                             
I: module-alsa-sink.c: Using hardware volume control. Hardware dB scale supported.                                                                          
I: module-alsa-sink.c: Using software mute control.                                                                                                         
D: alsa-util.c: snd_pcm_dump():                                                                                                                             
D: alsa-util.c: Hardware PCM card 0 'HDA ATI SB' device 0 subdevice 0                                                                                       
D: alsa-util.c: Its setup is:                                                                                                                               
D: alsa-util.c:   stream       : PLAYBACK                                                                                                                   
D: alsa-util.c:   access       : MMAP_INTERLEAVED                                                                                                           
D: alsa-util.c:   format       : S16_LE                                                                                                                     
D: alsa-util.c:   subformat    : STD                                                                                                                        
D: alsa-util.c:   channels     : 2                                                                                                                          
D: alsa-util.c:   rate         : 44100                                                                                                                      
D: alsa-util.c:   exact rate   : 44100 (44100/1)                                                                                                            
D: alsa-util.c:   msbits       : 16                                                                                                                         
D: alsa-util.c:   buffer_size  : 16384                                                                                                                      
D: alsa-util.c:   period_size  : 8192                                                                                                                       
D: alsa-util.c:   period_time  : 185759                                                                                                                     
D: alsa-util.c:   tstamp_mode  : NONE                                                                                                                       
D: alsa-util.c:   period_step  : 1                                                                                                                          
D: alsa-util.c:   avail_min    : 56713                                                                                                                      
D: alsa-util.c:   period_event : 0                                                                                                                          
D: alsa-util.c:   start_threshold  : -1                                                                                                                     
D: alsa-util.c:   stop_threshold   : -1                                                                                                                     
D: alsa-util.c:   silence_threshold: 0                                                                                                                      
D: alsa-util.c:   silence_size : 0                                                                                                                          
D: alsa-util.c:   boundary     : 4611686018427387904                                                                                                        
D: alsa-util.c:   appl_ptr     : 0                                                                                                                          
D: alsa-util.c:   hw_ptr       : 0                                                                                                                          
D: module-alsa-sink.c: Requested volume: 0:  64% 1:  64%                                                                                                    
D: module-alsa-sink.c: Got hardware volume: 0:  64% 1:  64%                                                                                                 
D: module-alsa-sink.c: Calculated software volume: 0: 100% 1: 100%                                                                                          
D: module-alsa-sink.c: Thread starting up                                                                                                                   
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29                                                                                                     
I: module-alsa-sink.c: Starting playback.                                                                                                                   
I: module.c: Loaded "module-alsa-sink" (index: #2; argument: "device=hw:0 channels=5 channel_map=front-left,front-right,rear-left,rear-right,lfe ").        
D: cli-command.c: Checking for existance of '/usr/lib64/pulse-0.9/modules/module-hal-detect.so': success                                                    
I: module-hal-detect.c: Trying capability alsa                                                                                                              
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer                                                                  
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer                                                              
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 tsched=1'     
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...                                                                                              
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D0p failed                                                                                                        
I: alsa-util.c: Couldn't open PCM device front:0: Device or resource busy                                                                                   
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...                                                                                         
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D0p failed                                                                                                        
I: alsa-util.c: Couldn't open PCM device surround40:0: Device or resource busy                                                                              
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...                                                                                         
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D0p failed                                                                                                        
I: alsa-util.c: Couldn't open PCM device surround41:0: Device or resource busy                                                                              
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...                                                                                         
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D0p failed                                                                                                        
I: alsa-util.c: Couldn't open PCM device surround50:0: Device or resource busy                                                                              
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...                                                                                         
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D0p failed                                                                                                        
I: alsa-util.c: Couldn't open PCM device surround51:0: Device or resource busy                                                                              
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...                                                                                         
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D0p failed                                                                                                        
I: alsa-util.c: Couldn't open PCM device surround71:0: Device or resource busy                                                                              
D: alsa-util.c: Trying hw:0 as last resort...                                                                                                               
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...                                                                                                 
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D0p failed                                                                                                        
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy                                                                                      
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 tsched=1"): initialization failed.                                                                                                                                      
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_playback_0                                           
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0 tsched=1'   
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...                                                                                              
D: alsa-util.c: Maximum hw buffer size is 371 ms                                                                                                            
I: module-alsa-source.c: Successfully opened device front:0.                                                                                                
I: module-alsa-source.c: Successfully enabled mmap() mode.                                                                                                  
I: module-alsa-source.c: Successfully enabled timer-based scheduling mode.                                                                                  
I: (alsa-lib)control.c: Invalid CTL front:0                                                                                                                 
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory                                                                                
I: alsa-util.c: Successfully attached to mixer 'hw:0'                                                                                                       
I: alsa-util.c: Using mixer control "Capture".                                                                                                              
I: module-device-restore.c: Restoring volume for source alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0.                                               
I: module-device-restore.c: Restoring mute state for source alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0.                                           
I: source.c: Created source 1 "alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right                                                                                                                                                          
I: module-alsa-source.c: Using 2 fragments of size 32768 bytes, buffer time is 371.52ms                                                                     
I: module-alsa-source.c: Time scheduling watermark is 20.00ms                                                                                               
D: module-alsa-source.c: hwbuf_unused_frames=0                                                                                                              
D: module-alsa-source.c: setting avail_min=62005                                                                                                            
I: module-alsa-source.c: Volume ranges from 0 to 31.                                                                                                        
I: module-alsa-source.c: Volume ranges from -16.50 dB to 30.00 dB.                                                                                          
I: alsa-util.c: All 2 channels can be mapped to mixer channels.                                                                                             
I: module-alsa-source.c: Using hardware volume control. Hardware dB scale supported.                                                                        
D: alsa-util.c: snd_pcm_dump():                                                                                                                             
D: alsa-util.c: Soft volume PCM                                                                                                                             
D: alsa-util.c: Control: PCM Playback Volume                                                                                                                
D: alsa-util.c: min_dB: -51                                                                                                                                 
D: alsa-util.c: max_dB: 0                                                                                                                                   
D: alsa-util.c: resolution: 256                                                                                                                             
D: alsa-util.c: Its setup is:                                                                                                                               
D: alsa-util.c:   stream       : CAPTURE                                                                                                                    
D: alsa-util.c:   access       : MMAP_INTERLEAVED                                                                                                           
D: alsa-util.c:   format       : S16_LE                                                                                                                     
D: alsa-util.c:   subformat    : STD                                                                                                                        
D: alsa-util.c:   channels     : 2                                                                                                                          
D: alsa-util.c:   rate         : 44100                                                                                                                      
D: alsa-util.c:   exact rate   : 44100 (44100/1)                                                                                                            
D: alsa-util.c:   msbits       : 16                                                                                                                         
D: alsa-util.c:   buffer_size  : 16384                                                                                                                      
D: alsa-util.c:   period_size  : 8192                                                                                                                       
D: alsa-util.c:   period_time  : 185759                                                                                                                     
D: alsa-util.c:   tstamp_mode  : NONE                                                                                                                       
D: alsa-util.c:   period_step  : 1                                                                                                                          
D: alsa-util.c:   avail_min    : 62005                                                                                                                      
D: alsa-util.c:   period_event : 0                                                                                                                          
D: alsa-util.c:   start_threshold  : -1                                                                                                                     
D: alsa-util.c:   stop_threshold   : -1                                                                                                                     
D: alsa-util.c:   silence_threshold: 0                                                                                                                      
D: alsa-util.c:   silence_size : 0                                                                                                                          
D: alsa-util.c:   boundary     : 4611686018427387904                                                                                                        
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA ATI SB' device 0 subdevice 0                                                                                
D: alsa-util.c: Its setup is:                                                                                                                               
D: alsa-util.c:   stream       : CAPTURE                                                                                                                    
D: alsa-util.c:   access       : MMAP_INTERLEAVED                                                                                                           
D: alsa-util.c:   format       : S16_LE                                                                                                                     
D: alsa-util.c:   subformat    : STD                                                                                                                        
D: alsa-util.c:   channels     : 2                                                                                                                          
D: alsa-util.c:   rate         : 44100                                                                                                                      
D: alsa-util.c:   exact rate   : 44100 (44100/1)                                                                                                            
D: alsa-util.c:   msbits       : 16                                                                                                                         
D: alsa-util.c:   buffer_size  : 16384                                                                                                                      
D: alsa-util.c:   period_size  : 8192                                                                                                                       
D: alsa-util.c:   period_time  : 185759                                                                                                                     
D: alsa-util.c:   tstamp_mode  : NONE                                                                                                                       
D: alsa-util.c:   period_step  : 1                                                                                                                          
D: alsa-util.c:   avail_min    : 62005                                                                                                                      
D: alsa-util.c:   period_event : 0                                                                                                                          
D: alsa-util.c:   star                                                                                                                                      
D: module-alsa-source.c: Requested volume: 0:  82% 1:  82%                                                                                                  
D: module-alsa-source.c: Got hardware volume: 0:  82% 1:  82%                                                                                               
D: module-alsa-source.c: Calculated software volume: 0: 100% 1: 100%                                                                                        
D: module-alsa-source.c: Thread starting up                                                                                                                 
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28                                                                                                     
I: module.c: Loaded "module-alsa-source" (index: #3; argument: "device_id=0 source_name=alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0 tsched=1").    
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_hw_specific_0                                        
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_control__1                                           
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_960f_sound_card_0_alsa_playback_3                                           
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_960f_sound_card_0_alsa_hw_specific_0                                        
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_960f_sound_card_0_alsa_control__1                                           
I: module-hal-detect.c: Loaded 1 modules.                                                                                                                   
I: module.c: Loaded "module-hal-detect" (index: #4; argument: "").                                                                                          
D: cli-command.c: Checking for existance of '/usr/lib64/pulse-0.9/modules/module-esound-protocol-unix.so': success                                          
I: module.c: Loaded "module-esound-protocol-unix" (index: #5; argument: "").                                                                                
I: module.c: Loaded "module-native-protocol-unix" (index: #6; argument: "").                                                                                
I: module-default-device-restore.c: Restored default sink 'alsa_output.hw_0'.                                                                               
D: core-subscribe.c: Dropped redundant event due to change event.                                                                                           
I: module-default-device-restore.c: Restored default source 'alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0'.                                         
I: module.c: Loaded "module-default-device-restore" (index: #7; argument: "").                                                                              
I: module.c: Loaded "module-rescue-streams" (index: #8; argument: "").                                                                                      
I: module.c: Loaded "module-always-sink" (index: #9; argument: "").                                                                                         
D: module-suspend-on-idle.c: Sink alsa_output.hw_0 becomes idle.                                                                                            
D: module-suspend-on-idle.c: Source alsa_output.hw_0.monitor becomes idle.                                                                                  
D: module-suspend-on-idle.c: Source alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0 becomes idle.                                                      
I: module.c: Loaded "module-suspend-on-idle" (index: #10; argument: "").                                                                                    
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session2"                                                                            
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session2                                                                             
I: module.c: Loaded "module-console-kit" (index: #11; argument: "").                                                                                        
I: module.c: Loaded "module-position-event-sounds" (index: #12; argument: "").                                                                              
D: cli-command.c: Checking for existance of '/usr/lib64/pulse-0.9/modules/module-gconf.so': failure                                                         
I: main.c: Daemon startup complete.                                                                                                                         
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired                                               
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired                                              
I: module-alsa-source.c: Overrun!                                                                                                                           
N: module-alsa-source.c: Increasing wakeup watermark to 40.00 ms
I: module-alsa-source.c: Overrun!
N: module-alsa-source.c: Increasing wakeup watermark to 80.00 ms
I: module-alsa-source.c: Overrun!
N: module-alsa-source.c: Increasing wakeup watermark to 160.00 ms
I: module-alsa-source.c: Overrun!
N: module-alsa-source.c: Increasing wakeup watermark to 320.00 ms
I: module-suspend-on-idle.c: Sink alsa_output.hw_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.hw_0.monitor idle for too long, suspending ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=InterfaceLockAcquired
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=InterfaceLockAcquired
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=InterfaceLockReleased
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer, member=InterfaceLockReleased

```

---

### Post by one51 on 2009-05-20
> **swankcr said:**
> All, 

First I'm going to say I'm a Fedora user -- sorry to break ranks :)  

I've been trying to get my 4.1 channel speakers to work in F10 for a few days now, with limited (ok, no) success.  I'm hoping you all can help.  If there's anything you can suggest I'd appreciate it.  My alsamixer (no matter what I do) seems shows only two channels. 


I had problems where no software device actually used the 5.1 channels, even though in speaker-test they worked fine.  Some layer was using only stereo and sending the output to all speakers (ugh).  Then after trying several "upgrades" (launchpad...) I started getting stuttering sound, probably due to the glitch-free audio feature which seems to work counter to its intent.

In the end I solved most of my problems by disabling (not removing!) Pulseaudio, using this guide: [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/")

The only drawback to my current ALSA-only solution is that only one sound device plays at once, but when I have a few more days of free time I can probably solve that.  At least now 5.1 works, and no stuttering.  Gotta love Linux...

Chip: VT1708S onboard sound on Asus M4A78 Pro

---

### Post by swankcr on 2009-05-20
I tried removing pulseaudio once, and I was faced with the same situation.  It almost looks to me like the problem is at the alsa level.  Like alsa isn't seeing using anything but 2 channels.  

Fedora doesn't appear to include alsaconf, so I don't have an .asoundrc.  One of these nights when I have a few free minutes, I'll see if I can just build one.

---

### Post by one51 on 2009-05-20
> **swankcr said:**
> I tried removing pulseaudio once, and I was faced with the same situation.  It almost looks to me like the problem is at the alsa level.  Like alsa isn't seeing using anything but 2 channels.  

Fedora doesn't appear to include alsaconf, so I don't have an .asoundrc.  One of these nights when I have a few free minutes, I'll see if I can just build one.

Try this thread: [http://ubuntuforums.org/showthread.php?t=783222]("http://ubuntuforums.org/showthread.php?t=783222")

How to get surround working in Alsa.  I used it to get worthwhile 2-ch sound, instead of all speakers getting full volume L+R (or combination thereof) from 2-ch sources like mp3.  But maybe the 5.1 section will help you.  Good luck...

---

### Post by unimatrix on 2009-06-12
PA keeps crashing on 6 channels. That's why it's always set to stereo by default.

---

### Post by ArbitraryC on 2009-06-12
I'm having trouble with VLC on my Ubuntu 9.04 system.

When trying to play 2.1 channel files, I only hear the .1 channel on front-left and front-right, and I don't get any voices. It's fine on totem and mplayer, all using pulseaudio. Doing other stuff like playing MP3s from banshee/audacious

Running this with 2 channels produces sound on the left when it thinks it's on the left, and on the right when it thinks it's on the right.
```
speaker-test -c #channels
```

I don't have a default.pa or daemon.conf in my ~/.pulse, so I included the system-wide ones. I also threw in my ~/.pulse/default-sink.

I might have to attach some of these in a separate post. :)

Anyway... this one's really got me stumped. Everything plays normally in other players, MP3s play normally in other players. MP3s even play normally in VLC. But, VLC plays the same 2.1 channel files fine on other computers.

Any help would be greatly appreciated.

---

### Post by ArbitraryC on 2009-06-12
> **ArbitraryC said:**
> 
I might have to attach some of these in a separate post. :)As promised.

---

### Post by ArbitraryC on 2009-06-13
hm... so, using padevchooser to look at the outputs from different applications, it looks like Totem sends 3 channels to pulseaudio, but VLC only sends two.

I think Pulse must be mixing the center channel out to the other two with totem, which is what you'd want it to do. When I unlock the channels and then mute the center channel from Totem, I get the same results as with VLC.

So this isn't a pulse bug, it's a VLC bug. It's a failure of VLC to send the third channel, which Pulse would be able to deal with just fine.

---

### Post by strange_cathect on 2009-07-31
When I try to edit 

> .pulse/daemon.conf

It is just blank. What happened here?

---

### Post by theog3 on 2009-08-12
Hi sammydee. I'm relatively new to Ubuntu and I'd like to mention a problem i'm facing with my sound card. At first, I have an Acer Aspire 8930G-944G64BN notebook with a 5.1 built-in Intel 82801I sound card (ALC889 Analog, ICH9 Family). Although sound playback has no significant problems, it seems that I have only 2.0 sound, eventhough i configured daemon.conf to have 6 channels (as you pointed in your how-to). So I'd appreciate it if you replied to me and guide me what to do to solve this. Thanks in advance! I'm also including the files you request in your guide.

Here is the output of aplay -L && aplay -l:
```
theog3@theog3-laptop:~$ aplay -L && aplay -l
default:CARD=Intel
    HDA Intel, ALC889 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC889 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

And this is the output of pulseaudio -k && pulseaudio -vv:
```
theog3@theog3-laptop:~$ pulseaudio -k && pulseaudio -vv
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: Giving up CAP_NICE
D: main.c: Can realtime: no, can high-priority: no
I: main.c: &#913;&#965;&#964;&#972; &#949;&#943;&#957;&#945;&#953; &#964;&#959; PulseAudio 0.9.14
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux i686 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is 1a9f24a529da5ef0f3e44b5a4a342e90.
I: main.c: Using runtime directory /home/theog3/.pulse/1a9f24a529da5ef0f3e44b5a4a342e90:runtime.
I: main.c: Using state directory /home/theog3/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64,0 KiB each, total size is 64,0 MiB, maximum usable slot size is 65496
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #0; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #1; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/theog3/.pulse/1a9f24a529da5ef0f3e44b5a4a342e90:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #2; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/theog3/.pulse/1a9f24a529da5ef0f3e44b5a4a342e90:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_playback_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: module-device-restore.c: Restoring volume for sink alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0.
I: module-device-restore.c: Restoring mute state for sink alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0.
I: sink.c: Created sink 0 "alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-device-restore.c: Restoring volume for source alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0.monitor.
I: module-device-restore.c: Restoring mute state for source alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0.monitor.
I: source.c: Created source 0 "alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-sink.c: Using 4 fragments of size 4352 bytes, buffer time is 98,68ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module-alsa-sink.c: Volume ranges from 0 to 64.
I: module-alsa-sink.c: Volume ranges from -64,00 dB to 0,00 dB.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel.
I: module-alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 4352
D: alsa-util.c:   period_size  : 1088
D: alsa-util.c:   period_time  : 24671
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 1088
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1140850688
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1140850688
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 4352
D: alsa-util.c:   period_size  : 1088
D: alsa-util.c:   period_time  : 24671
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 1088
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_
D: module-alsa-sink.c: Requested volume: 0: 100% 1: 100%
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
D: module-alsa-sink.c: Got hardware volume: 0: 100% 1: 100%
D: module-alsa-sink.c: Calculated software volume: 0: 100% 1: 100%
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Source alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0 becomes idle.
I: module.c: Loaded "module-alsa-sink" (index: #4; argument: "device_id=0 sink_name=alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0 tsched=0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: module-device-restore.c: Restoring volume for source alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0.
I: module-device-restore.c: Restoring mute state for source alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0.
I: source.c: Created source 1 "alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-source.c: Using 4 fragments of size 4352 bytes, buffer time is 98,68ms
D: module-alsa-source.c: hwbuf_unused=0
D: module-alsa-source.c: setting avail_min=1
I: module-alsa-source.c: Volume ranges from 0 to 46.
I: module-alsa-source.c: Volume ranges from -16,00 dB to 30,00 dB.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-source.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 4352
D: alsa-util.c:   period_size  : 1088
D: alsa-util.c:   period_time  : 24671
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 1088
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1140850688
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1140850688
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 4352
D: alsa-util.c:   period_size  : 1088
D: alsa-util.c:   period_time  : 24671
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 1088
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_th
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
D: module-alsa-source.c: Requested volume: 0: 100% 1: 100%
D: module-alsa-source.c: Got hardware volume: 0: 100% 1: 100%
D: module-alsa-source.c: Calculated software volume: 0: 100% 1: 100%
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-alsa-source" (index: #5; argument: "device_id=0 source_name=alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0 tsched=0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_hw_specific_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_hw_specific_1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_hw_specific_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #6; argument: "tsched=0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #7; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #8; argument: "").
I: module-default-device-restore.c: Restored default sink 'alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default source 'alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
I: module.c: Loaded "module-always-sink" (index: #11; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
I: module.c: Loaded "module-console-kit" (index: #12; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #13; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
```

---

### Post by GalloGlas on 2009-08-21
At one point I had surround sound working using this tutorial.  I have creative elite pro x-fi sound card.  

But every time a linux header update comes out I have to reinstall my sound drivers. The X-fi driver 1.0 never worked for me and will not install properly.  However, the 1.03 drivers do.  They provide all the channels in the mixer but in sound preferences are separate.  By changing them I can get sound to come out of the individual speakers. 

But this last update broke everything.  Now I'm back to 2 channel.   I've always managed to repeat the install steps and get surround working again.  But this time is different.   

So here is the output of a few things.  Let me know if you see anything i need to change.  

```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Daemon.conf 

```
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; disallow-module-loading = no
; disallow-exit = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = 20
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice

resample-method = src-linear
; disable-remixing = no
; disable-lfe-remixing = yes

; no-cpu-limit = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rtttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 6

default-fragments = 8
default-fragment-size-msec = 10
```

Default.pa 

```
## Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect tsched=0
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

### Automatically load driver modules for Bluetooth hardware
#.ifexists module-bluetooth-discover.so
#load-module module-bluetooth-discover
#.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=6 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
load-module module-console-kit

### Enable positioned event sounds
load-module module-position-event-sounds

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```

But here is the weird part..  speaker test output

```
speaker-test -Dpulse -c6 -twav

speaker-test 1.0.20

Playback device is pulse
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM pulse
Playback open error: -2,No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM pulse
Playback open error: -2,No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM pulse
Playback open error: -2,No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM pulse
Playback open error: -2,No such file or directory

```

The speaker test used to work... before the last update.   It is getting annoying that I have to reinstall the sound drivers every time a header update comes out... but never so annoying until now, when repeating the steps I've done time and time again didn't work.  

Hopefully ubuntu will get better support for sound in the near future.

---

### Post by coolen on 2009-09-17
Hey all.

First off, thanks for this. It's a good thread, and thanks to the steps outlined here, I have two channels working, not just one!

Problem is, I have a 5.1 setup.

I tried the first method, but the test keeps triggering the rear left and center speakers. I have no idea why. I think it's all plugged in correctly, although I've no Windows install to test it on.

My daemon.conf:

```
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; disallow-module-loading = no
; disallow-exit = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = 20
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice

resample-method = src-linear
; disable-remixing = no
; disable-lfe-remixing = yes

; no-cpu-limit = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rtttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
default-sample-channels = 6

default-fragments = 8
default-fragment-size-msec = 10
```

My default.pa:

```
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav
load-sample-dir-lazy /usr/share/sounds/ubuntu/stereo

.fail

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif


### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect tsched=0
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

### Automatically load driver modules for Bluetooth hardware
#.ifexists module-bluetooth-discover.so
#load-module module-bluetooth-discover
#.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
load-module module-console-kit

### Enable positioned event sounds
load-module module-position-event-sounds

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```

Result of aplay -L && aplay -l:

```
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Output of pulseaudio -k && pulseaudio -vv:

```
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: PolicyKit refuses acquire-high-priority privilege.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: main.c: Can realtime: no, can high-priority: no
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.14
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux x86_64 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is cef871a904afdba9b4db20354aab8d50.
I: main.c: Using runtime directory /home/benji/.pulse/cef871a904afdba9b4db20354aab8d50:runtime.
I: main.c: Using state directory /home/benji/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65472
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #0; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #1; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/benji/.pulse/cef871a904afdba9b4db20354aab8d50:device-volumes.x86_64-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #2; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/benji/.pulse/cef871a904afdba9b4db20354aab8d50:stream-volumes.x86_64-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_26c_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_26c_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_26c_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0 tsched=0'
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-sink.c: Successfully opened device surround51:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL surround51:0
I: alsa-util.c: Unable to attach to mixer surround51:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: module-device-restore.c: Restoring volume for sink alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0.
I: module-device-restore.c: Restoring mute state for sink alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0.
I: sink.c: Created sink 0 "alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0" with sample spec s16le 6ch 44100Hz and channel map front-left,front-right,rear-left,rear-right,front-center,lfe
I: module-device-restore.c: Restoring volume for source alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0.monitor.
I: module-device-restore.c: Restoring mute state for source alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0.monitor.
I: source.c: Created source 0 "alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0.monitor" with sample spec s16le 6ch 44100Hz and channel map front-left,front-right,rear-left,rear-right,front-center,lfe
I: module-alsa-sink.c: Using 8 fragments of size 5376 bytes, buffer time is 81.27ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module-alsa-sink.c: Volume ranges from 0 to 31.
I: module-alsa-sink.c: Volume ranges from -46.50 dB to 0.00 dB.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel.
I: module-alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 6
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 8070450532247928832
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 8070450532247928832
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA NVidia' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 6
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_eve
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
D: module-alsa-sink.c: Requested volume: 0:  52% 1:  52% 2:  52% 3:  52% 4:  52% 5:  52%
D: module-alsa-sink.c: Got hardware volume: 0:  52% 1:  52% 2:  52% 3:  52% 4:  52% 5:  52%
D: module-alsa-sink.c: Calculated software volume: 0: 100% 1: 100% 2: 100% 3: 100% 4: 100% 5: 100%
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Source alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0 becomes idle.
I: module.c: Loaded "module-alsa-sink" (index: #4; argument: "device_id=0 sink_name=alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0 tsched=0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_10de_26c_sound_card_0_alsa_capture_0 tsched=0'
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: PCM device plug:surround51:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: PCM device plug:surround71:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: PCM device plug:surround50:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: PCM device plug:surround41:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: PCM device plug:surround40:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: module-device-restore.c: Restoring volume for source alsa_input.pci_10de_26c_sound_card_0_alsa_capture_0.
I: module-device-restore.c: Restoring mute state for source alsa_input.pci_10de_26c_sound_card_0_alsa_capture_0.
I: source.c: Created source 1 "alsa_input.pci_10de_26c_sound_card_0_alsa_capture_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-source.c: Using 8 fragments of size 1792 bytes, buffer time is 81.27ms
D: module-alsa-source.c: hwbuf_unused=0
D: module-alsa-source.c: setting avail_min=1
I: module-alsa-source.c: Volume ranges from 0 to 31.
I: module-alsa-source.c: Volume ranges from -12.00 dB to 34.50 dB.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-source.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 8070450532247928832
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 8070450532247928832
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA NVidia' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
D: module-alsa-source.c: Requested volume: 0:  22% 1:  22%
D: module-alsa-source.c: Got hardware volume: 0:  25% 1:  25%
D: module-alsa-source.c: Calculated software volume: 0:  97% 1:  97%
D: module-suspend-on-idle.c: Source alsa_input.pci_10de_26c_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-alsa-source" (index: #5; argument: "device_id=0 source_name=alsa_input.pci_10de_26c_sound_card_0_alsa_capture_0 tsched=0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_26c_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #6; argument: "tsched=0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #7; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #8; argument: "").
I: module-default-device-restore.c: Restored default sink 'alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default source 'alsa_input.pci_10de_26c_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
I: module.c: Loaded "module-always-sink" (index: #11; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
I: module.c: Loaded "module-console-kit" (index: #12; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #13; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Sink alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_10de_26c_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
```

HOLY CRAP THAT WAS LONG!

Any ideas?

---

### Post by alexfish on 2009-12-13
[SIZE=5][COLOR=Red][B]Update 05/11/09: Attention everyone. This guide is now OUTDATED and no longer necessary. Configuring surround sound is now ridiculously easy in Ubuntu 9.10 (Karmic) - just go into the hardware tab in sound preferences, click the device to configure, then select a surround sound profile from the drop down box. There is NO NEED to use this guide at all any more!

[SIZE=2][COLOR=Blue] PLEASE .. I AM only A Learner  . a screen shot would be nice

   
[/COLOR][/SIZE][/B][/COLOR][/SIZE]

---

### Post by unimatrix on 2009-12-13
> **alexfish said:**
> Update 05/11/09: Attention everyone. This guide is now OUTDATED and no longer necessary. Configuring surround sound is now ridiculously easy in Ubuntu 9.10 (Karmic) - just go into the hardware tab in sound preferences, click the device to configure, then select a surround sound profile from the drop down box. There is NO NEED to use this guide at all any more!


Except when it doesn't work, like in my case where PulseAudio doesn't detect surround mode.

---

### Post by one51 on 2009-12-13
Here's my question.  In Jaunty, I had to disable Pulseaudio because I constantly had sound glitches/dropouts, especially when the system was running multiple programs at once.  It was basically unusable.

Is Karmic any better about this?  I'm rather nervous about upgrading, because my system is basically stable now.  But having disabled Pulseaudio, I can only have one program locking the sound stream at a time through Alsa, so it's quite annoying.  Plus it would be excellent to see if my digital audio out might finally work (in Karmic).  But ONLY if the Pulseaudio glitch problem (ironically caused by the "glitch-free audio" feature) is fixed.

---

### Post by SR_ELPIRATA on 2009-12-21
I changed mobos (after my post on page 14) and 9.10 gave me free scratching noises and what not (I havent tried an upgrade though, just the clean install) whereas in 9.04 I have perfect audio and surround. I used to have a dualboot setup so that whenever I needed to play something that didnt work on Ubuntu sound but now I dont have anymore.

The only thing I would like to know how to do is.... how to setup a crossover setting so that the LFE only receives sound below 70hz, currently I even hear dialogues and other sounds (on both the center and sub). Another option that I had never thought about was to use a physical crossover or something that blocks those frequencies from showing up in the sub.

BTW, I used to have a sound problem while playing 720p demos and found out that using xbmc I can play them without any noises like I would get from VLC. Is funny, I always kept that windows side because in there VLC played those 720p files without problems and also for watching hulu and getting 5.1 output, but I no longer have this problem. I still have it, just for games.

And, btw, the sound applet in 9.10 is CONFUSING. You can raise your main volume over 100% but once you turn down the volume you have to manually (at least for me) get into the panel again to raise it up to over 100%. Wish they hadnt touched that!

ELP

---

### Post by bapoumba on 2009-12-21
Moved to Outdated Tutorials.

---

### Post by one51 on 2009-12-21
> **SR_ELPIRATA said:**
> 
The only thing I would like to know how to do is.... how to setup a crossover setting so that the LFE only receives sound below 70hz, currently I even hear dialogues and other sounds (on both the center and sub). Another option that I had never thought about was to use a physical crossover or something that blocks those frequencies from showing up in the sub.

I would also like to know how to do this! Normally I just turn off the sub except when watching 5.1, because Jaunty cannot properly handle the bass in stereo signals. It just routes L+R to the sub channel, or something like that, full-frequency.

This isn't really an "outdated tutorial" since I don't plan to update to 9.10 after reading about the sound problems people had with it... I think many others plan the same.

---

### Post by bt.ionut on 2011-09-14
Hi, i have a problem, I attended dozens of tutorials to do to be heard 5.1 and I succeeded here have details about my board audio( [http://i56.tinypic.com/209g1eb.png](http://i56.tinypic.com/209g1eb.png) ), do you have any ideas how I could make them hear 5.1? Thank you.

---

### Post by GalloGlas on 2011-09-14
> **bt.ionut said:**
> Hi, i have a problem, I attended dozens of tutorials to do to be heard 5.1 and I succeeded here have details about my board audio( [http://i56.tinypic.com/209g1eb.png](http://i56.tinypic.com/209g1eb.png) ), do you have any ideas how I could make them hear 5.1? Thank you.

This thread died way back in 2009.  I'd suggest starting a new thread (if one already doesn't exist) so others that have the same issue can refer to it.   

PM me the link once you've done that.

---

