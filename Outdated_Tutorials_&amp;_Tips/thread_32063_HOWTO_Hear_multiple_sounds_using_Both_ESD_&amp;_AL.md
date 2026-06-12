---
title: "HOWTO: Hear multiple sounds using Both ESD &amp; ALSA"
date: 2005-05-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Gandalf on 2005-05-05
Hello there,
This is just a clean and better organised guide of varunus's HowTo located [here](http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound). So primarily all the credits go to him.

This HowTo will give you instruction on enabling software mixing, to avoid application problems like Audacity needing killall esd to work as well as Skype [now Skype will no longer crash if you receive a message or a call (when it try to play sound in fact)], so let's get to work shall we ?? :-P.


[list=1]We need to install libesd-alsa0 so
```

sudo apt-get install libesd-alsa0

```

[*]We need to create /etc/asound.conf, so
```

sudo gedit /etc/asound.conf

```
Insert into it:
```

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048	#1024
buffer_size 32768	#4096
			#periods 128
rate 48000		#44100
}
bindings {
0 0
1 1
}
}

```

[*]We need to change /etc/esound/esd.conf contents so:
```

sudo mv /etc/esound/esd.conf /etc/esound/esd.conf_backup
sudo gedit /etc/esound/esd.conf

```
Insert into it:
```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```

[*]Now **You** need to change ubuntu sound server to alsa (you can leave it ESD but better use alsa because it has better sound handling):
```

gstreamer-properties

```
Change both (in the Audio Tab not the Video) from ESD to ALSA so it looks just like the picture:
[[IMG]http://img104.echo.cx/img104/3140/screenshotmultimediasystemssel.th.png[/IMG]](http://img104.echo.cx/my.php?image=screenshotmultimediasystemssel.png)
[/list]
All that's left now is to restart your computer (after restart you must hear sound) to enable these changes. Also configure XMMS or Beep-media-player (or any player) to use ALSA instead of eSound/ESD. If you hear a strange sound, just change everything back to ESD. If everything worked correctly, now Audacity & Skype will work normally and all the program will play sound using either Alsa or ESD.
[INDENT]Correct beep-media-player configuration:
[[IMG]http://img100.echo.cx/img100/7397/screenshotbmppreferences3np.th.png[/IMG]](http://img100.echo.cx/my.php?image=screenshotbmppreferences3np.png)
[/INDENT]
***** If you couldn't play any sounds using ALSA then your /etc/asound.cond & /etc/esound/esd.conf needs some more advanced tweaking (or your sound card just won't support it).

***** The codes above are to be done inside a terminal window.

Thanks to [varunus](http://ubuntuforums.org/member.php?userid=2328) for the [original](http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound) HowTo and to [Vaportrail](http://ubuntuforums.org/member.php?userid=5069) for the correct /ets/asound.conf contents.

Enjoy everyone :D.

---

### Post by Xian on 2005-05-06
Thanks so much for posting this. I'd given up and was using polypaudio.
The method you presented worked great!

---

### Post by Gandalf on 2005-05-06
[QUOTE=Xian]Thanks so much for posting this. I'd given up and was using polypaudio.
The method you presented worked great![/QUOTE]
 no problem, i just made it clearer :D

---

### Post by mostwanted on 2005-05-06
Thanks! It works great.

---

### Post by dukeinlondon on 2005-05-06
you might find that realplayer still doesn't work after switching to alsa. this is because it is looking for /dev/dsp which is the oss device. Fortunately, alsa includes oss emulation. to enable it, just type 

```
modprobe -v snd-pcm-oss
```

this will create the /dev/dsp device, routed to alsa. 

Realplayer (and other oss only apps, no doubt) then works.

If that works fine, then just add snd-pcm-oss to the file /etc/modules

it will be loaded automatically at boot.

---

### Post by nix4me on 2005-05-06
excellent!  Finally a fix for sound problems!  Developers - Please fix it this way in the next release!

nix

---

### Post by bored2k on 2005-05-06
[QUOTE=dukeinlondon]you might find that realplayer still doesn't work after switching to alsa. this is because it is looking for /dev/dsp which is the oss device. Fortunately, alsa includes oss emulation. to enable it, just type 

```
modprobe -v snd-pcm-oss
```

this will create the /dev/dsp device, routed to alsa. 

Realplayer (and other oss only apps, no doubt) then works.

If that works fine, then just add snd-pcm-oss to the file /etc/modules

it will be loaded automatically at boot.[/QUOTE]
 It worked without that here.

---

### Post by NeoChaosX on 2005-05-06
period_size 2048	#1024
buffer_size 32768	#4096

Using these values caused my SDL games to go out of sync. If I use the smaller values, the sync is fixed but some videos have scratchy sound.  ](*,)

---

### Post by kb00heda on 2005-05-07
Gandalf: 

Just wanted to say that your HOWTO worked for me too. Thanks!  :)

---

### Post by Gandalf on 2005-05-07
[QUOTE=kb00heda]Gandalf: 

Just wanted to say that your HOWTO worked for me too. Thanks!  :)[/QUOTE]
 no problem

---

### Post by Vagabund on 2005-05-07
Thank's Gandalf,

after this modifications i can hear music with the BeepMediaPlayer and can start a video with gxine without a delayed audio  :) . But i have still the problem with the RealPlayer. If i see a video with the RealPlayer all other sounds are down. The BeepPlayer shows the problem report "Can't open audio, please check the plugin...". Dukeinlondon's tip had no result. Any other tip's?

Regards
Michael

---

### Post by pauloslf on 2005-05-07
you're the man!! thanks 
 \\:D/  \\:D/  a lot ...

---

### Post by psoleko on 2005-05-07
Works great for me too. Only weird thing I noticed that when you hit test in the default-source section of gstreamer-properties I get this message "Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'" I think this is a specific issue with the test function, because everything else is working beautifully. Thanks Gandalf.

---

### Post by manadskort on 2005-05-08
when i did this im unable to hear the system sounds and xmms vlc sounds, just skype sounds.

What did i do wrong?

---

### Post by Arthemys on 2005-05-08
[QUOTE=manadskort]when i did this im unable to hear the system sounds and xmms vlc sounds, just skype sounds.

What did i do wrong?[/QUOTE]

I'm having the same issue right now, apparently there's a 'thing' where two different applications can't be writing to the same sound server. You'd think that would be possible... I mean even DirectX can do that.

---

### Post by joekr on 2005-05-08
While this method DOES work, I noticed that my avis and mpgs all play choppy.  Having multiple sounds play is great, but not at the cost of video framerates.

Excellent tut, but not for me.

---

### Post by nehalem on 2005-05-09
[QUOTE=joekr]While this method DOES work, I noticed that my avis and mpgs all play choppy.  Having multiple sounds play is great, but not at the cost of video framerates.

Excellent tut, but not for me.[/QUOTE]

Is this consistent for people?

What are the advantages of doing this, i thought they used Alsa by default anyway?  When programs use dev/dsp does it no longer lock out everything else from using the sound device (like flash)?

I really just hope we can get polypaudio in the next version, seems a lot better.

---

### Post by nehalem on 2005-05-09
Well I just gave in and tried it.  Everything works pretty good but some things I still have issues with, namely stuff that uses /dev/dsp (vmware) will hog all the sound.  Anyway to point stuff to use ESD instead or something?

---

### Post by DKnight768 on 2005-05-09
After following this guide my SDL games ran horribly slow :-| so I just had to revert the process  ](*,)

---

### Post by Gandalf on 2005-05-09
it's weird for some it doesn't work :o it works with every program/game for me :o

---

### Post by manadskort on 2005-05-09
[QUOTE=Gandalf]it's weird for some it doesn't work :o it works with every program/game for me :o[/QUOTE]
 thanks for the great how to :).

When the system is heavy loaded, the sounds starts to sound wierd on skype, and sometimes i looses the connection.
Isnt that wierd?

I would be very happy if someone could tell me how to hear xmms sounds at the same time with the skype sounds.

---

### Post by McQuaid on 2005-05-09
Hello, I'm going to post my asound.conf file if others are having issues.  The main reaon I'm posting is, looking over yours Gandalf, I don't think yours is setup for fullduplex operation.  The only mixing going on with yours is for output not input.  Now, I'm definately not an expert on creating these, but someone who seemed to know a fair amount about these configs on #alsa helped me.

```
pcm.card0 {
  type hw
  card 0
# mmap_emulation true
}

#pcm.dmix0 {
#  type dmix 
#  ipc_key 34521 
#  slave {
#    pcm "card0" 
#  }
#}


pcm.dmix0 {
	type dmix
	ipc_key 1024 ## needs to be a power of 2
	slave {
		pcm "hw:0"
		period_time 0
		period_size 1024
		buffer_size 8192
               # format S16_LE
		rate 44100 ## not necessary
	}
#slowptr true
}





pcm.dsnoop0 {
  type dsnoop 
  ipc_key 2048
  slave {
    pcm "card0" 
  #  rate 48000
  }
}

pcm.asym0 {
  type asym 
  playback.pcm "dmix0" 
  capture.pcm "dsnoop0"
}

pcm.pasym0 {
  type plug 
  slave.pcm "asym0"
}

# 'dsp0' is espected by OSS emulation etc.
pcm.dsp0 {
  type                  plug
  slave.pcm             "asym0"
}

ctl.dsp0 {
    type                hw
    card                0
}

pcm.!default {
  type                  plug
  slave.pcm             "asym0"
}

ctl.!default {
    type                hw
    card                0
}
``` 

With this config, I can run multiple xmms's, beeps, rhtyhm or pretty much whatever while recording at the same time.  You can test yours by running a player and then launching arecord from the cli.  

About the rate setting, the person helping me with my config insisted that I don't need it, but when running esd, sound would be scratchy without it.  Again, not being an expert on these things, I think it's beneficial to have the rate at your sound cards native rate, most cards are 48000 so change that if needed.

Also you might find sdl games no longer have sound here's a fix:

    *  SDL - now time to change behaviour of apps which uses SDL to play sound. SDL tries to use hw:0, and without intervention, it fails to open audio device. But SDL uses AUDIODEV environment variable, so it placed such file to /etc/profile.d/, example dmix_sdl.sh:

export AUDIODEV=default

 
and finally mplayer can be modified within the gui (gmplayer) but mplayer alone won't read that. Here's my    ~/.mplayer/config
vo="xv"
ao="alsa:device=default"

The vo="xv" will set mplayer to use xv hardware overlay for video so most of you will want that as well if you haven't set it as such.  I'm mainly use totem but it's nice to have mplayer working with this setup.

And the gstreamer-properties test with this setup will work for both playback and recording.

As gandalf said, with certain sound setups you might have issues, if so look at this page and search for your soundcard (it's where I got most of my info)

[http://alsa.opensrc.org/index.php?page=DmixPlugin](http://alsa.opensrc.org/index.php?page=DmixPlugin) 


and here at the same site their quick n dirty dmix esd arts sdl how to

[http://alsa.opensrc.org/index.php?page=Dmix+Kde+-+arts%2C+ESD+and+SDL+quick+and+dirty+HOWTO](http://alsa.opensrc.org/index.php?page=Dmix+Kde+-+arts%2C+ESD+and+SDL+quick+and+dirty+HOWTO) 

My final comment on this is two issues.  This works for 99% of apps out there, but some older apps don't map properly, for ex I couldn't get quake3/et and teamspeak to play nice, but this is because my onboard sound only has software mixing, those with hardware mixing shouldn't have issue.

The other thing is I like to use the gnome option for another user to login without logging me out.  But running esd in the one login holds the card, so the other user gets no sound.  Again not sure if this is the case with hardware mixing cards.  If someone could test that out, I'm curious.

---

### Post by Rehevkor on 2005-05-10
Excellent how-to. Most of my games (UT2004, SimCity 3000U, Enemy Territory) required that I kill esd before being able to play with sound, and I always had to reboot afterward to get sound in Ubuntu back. After following this guide, the sound works flawlessly in everything. No more killing esd and rebooting! Thanks :D

---

### Post by Gandalf on 2005-05-11
[QUOTE=Rehevkor]Excellent how-to. Most of my games (UT2004, SimCity 3000U, Enemy Territory) required that I kill esd before being able to play with sound, and I always had to reboot afterward to get sound in Ubuntu back. After following this guide, the sound works flawlessly in everything. No more killing esd and rebooting! Thanks :D[/QUOTE]
 no problem, just for your record, no need to reboot ubuntu juste type [color=blue]esd[/color] in a console will turn on ESD again

---

### Post by dhega on 2005-05-11
wee
Nice guide.

---

### Post by manadskort on 2005-05-11
is it just me?

I cant play music with xmms at the same time that im using skype.

---

### Post by McQuaid on 2005-05-11
Oh and for sdl games, install libsdl1.2debian-alsa

You could install the esd version but both will work and this way you can have sdl games work in another window manager where you might not be running esd.

It defaulted to libsdl1.2debian-oss.  Not sure exactly why that doesn't work when alsa has oss emulation.  

But really, can we not purge oss completely from a distribution yet?

---

### Post by Jump on 2005-05-12
Work great, thanks!

---

### Post by Rehevkor on 2005-05-12
[QUOTE=Gandalf]no problem, just for your record, no need to reboot ubuntu juste type [color=blue]esd[/color] in a console will turn on ESD again[/QUOTE]
 Well, I did that, but it would just play a series of pc speaker beeps and the interface sounds in Ubuntu still wouldn't play. It would only work if I rebooted.

Fortunately, I don't have to worry about that now :)

---

### Post by nt7561 on 2005-05-12
I have a soundblaster 24bit live on board card. Is this guide working for it also?

---

### Post by mortram on 2005-05-12
I tried this guide to get my M-Audio USB Quattro playing back w/o scratchy sound through ESD... worked wonderfully for the audio.

Unfortunately it seems to break my USB Best Data 56k modem, using the slmodem-2.9.10_USB package...


I've confirmed this a couple of times.  Being new to linux, I reformatted, reinstalled Hoary.  Modem works until I use this guide, then it doesn't!

Sound is great, but not quite as important as my internet connection.  Is there a way the two can be reconciled or any clue as to why this would happen?

---

### Post by Gandalf on 2005-05-12
[QUOTE=mortram]I tried this guide to get my M-Audio USB Quattro playing back w/o scratchy sound through ESD... worked wonderfully for the audio.

Unfortunately it seems to break my USB Best Data 56k modem, using the slmodem-2.9.10_USB package...


I've confirmed this a couple of times.  Being new to linux, I reformatted, reinstalled Hoary.  Modem works until I use this guide, then it doesn't!

Sound is great, but not quite as important as my internet connection.  Is there a way the two can be reconciled or any clue as to why this would happen?[/QUOTE]
 is there any configuration file of this modem drivers? if yes try to make it use Alsa instead of ESD

---

### Post by mortram on 2005-05-12
it's not configured for ALSA or ESD, there's no sound output.   It's not that the switch to ALSA breaks the sound on the modem, it breaks the modem itself, which only spits out NO CARRIER messages after the switch to ALSA and won't pick up the line or dial.  here's the makefile if that's of any consequence:

###########################################################################
#
#
#       Makefile  --  modem Makefile.
#
#       Copyright(c) 2003, Smart Link Ltd. ([www.smlink.com](www.smlink.com))
#	All rights reserved.
#
#       Author: Sasha K (sashak@smlink.com)
#
#
###########################################################################
#
###########################################################################

KERNEL_DIR:=/lib/modules/$(shell uname -r)/build

# tools
INSTALL:=install

all: modem
#all: modem drivers

modem:
	$(MAKE) -C $@ all

install: all install-drivers
	$(INSTALL) -D -m 755 modem/slmodemd ${DESTDIR}/usr/sbin/slmodemd
	$(RM) -rf ${DESTDIR}/var/lib/slmodem
	$(INSTALL) -d -D -m 755 ${DESTDIR}/var/lib/slmodem

uninstall: uninstall-drivers
	$(RM) ${DESTDIR}/usr/sbin/slmodemd
	$(RM) -rf ${DESTDIR}/var/lib/slmodem

drivers:
	$(MAKE) -C drivers KERNEL_DIR=$(KERNEL_DIR)

install-drivers: drivers
	$(MAKE) install -C drivers KERNEL_DIR=$(KERNEL_DIR)
uninstall-drivers:
	$(MAKE) uninstall -C drivers KERNEL_DIR=$(KERNEL_DIR)

# misc rules
sub-dirs:= modem drivers
.PHONY: $(sub-dirs) all old clean dep install
clean dep: %: %-sub-dirs
%-sub-dirs:
	$(foreach dir,$(sub-dirs),$(MAKE) -C $(dir) $(patsubst %-sub-dirs,%,$@) && ) echo "done."

---

### Post by mortram on 2005-05-13
appears to be something called in the asound.conf, I tried commenting/uncommenting sections to see what happened (the expressions themselves make almost no sense to me other than the sample rates, etc.).  It seems with the asound, I can either get the modem & no sound, the modem and scratchy sound, or great sound and no modem.

I found the polypaudio packages in Synaptic and installed those... on reboot the sound is clear and the modem's working, so I guess I've found my solution.  

Thanks for the suggestions and the tutorial.

---

### Post by crash369 on 2005-05-14
so far, most everything i've tried work - xmms, totem, flash, OS sounds.  the only thing that doesn't work is mplayer.

when i try to open anything with mplayer, i get "Could not open/initialize audio device -> no sound." error.

for settings, i have tried blank ao, ao=alsa, and ao=alsa:device=default

does anyone know how to fix this?

---

### Post by NeoChaosX on 2005-05-14
[QUOTE=NeoChaosX]period_size 2048	#1024
buffer_size 32768	#4096

Using these values caused my SDL games to go out of sync. If I use the smaller values, the sync is fixed but some videos have scratchy sound.  ](*,)[/QUOTE]
So nobody can help me with this issue?

---

### Post by arrizaba on 2005-05-14
Same problems here: mplayer does not work and games that use SDL sounds freeze if another application with sound is on.   
Any solutions :???: 
I tried the ones posted in this forum, no success...

---

### Post by passcode on 2005-05-15
Nice Job  \\:D/

---

### Post by hyapadi on 2005-05-15
[QUOTE=Gandalf]Hello there,
This is just a clean and better organised guide of varunus's HowTo located [here](http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound). So primarily all the credits go to him.

This HowTo will give you instruction on enabling software mixing, to avoid application problems like Audacity needing killall esd to work as well as Skype [now Skype will no longer crash if you receive a message or a call (when it try to play sound in fact)], so let's get to work shall we ?? :-P.


[list=1]We need to install libesd-alsa0 so
```

sudo apt-get install libesd-alsa0

```

[*]We need to create /etc/asound.conf, so
```

sudo gedit /etc/asound.conf

```
Insert into it:
```

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048	#1024
buffer_size 32768	#4096
			#periods 128
rate 48000		#44100
}
bindings {
0 0
1 1
}
}

```

[*]We need to change /etc/esound/esd.conf contents so:
```

sudo mv /etc/esound/esd.conf /etc/esound/esd.conf_backup
sudo gedit /etc/esound/esd.conf

```
Insert into it:
```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```

[*]Now **You** need to change ubuntu sound server to alsa (you can leave it ESD but better use alsa because it has better sound handling):
```

gstreamer-properties

```
Change both (in the Audio Tab not the Video) from ESD to ALSA so it looks just like the picture:
[[IMG]http://img104.echo.cx/img104/3140/screenshotmultimediasystemssel.th.png[/IMG]](http://img104.echo.cx/my.php?image=screenshotmultimediasystemssel.png)
[/list]
All that's left now is to restart your computer (after restart you must hear sound) to enable these changes. Also configure XMMS or Beep-media-player (or any player) to use ALSA instead of eSound/ESD. If you hear a strange sound, just change everything back to ESD. If everything worked correctly, now Audacity & Skype will work normally and all the program will play sound using either Alsa or ESD.
[INDENT]Correct beep-media-player configuration:
[[IMG]http://img100.echo.cx/img100/7397/screenshotbmppreferences3np.th.png[/IMG]](http://img100.echo.cx/my.php?image=screenshotbmppreferences3np.png)
[/INDENT]
***** If you couldn't play any sounds using ALSA then your /etc/asound.cond & /etc/esound/esd.conf needs some more advanced tweaking (or your sound card just won't support it).

***** The codes above are to be done inside a terminal window.

Thanks to [varunus](http://ubuntuforums.org/member.php?userid=2328) for the [original](http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound) HowTo and to [Vaportrail](http://ubuntuforums.org/member.php?userid=5069) for the correct /ets/asound.conf contents.

Enjoy everyone :D.[/QUOTE]

I follow this tutorial and now I lost all the sounds. How to undo these changes?

Thanks

---

### Post by Gandalf on 2005-05-15
[QUOTE=hyapadi]I follow this tutorial and now I lost all the sounds. How to undo these changes?

Thanks[/QUOTE]
 well delete /etc/asound.conf
cp /etc/esound/esd.conf_backup to /etc/esound/esd.conf
and remove the apt-getted packages

---

### Post by stoffe on 2005-05-15
I'm probably not the first to wonder this, but is there any possibility of a good config like this getting into the default installation? And in the meantime, having it as a package that can be installed (via backports perhaps?)

It's a huge annoyance especially as it seems solutions are well known. Especially now when I'm converting people with my new Ubuntu CD:s this is one of the issues that makes even hardened commandline geeks roll their eyes...

Not to be too negative though, I'm happy there are solutions, just wondering if the solutions are generic enough to include from the start, and asking if it is possible.

---

### Post by Gandalf on 2005-05-15
[QUOTE=stoffe]I'm probably not the first to wonder this, but is there any possibility of a good config like this getting into the default installation? And in the meantime, having it as a package that can be installed (via backports perhaps?)

It's a huge annoyance especially as it seems solutions are well known. Especially now when I'm converting people with my new Ubuntu CD:s this is one of the issues that makes even hardened commandline geeks roll their eyes...

Not to be too negative though, I'm happy there are solutions, just wondering if the solutions are generic enough to include from the start, and asking if it is possible.[/QUOTE]
 well it's not in default installation because not all audio card support this and this topic proove this

---

### Post by Leira on 2005-05-22
i followed this approch, and my rhythmbox, xmms and mplayer r all works well. but when i use esd failed, when i tried "esd -d default", it said:
- using device default
default: No such file or directory
and my mpd (with mixer_type "alsa" and mixer_device "default") failed with same message.

---

### Post by Leira on 2005-05-23
i am using ubuntu amd64, and there is no libesd-alsa0 package on this arch. i downloaded the esound src package, and modified the debian/control file, added amd64 arch to libesd-alsa0 package, and recompile the deb package my self. i installed this libesd-alsa0 amd64 package, but it still has problem with alsa using dev default:
```
- using device default
default: No such file or directory
```
it seems the libesd-alsa0 package on amd64 arch is not workable, it still use oss, and maybe this is it is not included in amd64 arch officially.

i have to use aoss to start esd, but i cannot where gnome start it. so i used a temporary solution:
1. mv /usr/bin/esd /usr/bin/esd.orig
2. make a script /usr/bin/esd:
```
#!/bin/sh

aoss /usr/bin/esd.orig $*
```

now, it just can work, and the gnome's event sound as well.

---

### Post by McQuaid on 2005-05-24
I'm not up to speed on amd stuff.  Aren't all amd chips x86 compat? or just not the amd64 ones?

---

### Post by fackamato on 2005-05-25
[QUOTE=McQuaid]I'm not up to speed on amd stuff.  Aren't all amd chips x86 compat? or just not the amd64 ones?[/QUOTE]

All AMD CPU's are x86 compatible of course.

By the way, I'm using this /etc/asound.cfg :

> pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,1"
period_time 0
period_size 1024
buffer_size 4096
periods 128
rate 44100
}
bindings {
0 0
1 1
}
}


And this /etc/esound/esd.conf :

> [esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=


And using the esd sound server for gnome sounds, beep-media-player uses alsa. So, everything works (several applications can use the sound card at once).

---

### Post by daveman on 2005-05-30
After doing this my IBM Thinkpad R51 beeps on all sorts of actions even with my main and mono mixes muted.  Closing windows, new email, prompts, etc.  How can I make it not do that?  Thanks

---

### Post by rabidninjawombat on 2005-06-08
[QUOTE=McQuaid]Hello, I'm going to post my asound.conf file if others are having issues.  The main reaon I'm posting is, looking over yours Gandalf, I don't think yours is setup for fullduplex operation.  The only mixing going on with yours is for output not input.  Now, I'm definately not an expert on creating these, but someone who seemed to know a fair amount about these configs on #alsa helped me.
.[/QUOTE]


Thanks!  Your asound.cfg worked fine :)  can now listen to multiple sounds!  Great help guys!

---

### Post by kiddyfurby on 2005-06-08
I have every program using dmix happily but skype
any idea?
skype is taking over the whole sound system

---

### Post by ksmith on 2005-06-13
Has anyone got this working with an amd64? Step 1 gives me the following:
```
kcs@xorb:~$ sudo apt-get install libesd-alsa0
Reading package lists... Done
Building dependency tree... Done
Package libesd-alsa0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libesd-alsa0 has no installation candidate
kcs@xorb:~$
```
I'd love to do this howto but it doesn't appear amd64 friendly.

---

### Post by ChamPro on 2005-06-14
[QUOTE=McQuaid]Hello, I'm going to post my asound.conf file if others are having issues.  The main reaon I'm posting is, looking over yours Gandalf, I don't think yours is setup for fullduplex operation.  The only mixing going on with yours is for output not input.  Now, I'm definately not an expert on creating these, but someone who seemed to know a fair amount about these configs on #alsa helped me.

```
pcm.card0 {
  type hw
  card 0
# mmap_emulation true
}

#pcm.dmix0 {
#  type dmix 
#  ipc_key 34521 
#  slave {
#    pcm "card0" 
#  }
#}


pcm.dmix0 {
	type dmix
	ipc_key 1024 ## needs to be a power of 2
	slave {
		pcm "hw:0"
		period_time 0
		period_size 1024
		buffer_size 8192
               # format S16_LE
		rate 44100 ## not necessary
	}
#slowptr true
}





pcm.dsnoop0 {
  type dsnoop 
  ipc_key 2048
  slave {
    pcm "card0" 
  #  rate 48000
  }
}

pcm.asym0 {
  type asym 
  playback.pcm "dmix0" 
  capture.pcm "dsnoop0"
}

pcm.pasym0 {
  type plug 
  slave.pcm "asym0"
}

# 'dsp0' is espected by OSS emulation etc.
pcm.dsp0 {
  type                  plug
  slave.pcm             "asym0"
}

ctl.dsp0 {
    type                hw
    card                0
}

pcm.!default {
  type                  plug
  slave.pcm             "asym0"
}

ctl.!default {
    type                hw
    card                0
}
```[/QUOTE]
Finally, an asoud.conf that works for my sound card (which is whatever on-board card is on the Centrino in a Dell Inspiron 8600). I now have no lag in my videos or mp3s! Thanks!

[QUOTE=McQuaid]and finally mplayer can be modified within the gui (gmplayer) but mplayer alone won't read that. Here's my    ~/.mplayer/config
vo="xv"
ao="alsa:device=default"

The vo="xv" will set mplayer to use xv hardware overlay for video so most of you will want that as well if you haven't set it as such.  I'm mainly use totem but it's nice to have mplayer working with this setup.
[/QUOTE]
Unrelated... but I still can't get the xv option to display at the correct aspect ratio... ah well.

---

### Post by Rickie on 2005-06-14
None of the asound's posted let me have multiple programs using Alsa at the same time, i get An error saying the device 'Alsa' is already in use, and some programs dont even load untill i close the other program that was using Alsa. :(

---

### Post by fabiuu on 2005-06-26
that's great! worked fine here.

just one little thing.

i couldn't get xmms and aMSN working together, but is really simple

just set the sound server from "play $sound" to "aplay $sound" (alsa i suppose)

tks!

---

### Post by fabiuu on 2005-06-26
[QUOTE=Rickie]None of the asound's posted let me have multiple programs using Alsa at the same time, i get An error saying the device 'Alsa' is already in use, and some programs dont even load untill i close the other program that was using Alsa. :([/QUOTE]
 Maybe you have to update alsa:

sudo apt-get install libesd-alsa0

---

### Post by Jesus Franco on 2005-06-26
Breezy fixed this issue btw. But once agian very good fix for Horay users.  :)

---

### Post by twowheeler on 2005-06-27
[QUOTE=McQuaid]Hello, I'm going to post my asound.conf file if others are having issues.  The main reaon I'm posting is, looking over yours Gandalf, I don't think yours is setup for fullduplex operation.  The only mixing going on with yours is for output not input.  Now, I'm definately not an expert on creating these, but someone who seemed to know a fair amount about these configs on #alsa helped me.[/QUOTE]
I tried both of these asound.conf's.  Gandalf's worked ok but did not solve the problem of audacity coughing up errors.  McQuaid's gave me horrible scratchy sound so I killed that one.  So I am back to Gandalf's original approach.

But I also have a little hackery that allows audacity to start, and should help with anything else that does not like esd.  It is a wrapper script that turns off esd temporarily and then restarts it.  

Create a file /usr/bin/esdoss with these contents.
```
#! /bin/sh
gconftool-2 --set --type bool /desktop/gnome/sound/enable_esd "false"
exec "$@"
gconftool-2 --set --type bool /desktop/gnome/sound/enable_esd "true"
```
Make this file executable:
```
sudo chmod a+x /usr/bin/esdoss
```
Then edit the menu entry for audacity to include this wrapper script.  I did this with smeg.
```
/usr/bin/esdoss audacity
```
You can do the same with other programs if they have sound issues under esd.  

If you kill your system following these instructions, I don't know nothing about it.  I swear.
:-)

---

### Post by WMCoolmon on 2005-07-05
I too am using AMD64, and can't do this Howto. :/

---

### Post by zue on 2005-07-12
[QUOTE=ksmith]Has anyone got this working with an amd64? Step 1 gives me the following:
```
kcs@xorb:~$ sudo apt-get install libesd-alsa0
Reading package lists... Done
Building dependency tree... Done
Package libesd-alsa0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libesd-alsa0 has no installation candidate
kcs@xorb:~$
```
I'd love to do this howto but it doesn't appear amd64 friendly.[/QUOTE]

Yup.  Same here.  Does anyone know if getting multiple sounds to work is possible with amd64?

---

### Post by filemanager on 2005-07-12
[QUOTE=zue]Yup.  Same here.  Does anyone know if getting multiple sounds to work is possible with amd64?[/QUOTE]
 I get that same error :(

---

### Post by DancingSun on 2005-07-12
I believe it's because libesd0-alsa is not available on the AMD64 repositories.

I've requested this in the backports forum about a week ago, but so far no reponse, and the post is already pushed down to the 3rd page ... :(

It's a pity that AMD64 application support for Ubuntu seems to be neglected.

---

### Post by filemanager on 2005-07-12
[QUOTE=DancingSun]I believe it's because libesd0-alsa is not available on the AMD64 repositories.

I've requested this in the backports forum about a week ago, but so far no reponse, and the post is already pushed down to the 3rd page ... :(

It's a pity that AMD64 application support for Ubuntu seems to be neglected.[/QUOTE]
 I feel so neglected. ;)

Do you think in the next release (when is that.. October?) AMD64 systems will have more application support?

It would be nice to have sound ([http://www.ubuntuforums.org/showthread.php?t=48490)](http://www.ubuntuforums.org/showthread.php?t=48490)). sigh.

---

### Post by JoeyrS on 2005-07-17
Congrats :-)
Your tutorial is very helpful.

---

### Post by tlaloczint on 2005-07-18
hi to all I have a problem following this tutorial and ths is what I got 

gstreamer-properties

** (gstreamer-properties:9102): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/icons/SphereCrystal/scalable/stock: Image file '/usr/share/icons/SphereCrystal/scalable/stock' contains no data


(gstreamer-properties:9102): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(gstreamer-properties:9102): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(gstreamer-properties:9102): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(gstreamer-properties:9102): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(gstreamer-properties:9102): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(gstreamer-properties:9102): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(gstreamer-properties:9102): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(gstreamer-properties:9102): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(gstreamer-properties:9102): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(gstreamer-properties:9102): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(gstreamer-properties:9102): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(gstreamer-properties:9102): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

if someone can help me please

---

### Post by NeoChaosX on 2005-07-18
> ** (gstreamer-properties:9102): WARNING **: Pixbuf theme: **Cannot load pixmap file /usr/share/icons/SphereCrystal/scalable/stock: *Image file*** '/usr/share/icons/SphereCrystal/scalable/stock' contains no data

This has nothing to do with the sound fixes. It's complaining about missing files in the iconset you're using.

---

### Post by DiGiTaLFX on 2005-07-23
[QUOTE=Gandalf]Change both (in the Audio Tab not the Video) from ESD to ALSA[/QUOTE]
Hi I've just tried doing this part, and its fine for sink (as in click test plays a sound fine) but for source if I click test I get the message:
> Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'
Any idea why this is?
Thanks
DiGiTaLFX

---

### Post by varunus on 2005-07-23
This is because gandalf's original settings don't allow for "full duplex" (the ability to record and play at the same time).  Use the following /etc/asound.conf for full duplex (or at least, it works for me):

```

pcm.card0 {

  type hw

  card 0

  mmap_emulation true

}

#DMIX output device
pcm.!output {
type dmix
ipc_key 1234
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024
buffer_size 8192
rate 44100
}
bindings {
0 0
1 1
}
}

#
# DSNOOP input device
#
pcm.!input {
type dsnoop
ipc_key 4321
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024
rate 44100
}
}

#
# ASYM duplex device
#
pcm.!duplex {
type asym
playback.pcm "output"
capture.pcm "input"
}

#
# Make the duplex device default
#
pcm.!default {
type plug
slave.pcm "duplex"
}

#
# OSS Compability

pcm.!dsp0 {
type plug
slave.pcm "duplex"
}

ctl.!mixer0 {
type hw
card 0
}

```

---

### Post by DiGiTaLFX on 2005-07-23
OK that half does it. But sound was very distorted it seemed, and clicking test on the source worked, but then clicking ok crashed the program. I've gone back to other other config for now. But i think I'll do a bit of reading about this once i've got a properly working system (low priority for me atm).
Cheers neway
DiGiTaLFX

---

### Post by NeoChaosX on 2005-07-23
Varunus:
> pcm.!duplex {
type asym
playback.pcm "output"
capture.pcm "input"
}
Don't do this. This part of your config breaks quite a few things, including sound in Gaim. The [other thread about setting up duplex sound](http://www.ubuntuforums.org/showthread.php?t=44753), on page 5, instructs you should have that section set up like this:
> pcm.!default {
    type plug
    slave.pcm "output"
}

---

### Post by varunus on 2005-07-23
I haven't had any problems using this config on my sound card.  (Everything works for me...haven't run into an app yet that doesn't have sound and is supposed to...)  My sound card isn't exactly that great either, its one of those intel integrated AC97 ones.  Ah well, I guess that config doesn't work for everyone.  Thanks for the warning.

---

### Post by André on 2005-07-24
Hi,

your HowTo worked great for me. Sound whereever and whatever i click or run ;-)

I just wanted to contribute that when i set the KDE sound daemon via kcontrol to ESD i even get sound in KDE apps while running Gnome (what didn't work for me before).

I use some apps in Gnome like the nice K3B and Kile. And now they work with sound and integrate even better that way...

... so what i just trying to say: Thank you!

Greetings
André

---

### Post by tseliot on 2005-07-24
[QUOTE=varunus]This is because gandalf's original settings don't allow for "full duplex" (the ability to record and play at the same time).  Use the following /etc/asound.conf for full duplex (or at least, it works for me):

```

pcm.card0 {

  type hw

  card 0

  mmap_emulation true

}

#DMIX output device
pcm.!output {
type dmix
ipc_key 1234
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024
buffer_size 8192
rate 44100
}
bindings {
0 0
1 1
}
}

#
# DSNOOP input device
#
pcm.!input {
type dsnoop
ipc_key 4321
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024
rate 44100
}
}

#
# ASYM duplex device
#
pcm.!duplex {
type asym
playback.pcm "output"
capture.pcm "input"
}

#
# Make the duplex device default
#
pcm.!default {
type plug
slave.pcm "duplex"
}

#
# OSS Compability

pcm.!dsp0 {
type plug
slave.pcm "duplex"
}

ctl.!mixer0 {
type hw
card 0
}

```[/QUOTE]

It did the trick for me. At least it made ALSA work again on my computer. No multiple sounds though.

Thanks anyway

---

### Post by charlieg on 2005-07-24
Working great for me.  Many moons ago I did this in Gentoo as well, so as soon as I saw ESD in top, I scrambled straight to this thread.

---

### Post by jamaas on 2005-07-26
Hi Guys,

Thanks for this, for a newbie can you please tell me how/where to
"change ubuntu sound server to alsa" ??

I'm running hoary on a dell d410 notebook.

Thanks


   4. Now You need to change ubuntu sound server to alsa (you can leave it ESD but better use alsa because it has better sound handling):
      Code:

      gstreamer-properties


      Change both (in the Audio Tab not the Video) from ESD to ALSA so it looks just like the picture:
      [http://img104.echo.cx/img104/3140/s...stemssel.th.png](http://img104.echo.cx/img104/3140/s...stemssel.th.png)

---

### Post by bored2k on 2005-07-26
[QUOTE=jamaas]Hi Guys,

Thanks for this, for a newbie can you please tell me how/where to
"change ubuntu sound server to alsa" ??

I'm running hoary on a dell d410 notebook.

Thanks


   4. Now You need to change ubuntu sound server to alsa (you can leave it ESD but better use alsa because it has better sound handling):
      Code:

      gstreamer-properties


      Change both (in the Audio Tab not the Video) from ESD to ALSA so it looks just like the picture:
      [http://img104.echo.cx/img104/3140/s...stemssel.th.png](http://img104.echo.cx/img104/3140/s...stemssel.th.png)[/QUOTE]
 In your upper panel: System - Preferences - Multimedia Streams Selector

---

### Post by songochain on 2005-07-26
i've a problem with e17 and polyaudio. I cant get fullscreen into e17 using mplayer but in gnome i havent this problem. I know it's polyaudio because before i could get fullscreen but i've installed polyaudio to can hear multiple sounds. 
 Any idea?
 thanks

---

### Post by jonny on 2005-08-05
Fabulous.  I couldn't get Skype working - it used to hang whenever I tried to dial out - and I tried this how-to in desperation.

It worked like a charm.  Thank you.

---

### Post by ubuntu_cork on 2005-08-16
hi folks, thanks for the heads up with the sound, got sound output no problem
using a cmi8738 cheap chip works great
only thing is when trying to record sound from mic
it works fine under xp.
not that i want it too...
but its our killer app here, skype.
no skype means my wife will be reliant on xp, and otherwise we are soo happy with ubuntu and kubuntu
tried all the usual combos of switchs that are in kmixer etc...
nothing seems to work,
except one thing,
with them all on, i get perfect mic playback
but the pcm is on full volume for record for this to happen
also sound is then distorted on playback
not what i was hoping for

Can anyone offer any help i think the solution is to max out pcm for input
but have it much lower for output of normal sound
I dont know how to achieve this.


Can anyone help or point me in the right direction?
ps, dont tell me google...4 days of googling=bfz
where bfz=big fat zero!

thanks in advance

Mick.  O:)

---

### Post by mrguytx on 2005-08-16
thanks, my sound is now screwed, I have neither ALSA nor ESD.
sheesh.

---

### Post by j.hill on 2005-08-22
I tried this procedure because I have no audio in Totem -- video only.  But I *still* have no audio.  What else can I try?  

I already have libdvdcss2 and libdvdread.

All I want is to play frickin' DVDs!!  

[shakes fist at computer]

---

### Post by Turb0flat4 on 2005-09-12
Just wanted to register and say a big THANK YOU !! to gandalf and varunu for an excellent Howto. Now my new Ubuntu box can use mplayer without a hitch. 

You guys are the best ! Keep it up. :)

---

### Post by patricia on 2005-09-16
[QUOTE=jonny]Fabulous.  I couldn't get Skype working - it used to hang whenever I tried to dial out - and I tried this how-to in desperation.

It worked like a charm.  Thank you.[/QUOTE]


Hey Guys!

My skype doesn't ring, but I a answer I call i can hear the other side and so they can hear me, but it just don't ring when I got ou made a call. What's wrong? How can I fix it?

Thanks

---

### Post by patricia on 2005-09-18
Hey Guys!

It did work for me, but only for a little time. Sumetimes I need to use vmware and also skpye and now all my sound system is crazy!!! Even AMSN is not working with sound any more :(  And also rythmbox, that always work before, did not work now! :(

I've tryied polypaudio but it didn't work too! Could, please, some one help me!


Thanks!

---

### Post by thezerogroup on 2005-09-21
I've followed the above directions, however when I type in:
```

#aplay /usr/share/sounds/login.wav
ALSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave

```

I then type:
```

#esd 

```
I get the same message as above. Any ideas?

---

### Post by calliari on 2005-09-21
This things don't works for me... I can't play more then one sound at the same time.

I'm using an Ensonic Sound Card.

Xmms is working with alsa, with this configuration:

Alsa 1.2.10 output plugin

Audio Device: hw:0,1
Mixer Card: 0
Mixer Device: PCM

Ubuntu 5.04

Do you have some idea?

I did the complete process describe in teh beginning of this topic.

thank you...

---

### Post by ubuntu_cork on 2005-09-22
[QUOTE=ubuntu_cork]hi folks, thanks for the heads up with the sound, got sound output no problem
using a cmi8738 cheap chip works great
only thing is when trying to record sound from mic
it works fine under xp.
not that i want it too...
but its our killer app here, skype.
no skype means my wife will be reliant on xp, and otherwise we are soo happy with ubuntu and kubuntu
tried all the usual combos of switchs that are in kmixer etc...
nothing seems to work,
except one thing,
with them all on, i get perfect mic playback
but the pcm is on full volume for record for this to happen
also sound is then distorted on playback
not what i was hoping for

Can anyone offer any help i think the solution is to max out pcm for input
but have it much lower for output of normal sound
I dont know how to achieve this.


Can anyone help or point me in the right direction?
ps, dont tell me google...4 days of googling=bfz
where bfz=big fat zero!

thanks in advance

Mick.  O:)[/QUOTE]
 fixed my sound problem the time honoured way
i threw more money at it :-)
I went out and paid 12euro more and got me a foremedia sound card, now skype mic is fine, i can hear sounds, and as i dont have a fancy computer setup, the stereo output is just fine.
not bad for the extra 12 bucks huh!
my advice...
AVOID LIKE THE PLAGUE CMI CHIPSETS.  
The mic driver is horrendous!

ps. thanks for a great sound howto

---

### Post by YourSurrogateGod on 2005-09-24
I tried what was described above, but no go :( .

I usually use xmms (music) and totem (videos, dvds.) I did the above mentioned changes and now my totem is without sound. Darn...

---

### Post by ekravche on 2005-10-08
It worked nicely for me too. Thank you

---

### Post by zugvogel on 2005-10-10
Many thanks for this howto - it's helped me get talking to people I wouldn't otherwise have been able to call. And it got XMMS working properly too.

---

### Post by aham925925 on 2005-10-12
Hi 

This is in reference to The Tutorial Gandalf posted

I still cannont hear sound :( :( :(

Can Anybody help??

I have no music on my linux system to test on but even if i go into volume monitor it says "Cannot connect to sound daemon.  Please run 'esd' at the command prompt"

Could someone please help i am dieing to listen to music on Linux....I am just a newbie

Bye

aham925925

---

### Post by tseliot on 2005-10-12
[QUOTE=aham925925]Hi 

This is in reference to The Tutorial Gandalf posted

I still cannont hear sound :( :( :(

Can Anybody help??

I have no music on my linux system to test on but even if i go into volume monitor it says "Cannot connect to sound daemon.  Please run 'esd' at the command prompt"

Could someone please help i am dieing to listen to music on Linux....I am just a newbie

Bye

aham925925[/QUOTE]
Breezy is going be released tomorrow. You should try it because it will solve the problems with audio of Hoary (I've tried it myself with a livecd)

---

### Post by aham925925 on 2005-10-12
ohk thanks

Could you please tell me where to download Breezy, how to install it, what it is and if it would solve all of my sound problems?

Thanks :D

---

### Post by tseliot on 2005-10-12
[QUOTE=aham925925]ohk thanks

Could you please tell me where to download Breezy, how to install it, what it is and if it would solve all of my sound problems?

Thanks :D[/QUOTE]
Ubuntu Breezy 5.10 is the next release of Ubuntu. Currently the stable version is Ubuntu Hoary 5.04 but tomorrow the stable version of Breezy is going to be released. You will be able to download it in the same way you did it for Hoary : [http://www.ubuntulinux.org/download]("http://www.ubuntulinux.org/download")

AFAIK the problems with sound have been solved in Breezy (and my previous computer can prove that) but you might want to try a livecd first so as to be sure it really solves your problems.

---

### Post by rgrig on 2005-10-12
After following the steps in this howto in "Multimedia System Selector" I get an error when I test the ALSA input. With ESD input it does not give an error. However, mi mike seems not to work with either setting.

Any help?

---

### Post by ameerirshad on 2005-10-13
[quote=Xian]Thanks so much for posting this. I'd given up and was using polypaudio.
The method you presented worked great![/quote]

I read that polypaudio is the "new" ESD, so why turning back to the "old" ESD?

---

### Post by j813 on 2005-11-25
Am I correct this is to enable multiple users of the sound?
Am using 5.10 and tried the instructions in page 1 but can't download the file.
Is there a new instruction for 5.10?

Thanks;)

---

### Post by tedddee on 2005-11-27
[QUOTE=dukeinlondon]you might find that realplayer still doesn't work after switching to alsa. this is because it is looking for /dev/dsp which is the oss device. Fortunately, alsa includes oss emulation. to enable it, just type 

```
modprobe -v snd-pcm-oss
```

this will create the /dev/dsp device, routed to alsa. 

Realplayer (and other oss only apps, no doubt) then works.

If that works fine, then just add snd-pcm-oss to the file /etc/modules

it will be loaded automatically at boot.[/QUOTE]

how do i reverse modprobe -v snd-pcm-oss ?

i tried this and now quake4 wont start, tried rebooting and its still the same

---

### Post by shreevatsa on 2005-12-05
[QUOTE=Gandalf]
[quote=stoffe]I'm probably not the first to wonder this, but is there any possibility of a good config like this getting into the default installation? And in the meantime, having it as a package that can be installed (via backports perhaps?)
It's a huge annoyance especially as it seems solutions are well known. Especially now when I'm converting people with my new Ubuntu CD:s this is one of the issues that makes even hardened commandline geeks roll their eyes...
Not to be too negative though, I'm happy there are solutions, just wondering if the solutions are generic enough to include from the start, and asking if it is possible.[/quote]
well it's not in default installation because not all audio card support this and this topic proove this[/QUOTE]
Well then, can't we have a package that detects if our audio card supports it or not, before applying these changes? Or a package that when installed, will apply these configurations, and when removed, will restore our old ones?

---

### Post by KlausPaiva on 2006-02-08
Hello!

I've followed this tutorial and, now I can hear sounds from XMMS and GAIM but, not from XMMS and Skype.

I've put XMMS to use ESD and GAIM to use Alsa, everything worked fine.

(I don't know where I specify to Skype to use ESD or Alsa. I've found something that points to /dev/dsp, nothing more)

But, when I use XMMS (both in ESD or ALSA), Skype says that the device is busy... (my GAIM is closed and artsd or esd are not running when I'm doing this test)

Somente knows something to help me?

---

### Post by dmvianna on 2006-03-13
:cool: Works here as well.

---

### Post by dmvianna on 2006-03-13
Originally Posted by **KlausPaiva**:
> (I don't know where I specify to Skype to use ESD or Alsa. I've found something that points to /dev/dsp, nothing more)

But, when I use XMMS (both in ESD or ALSA), Skype says that the device is busy... (my GAIM is closed and artsd or esd are not running when I'm doing this test)
/dev/dsp **is** ALSA's OSS emulation. I've heard that Skype highjacks /dev/dsp in many places before getting to this forum. So, either use one or another each time, or keep googlin'... :confused:

[EDIT] I reckon this is what you wanted? [[http://juljas.net/linux/skype/](http://juljas.net/linux/skype/) skype-dsp-hijacker]
There is also a deb package for Ubuntu, but it's not as up to date as the tar in that page.

---

### Post by Shampyon on 2006-03-17
Heyo. I used to use Xandros because of the Windows networking capability, but after trying out the Live CD for Ubuntu I had to switch. When the time came for me to get a new computer, I decided to dedicate this one to Ubuntu.

Thing is, I didn't check hard enough and didn't realise my Sound Blaster Audigy Value (comes up as "Creative Labs SB Audigy LS" in #lspci) wasn't out-of-the-box compatible. So I tried the tutorial in this thread:
[http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound)

It worked, sort of. I could hear sounds, but they were crackly, distorted. Lots of white noise when performing simple tasks. So I tried out the advice at the start of this thread. No I have no sound again.

It's got me a little miffed, 'cause I just used Automatix for the first time and got just about every bit of extra software I wanted to use, but I can't hear a darned thing.

---

### Post by .celleken on 2006-03-20
Hi all,

I just installed this Linux: Ubuntu and saw this tut to turn on the music :D
Well it failed here :D I am a complete newbie in this linux world and don't have a clue what to do ^^
I followed those steps and 'alsamixer' shows my Audigy 2. 
When I play a sound my Volume Meter lights up. So he detects it... 
My PC Speakers are unmuted and my config is set on ALSA, Audigy 2

If someone can help me, be my guest. :)

The main reason for testing this Linux is that I'm sick of Windows... (My Enemy Territory won't work on Windows and here on Linux it works great...if I had sound it would be tha bomb :D)

Go open source ^^

Thank you for your time and
greetings from Belgium,
.celleken

---

### Post by kperkins on 2006-03-26
Try muting the external speakers (using alsamixer), and leave PC speakers unmuted.  That worked for me on my laptop.

---

### Post by nismoskys on 2006-03-27
i tried this and it killed my sound.. no sounds at all. i tried restoring the backup.. doesnt work.. if i try playing music in rhythmbox the progress scrolls really fast but still.. no sound.

---

### Post by nismoskys on 2006-03-27
**nvm**, restoring the settings and changing gstreamer back to ESD and OSS , w. reboot worked.

---

### Post by Stormx on 2006-03-30
BTW, it looks like sound recorder doesn't work with these settings. I had to swap em back ;-)

---

### Post by YourSurrogateGod on 2006-05-17
Sweet. Finally, my OS does what I want it to do with sound :KS .

---

### Post by CameronCalver on 2006-05-19
Hey i use breezy and when i play ut2004 for the first time afteri boot the sound works perfetly but if i quit ever sound works exept for ut2004 untill i restart or log out then log back in i did the hotto but it still doesnt work maybe ut2004using esd not alsa?

---

### Post by mdz on 2006-06-15
[QUOTE=nix4me]excellent!  Finally a fix for sound problems!  Developers - Please fix it this way in the next release!
[/QUOTE]

This looks essentially the same as the default configuration since 5.10 (Breezy).  Here's the spec which was implemented:

[https://wiki.ubuntu.com/UbuntuDownUnder/BOFs/AudioInfrastructure](https://wiki.ubuntu.com/UbuntuDownUnder/BOFs/AudioInfrastructure)

The things that this howto does are:

- Installs libesd-alsa0 (this is installed by default)
- Creates an asound.conf which enables dmix (this is enabled by default on hardware where it works, via /usr/share/alsa/cards)
- Creates a new /etc/esound/esd.conf which is equivalent to the default one (the only difference is "-d default" which is the default)
- Changes the gstreamer backend to ALSA (the default backend is automatic, which defaults to ALSA, and it intelligently falls back to others if that doesn't work)

In other words, this howto shouldn't make a difference for anyone, and if it does, the development team would like to hear about it.  So if this fixed things for you, please do the following:

- Boot a 6.06 LTS live CD and check that sound works as expected
- Undo your changes one by one, testing at each step, and see which of the changes actually fixed things
- Look at the output from installing libesd-alsa0 and see if it told you it was already installed
- Send mail to [email]ubuntu-devel@lists.ubuntu.com[/email] with your findings

---

### Post by F0CUS on 2006-06-16
It Worked great and fixed my problems, thanks! :KS

---

### Post by RasKolniKoV on 2006-08-04
Hi,

Lot's of thanx :)

But there is still a problem... I can hear sound in Enemy Territory as long as no other application is playing sound, but as soon as I am listening to music or something I get no sound in ET.

I really love playing while listening to music :-({|=  so... please help :)

Thanx ^^,

---

### Post by Jivicin on 2006-08-04
Nice HOWTO.  This worked perfectly with my Audacity problems.  I did have to switch the input to OSS to get sound recorder to work though.

Thanks!

---

### Post by rogeriovinhal on 2006-08-20
I followed that instructions, and my sound in Dapper is now broken... :( 

I tried to undo that, but no good... When I type 'aplay -l', my sound card is listed, also in dmesg...
But when I try to select it in System->Preferences->Sound, there is no card available to choose...

Any idea where to look for?

EDIT: Nevermind, PCM muted. Now working.

---

### Post by ubuntu_demon on 2006-08-25
**DON'T FOLLOW THIS HOWTO**

This howto was written for Hoary and is therefor deprecated if you are running Breezy or Dapper.

If you already did this howto :
> 
In other words, this howto shouldn't make a difference for anyone, and if it does, the development team would like to hear about it. So if this fixed things for you, please do the following:

- Boot a 6.06 LTS live CD and check that sound works as expected
- Undo your changes one by one, testing at each step, and see which of the changes actually fixed things
- Look at the output from installing libesd-alsa0 and see if it told you it was already installed
- Send mail to [email]ubuntu-devel@lists.ubuntu.com[/email] with your findings


If the default sound setup doesn't work for you :
-**please submit bug reports to malone on launchpad**
-here's a guide for sound problems which is more up to date :
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

For more information please see mdz's post here :
[http://ubuntuforums.org/showpost.php?p=1143531&postcount=108](http://ubuntuforums.org/showpost.php?p=1143531&postcount=108)

mdz = Matt Zimmerman = CTO of canonical

---

### Post by ubuntu_demon on 2006-08-25
I'm inclined to close this thread because I can't believe this many people still run hoary in other words : people are following a deprecated howto.

**DON'T POST IN THIS THREAD UNLESS YOU HAVE A REALLY GOOD REASON**

---

### Post by Bluecircle on 2007-06-11
This guide worked perfectly for me!

Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

Edit: Haha now I see the warnings on the last page saying don't use this guide. Well it worked perfectly for me on Gutsy...

---

### Post by daulex on 2007-10-04
> 
I'm inclined to close this thread because I can't believe this many people still run hoary in other words : people are following a deprecated howto.

DON'T POST IN THIS THREAD UNLESS YOU HAVE A REALLY GOOD REASON


what do you mean deprecated.. ?

---

### Post by DouglasAWh on 2007-10-22
> **Gandalf said:**
> Hello there,
This is just a clean and better organised guide of varunus's HowTo located [here](http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound). So primarily all the credits go to him.

...


Enjoy everyone :D.

I'm using Gutsy and this thread was great for me!  I used xset to turn things off but I couldn't seem to use xset to turn them back on!!

---

### Post by Mr_Ada on 2008-03-23
You must be Gandalf the Great!  Thanks that worked great.  Now if I can get MIDI to work!

chris

---

### Post by willemmulder on 2008-04-29
well, I run 8.04 fresh install, and was not able to play multiple sounds at once. This tutorial fixed my sound issues. 

So it's not as outdated as it seems :)

---

### Post by airlife99 on 2008-04-30
Worked for me with 8.04 on an acer 4920, intel sound card.
lovely!

---

### Post by Stunts on 2008-05-07
Amazing as it may seem it also fixed my problems in 8.04...
Just wanted to say thanks.

---

### Post by cmpunk on 2008-08-07
I followed the instructions on the first page and now my sound doesnt work anymore, how do i change it back to the default settings?

---

### Post by gioy808 on 2008-08-11
First thanks for this Tutorial.

Ive followed all steps correctly but the problem is even there.

So when i open a mp3 file and open an windows application with wine the sound only works on the mp3 or on wine.

In ubuntu desktop i can open more applications with sound then 1.

Can anybody help me?

My Mainboard is an ASUS M2N-SLI with a 	nVIDIA nForce 560 chipset.

[[IMG]http://img3.imagebanana.com/img/gf9sfdw3/thumb/soundproblem1.png[/IMG]](http://img3.imagebanana.com/view/gf9sfdw3/soundproblem1.png)

[[IMG]http://img3.imagebanana.com/img/szqg9r/thumb/soundproblem2.png[/IMG]](http://img3.imagebanana.com/view/szqg9r/soundproblem2.png)

---

### Post by dieknolle on 2008-10-08
Ive been short before giving up when i found this
works nearly perfect
only got some probs wiht pidgin left.

---

### Post by fackamato on 2008-10-08
> **dieknolle said:**
> Ive been short before giving up when i found this
works nearly perfect
only got some probs wiht pidgin left.

Using which Ubuntu version?

---

### Post by dieknolle on 2008-10-13
I have 8.04 x64 installed.
I also have a normal headset plus a sound system via iec958.
I change between them with gstreamer-properties.
[[IMG]http://img220.imageshack.us/img220/6760/bildschirmfotohy9.th.png[/IMG]](http://img220.imageshack.us/my.php?image=bildschirmfotohy9.png)
Because it doesnt work at the same time. Would it be possible hearing the same on both?

Pigin works(forgot changing to alsa)

Ho do i change adobe flash to alsa /or do you recommend any other flash app
I think it uses esd, however when flash is running no other app can play sound

I appreciate every help!
thanks in advance.

---

### Post by A2005J on 2008-10-19
I followed the tutorial correctly I think... What happens is skype plays through my USB headset but anything else: Internet, music, etc plays through my speekers can you tell me how to get it back to the default settings?

---

### Post by fackamato on 2008-10-20
> **A2005J said:**
> I followed the tutorial correctly I think... What happens is skype plays through my USB headset but anything else: Internet, music, etc plays through my speekers can you tell me how to get it back to the default settings?

Do the guide backwards.

---

### Post by Bödvar on 2008-11-08
I still can't get Skype to work. Followed all the steps. I can hear myself blowing into the mic, but my voice doesn't come through, and when I use Skype, my contacts can't hear me, even though I can hear them.

---

### Post by oooh on 2009-01-17
I run Hardy Heron and could never use skype when using youtube, amarok, totem or whatever program producing sound. 

However, I updated to the last headers last week and after restarting the problem **WAS COMPLETELLY SOLVED** ! I dont know why or how.

However, after one more computer restart, the problem **APPEARED AGAIN**, so I still have the problem.

How could these headers make a point (I also did a nvidia drivers update) on this skype problem?

---

### Post by wotwhowhy on 2009-02-16
Hey, thanks for the instructions, all seams to work OK, the sound out in my headphones then cut down to output out of only one earphone, but if I change the device back to pulse in skype options it works OK, with one exception.  If I open the Alsa mixer all the inputs are muted, if I un-mute and increase the volume this works with skype fine. But as soon as I close the asla mixer, all the inputs are muted again!!!  Frustrating.  Any ideas???

---

### Post by RafaelG on 2009-05-25
How I can  Reset my Default Settings if I did everything you say on this Howto, Because all the sound in FireFox don't work with this Howto.

---

### Post by fackamato on 2009-05-25
Don't use this 'howto', it doesn't work on new Ubuntus. Thread should be locked...

---

### Post by RafaelG on 2009-05-25
I already  Used it. What I can do to get back the dafault sound setting of Ubuntu 9.04, by the way I'm new in Ubuntu.

---

### Post by rolandixor on 2009-05-29
try deleting the .asoundrc file you would have created.

---

