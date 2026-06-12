---
title: "HOWTO: M-audio Revolution and upgrade Alsa"
date: 2007-04-03
forum: Outdated Tutorials &amp; Tips
---

### Post by miceagol on 2007-04-03
I got sick and tired of having half working 5.1 sound cards, and bought a M-audio Revolution 5.1 after thorough research. ***I highly recommend the M-audio Revolution 5.1 for Ubuntu.*** There are three main reasons for choosing this card. With this card your *5.1 configuration works*, you get a *high quality* card and you *support a manufacturer* who releases the card's specs to the linux community. **Don't support Creative!** With their attitude towards Linux, they should not get our money. The Revolution 5.1 is a bit more expensive than a Creative eqvivalent, but it's worth the extra money.

This card should more or less work out of the box with an updated system. You should read on if you
[LIST]
[*] Still have Edgy
[*] Want to use the line in port
[*] Want to duplicate the front channel audio stream to the rear channels
[/LIST]

This card doesn't work well with Alsa versions older than 1.0.12. Since Edgy includes version 1.0.11, you should upgrade to the latest version. If you have Feisty installed, you should be ok. It comes with Alsa 1.0.13. The line-in port only works from 1.0.14rc1 or newer, so you should upgrade if you need that feauture.

_[SIZE="4"]Bugs and untested features[/SIZE]_

I should note that after any reboot, the front left channel is muted, but it's a known bug, and will probably be fixed in a future Alsa release. To fix it for the current session, you have to adjust the volume of the front channels in alsamixer, e.g. up and down once. There is one more known bug, which is the headphones output. It does not work. Unfortunately I'm not able to test the digital S/PDIF output. If somebody has information about this, please make a post about it here.

_[SIZE="4"]Installing the latest Alsa drivers[/SIZE]_

I'll show you how to install Alsa properly. First of all you should run
```

sudo /etc/init.d/alsa-utils stop

```
This stops the Alsa machinery. I didn't do this first time I installed the Alsa drivers, and got some [severe problems]("http://www.ubuntuforums.org/showthread.php?t=394124") because of it. [COLOR="Red"]It's important that you do not forget the above command.[/COLOR] Now, download the latest development release of *alsa-driver*, *alsa-lib* and *alsa-utils* from the [Alsa webpage]("http://www.alsa-project.org/"), and do the following with all the tarballs in the order I listed the three tarballs:
```

tar xvf <filename>.tar.bz2
cd <filename>
sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=ice1724 --with-oss=yes
sudo make
sudo make install

```
If you have any other cards (like an onboard card), you can add it to --with-cards seperated by commas. After the installation is finished, do a complete reboot. Then run
```

cat /proc/asound/version

```
to check if you successfully upgraded Alsa.  The first time you reboot after upgrading Alsa or installing a new system, you must increase the volume of all channels in *alsamixer*.

_[SIZE="4"]Duplicating the front channel audio stream to the rear channels[/SIZE]_

Now, you should have a working card. If you try play a DVD with Totem, you will hear 5.1 surround. :) If you want to duplicate the stereo stream in the front channels to the rear channels you should continue reading. 

To make that work you need to edit your *~/.asoundrc*. If it doesn't exist, create it. I went through a lot to find out what to add to the file. I tried to copy different .asoundrc files I found here at the forum and on the web, but no files worked correctly. Most of them did duplicate the speakers, but they also added a chipmunk effect, i.e. sound was playing slightly too fast. Sharon den Adel on speed. ;) Anyway, in addition any sound using the xine engine (e.g. amarok) was also choppy.

I ended up in the #alsa IRC channel at irc.freenode.net, and you have no idea how helpful they're there. I got some personal service, and was given this final working .asoundrc. It's fine-tuned for the M-audio Revolution 5.1 (and 7.1?) :)
```

# 6 channel dmix:
pcm.dmix6 {
     type dmix
        ipc_key 1024
        ipc_key_add_uid false
        ipc_perm 0660
        slave {
                pcm "hw:0,0"
                rate 48000
                channels 6
                period_time 0
                period_size 1024
                buffer_time 0
                buffer_size 5120
        }
     }

# upmixing: 
pcm.ch51dup {
        type route
        slave.pcm dmix6
        slave.channels 6
        ttable.0.0 1
        ttable.1.1 1
        ttable.0.2 1
        ttable.1.3 1
        ttable.0.4 0.5
        ttable.1.4 0.5
        ttable.0.5 0.5
        ttable.1.5 0.5
   }

pcm.duplex {
     type asym
     playback.pcm "ch51dup" # upmix first
     capture.pcm "hw:0"
}

# change default device:
pcm.!default {
     type plug 
     slave.pcm "duplex"
}

# for aoss
pcm.dsp "duplex"

pcm.dsp1 "duplex"

```
For the changes to take effect, run
```

sudo /etc/init.d/alsa-utils restart

```
and reopen any program using the sound card. Now **amarok** will duplicate the channels as default, and **totem** will play DVD movies with 5.1 surround as default. 

What you have to do with some other programs: 
[LIST]
[*] **xmms**: Open the preferences. Go to "output plugin" and click on "configure", and write default as audio device.
[*] **mplayer**: Files with a 2 channel audio stream will automatically be duplicated as default. To play a file with a surround stream (e.g. AC3), use the following command:
```

mplayer -ao alsa:device=plug=dmix6 filename

```
[/LIST]

I haven't figured out how to configure VLC correctly. If you know, post it here, and I'll include it in the HOWTO. The same applies for any other programs.

:KS miceagol :KS

---

### Post by herbster on 2007-04-20
miceagol,

My M-Audio 7.1 came last night in the mail and I installed it, man it sounds great! I used this HowTo and have gotten it working just fine with everything, but my 5.1 is not working right. I also have not edited my .asoundrc file as you instructed as I don't need to duplicate sound to rear speakers, my Logi system has a Matrix Mode button to do that optionally.

So I have installed alsa 1.0.13 successfully, etc. and it's good. But I'm getting this when I do speaker-test

```
bobby@bobby-ubuntu:~$ speaker-test -Dplug:surround51 -c6

speaker-test 1.0.13

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.surround51.card'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_getenv returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM surround51
Playback open error: -2,No such file or directory

bobby@bobby-ubuntu:~$
```

Any help would be appreciated!

---

### Post by miceagol on 2007-04-21
> **herbster said:**
> miceagol,

My M-Audio 7.1 came last night in the mail and I installed it, man it sounds great! I used this HowTo and have gotten it working just fine with everything, but my 5.1 is not working right. I also have not edited my .asoundrc file as you instructed as I don't need to duplicate sound to rear speakers, my Logi system has a Matrix Mode button to do that optionally.

So I have installed alsa 1.0.13 successfully, etc. and it's good. But I'm getting this when I do speaker-test

```
bobby@bobby-ubuntu:~$ speaker-test -Dplug:surround51 -c6

speaker-test 1.0.13

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.surround51.card'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_getenv returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM surround51
Playback open error: -2,No such file or directory

bobby@bobby-ubuntu:~$
```

Any help would be appreciated!

Nice that you decided to buy the card. :)

Hmm, my guess is that you need surround51 defined in asoundrc to do that, hence
```

ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.surround51.card'

```
Have you tried playing a DVD in Totem? I think it worked out of the box for me before I edited the asoundrc-file. You could try editing asoundrc anyway, unless you really don't want it.

I guess these two commands won't work for you either unless you edit asoundrc:
```

speaker-test -Dplug:ch51dup -c6 -twav

```
```

speaker-test -Dplug:dmix6 -c6 -twav

```

This command gives just 2 channel sound with my system too:
```

speaker-test -c6 -twav

```

I'm not really good with this myself. I got all the help I needed in #alsa. :) You could try going there and ask for someone called wishie, that was the guy who helped me. You can tell him I sent you there (I'm called michaeka on IRC).

---

### Post by herbster on 2007-04-21
miceagol,

I was in #alsa yesterday and got this sucker working BRILLIANTLY! Full 5.1, as well as regular upmixing with 2channels  videos and songs, and also couldn't play multiple prog sounds simultaneously, but fixed all of this with wishie (a genius!!)'s help!

Here's my .asoundrc:

```
# <wishie[out]> that is where i force ALSA to use my "default" device, not its own internally defined one.
# <wishie[out]> type "plug" means its going through the "plug" plugin, which does sample rate/format conversion
# <wishie[out]> slave.pcm "duplex"
# <wishie[out]> means to pass the audio stream to the pcm.duplex device..
# <wishie[out]> type asym  <-- makes a 'full duplex' (input/output) device.
# <wishie[out]> so for output (playback) pass the audio on to "ch51dup"
# <wishie[out]> and for input (capture) use hw:0
# <wishie[out]> hw:0 just means your first soundcard.
# <wishie[out]> now to the tricky stuff...
# <wishie[out]> pcm.ch51dup
# <wishie[out]> type route  <-- means we want to route audio to other speakers/channels
# <wishie[out]> the interesting parts here, are the ttable lines
# <wishie[out]> front left/right are channels "0" and "1"
# <wishie[out]> so, we are doing the following
# <wishie[out]> ttable.0.0 1   <-- copying channel 0 to speaker 0 with gain (volume) of 1
# <wishie[out]> ttable.1.1 1   <-- copying channel 1 to speaker 1 with gain (volume) of 1
# <wishie[out]> ttable.0.2 1  <-- copying channel 0 (front left) to speaker 2 (rear left) with volume 1
# <wishie[out]> now, for the center.. we have 2 entries..
# <wishie[out]> ttable.0.4 0.5 
# <wishie[out]> ttable.1.4 0.5
# <wishie[out]> first one says copy front left to the center speaker
# <wishie[out]> second one says copy the front right to the center speaker
# <wishie[out]> therefore, you are actually getting front left AND right signals from the center speaker
# <wishie[out]> same for the LFE (sub channel) which is speaker 5
# <wishie[out]> now, for the center and sub, you see i have the volume (gain) at 0.5
# <wishie[out]> since i found that using "1" was too over powering
# <wishie[out]> moving on..
# <wishie[out]> you will see it has slave.channels 6
# <wishie[out]> since we "upmixed" the 2 channel mp3 to 6 channels.
# <wishie[out]> and the "slave.pcm dmix6" tells alsa to pass the audio onto the device pcm.dmix6
# <wishie[out]> now, dmix6 basically takes 6 channels input, and passes it to its slave (which is hw:0,0)
# <wishie[out]> but, multiple programs can access dmix6 at the one time.
# <wishie[out]> where as only 1 program can access hw:0,0 at any time.
# <wishie[out]> so ALSA takes all the input via dmix6, mixes the streams together, THEN sends them to hw:0,0 (which is your soundcard)
# <wishie[out]> so, as far as your sound card is concerned, it is only getting accessed once.
# <wishie[out]> ALSA it taking care of the multiple sound streams, and making them all into one.



# 6 channel dmix:
pcm.dmix6 {
     type dmix
        ipc_key 1024
        ipc_key_add_uid false
        ipc_perm 0660
        slave {
                pcm "hw:0,0"
                rate 48000
                format "S32_LE"
		channels 6
                period_time 0
                period_size 1024
                buffer_time 0
                buffer_size 8192
        }
     }

# upmixing: 
pcm.ch51dup {
        type route
        slave.pcm dmix6
        slave.channels 6
        ttable.0.0 1
        ttable.1.1 1
        ttable.0.2 0.6
        ttable.1.3 0.6
        ttable.0.4 0.5
        ttable.1.4 0.5
        ttable.0.5 0.5
        ttable.1.5 0.5
   }

pcm.duplex {
     type asym
     playback.pcm "ch51dup" # upmix first
     capture.pcm "hw:0"
}

# change default device:
pcm.!default {
     type plug 
     slave {
	pcm "duplex"
	}
}

# for aoss
pcm.dsp "duplex"

pcm.dsp1 "duplex"
```

That gives me full 5.1 from a song in amarok or a regular video in vlc, etc.

AND, I got VLC working too! I popped in a DVD, started playing and all I need to do is click Audio > Audio Device > 5.1, and bam! Perfect, genuine 5.1 with movies, and 5.1 also plays at the same time as other programs too, so this is just a complete solution at last.

**The M-Audio card is EXTREMELY recommended to anyone who wants a full, high-quality sound experience in linux!!!!**

And thanks again for your help, miceagol! Now I really have no need to ever boot into windows ;)

P.S. Also attached my /usr/share/alsa/alsa.conf for anyone who gets this card. Get it! :D

---

### Post by miceagol on 2007-04-21
I'm so happy it worked out for you. :D And yes, this card satifies both quality and Linux demands. It's not hard to get it working, and when it works, it works *really* well. I'm thinking about sending a mail to both M-audio and Creative, and send them a link to this thread. That'll show M-audio that their business model is working, and Creative that their business model is *not* working.

It seems like wishie has made some revisions to .asoundrc since last time, so I'll test it and see how it works compared to the old one. :)

---

### Post by whiskybar on 2007-04-23
I have bought this card lately too. The sound is clear but it seems I'm missing microphone and line-in input controls in alsamixer (and other mixers, too). Do you guys have the controls as this guy:

[http://seehuhn.de/comp/hardware/revolution](http://seehuhn.de/comp/hardware/revolution)

? I'm missing Line Loopback, Mic Loopback, CD Loopback, Loopback, and Capture Channel.

I used to use my onboard soundcard (that came with the nVidia Neo2 Platinum mobo) but disabled it in the BIOS. Then, I put it M-Audio and rebooted. Do I have to remove some of the modules that the previous sound card used?

I'm using Feisty Fawn with their ALSA 1.0.13.

Thank you!

---

### Post by gorezz on 2007-04-24
HI guys, I have extremely new to Ubuntu - this is my first day =)
I followed your tutorial and finally sound works on my m-audio revo 5.1
but the issue i am having is when i click on the music icon and click volume control
i can see all the channels but they are not correct. LFE runs my Right channel and the center runs the left and the right and left run the center.
How do i fix this? i am at a loss and not very good at manipulating this =)
thanks a lot
Grant

---

### Post by miceagol on 2007-04-24
> **whiskybar said:**
> I have bought this card lately too. The sound is clear but it seems I'm missing microphone and line-in input controls in alsamixer (and other mixers, too). Do you guys have the controls as this guy:

[http://seehuhn.de/comp/hardware/revolution](http://seehuhn.de/comp/hardware/revolution)

? I'm missing Line Loopback, Mic Loopback, CD Loopback, Loopback, and Capture Channel.

I used to use my onboard soundcard (that came with the nVidia Neo2 Platinum mobo) but disabled it in the BIOS. Then, I put it M-Audio and rebooted. Do I have to remove some of the modules that the previous sound card used?

I'm using Feisty Fawn with their ALSA 1.0.13.

Thank you!

I quote from the HOWTO above:
> The line-in port only works from 1.0.14rc1 or newer, so you should upgrade if you need that feauture.
I.e. you must install the latest development release of Alsa. You'll find instructions on how to do this in the HOWTO.

---

### Post by miceagol on 2007-04-24
> **gorezz said:**
> HI guys, I have extremely new to Ubuntu - this is my first day =)
I followed your tutorial and finally sound works on my m-audio revo 5.1
but the issue i am having is when i click on the music icon and click volume control
i can see all the channels but they are not correct. LFE runs my Right channel and the center runs the left and the right and left run the center.
How do i fix this? i am at a loss and not very good at manipulating this =)
thanks a lot
Grant

What version of Alsa do you have? Check with:
```
cat /proc/asound/version
```
I've got 1.0.14rc3, and my controls are correct (I have 4.1 though, so can't test Center and LFE). Is the same problem present in alsamixer? Open a terminal, and enter alsamixer on the command line to start it. If upgrading to the latest Alsa doesn't work, you might want to report it as a [bug ]("https://bugtrack.alsa-project.org/alsa-bug/login_page.php").

Anyway, this shouldn't be harder than remembering which control controls which speaker, or am I wrong?

---

### Post by whiskybar on 2007-04-24
Thank you for responding. I think my version is fine though:

cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).

I will try to upgrade to the most recent version then (rc3). Maybe the problem is the previous card and its modules. I really don't know. Maybe I have other modules hanging around; anyway, I'm getting a new hard drive in a couple of days and will do a fresh install of ubuntu (after 2.5 years!).

It seems as if all the input controls were disabled; I got the following in alsamixer:

PCM   PCM Cent  PCM LFE  PCM Rear   IEC958  IEC958 O IEC958 1  Deemphas   H/W      H/W 1    H/W 2    H/W 3     H/W 4    H/W 5    Multi Tr Multi Tr  Multi Tr Multi Tr  Multi Tr   Multi Tr

Can you see some controls between "PCM Rear" and "IEC958" in alsamixer? And do you use 64bit or 32bit drivers? My system is 64bit.

Jiri

---

### Post by miceagol on 2007-04-28
> **whiskybar said:**
> Thank you for responding. I think my version is fine though:

cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).

I will try to upgrade to the most recent version then (rc3). Maybe the problem is the previous card and its modules. I really don't know. Maybe I have other modules hanging around; anyway, I'm getting a new hard drive in a couple of days and will do a fresh install of ubuntu (after 2.5 years!).


It might probably be that you need the latest drivers. The drivers are working fine, even though they're a development release. :)

> **whiskybar said:**
> 
It seems as if all the input controls were disabled; I got the following in alsamixer:

PCM   PCM Cent  PCM LFE  PCM Rear   IEC958  IEC958 O IEC958 1  Deemphas   H/W      H/W 1    H/W 2    H/W 3     H/W 4    H/W 5    Multi Tr Multi Tr  Multi Tr Multi Tr  Multi Tr   Multi Tr

Can you see some controls between "PCM Rear" and "IEC958" in alsamixer? And do you use 64bit or 32bit drivers? My system is 64bit.


I've got "Line Loopback", "CD Loopback" and "Mic Loopback" inbetween "PCM Rear" and "IEC958". Furthermore i also have "Capture" and "Loopback". I'm using the 32 bit version.

---

### Post by kv11 on 2007-05-03
I've recently bought this card. I've quite impressed by the sound quality, and it works almost without troubles in the feisty. The only thing which is bad for me is that I can't easily mute the sound. PCM channel simply has no mute controll in alsamixer.

Is this only my fault or someone else has similar problems ?

---

### Post by miceagol on 2007-05-07
> **kv11 said:**
> I've recently bought this card. I've quite impressed by the sound quality, and it works almost without troubles in the feisty. The only thing which is bad for me is that I can't easily mute the sound. PCM channel simply has no mute controll in alsamixer.

Is this only my fault or someone else has similar problems ?

You're right, I hadn't noticed that before. There's no reaction when I push m in alsamixer. I always use my master volume control physically connected to my speakers to mute the sound.

Does anybody know another way to mute the sound? If not, I'll include this as a bug in the HowTo...

---

### Post by whiskybar on 2007-05-09
Finally I got the input settings in the mixer. I had to compile the new driver from the development version of alsa-driver. Reinstalling and upgrading to feisty did not help because the driver is too old there (Jan 2007). I even got the i386 live CD but to no avail. I hope it will work out of the box with gutsy!

I wanted to package the development versions of the libraries but one needs to build and install the kernel module from alsa-driver - this is actually part of the big kernel package so I would have to create some diversions or something but I don't know how so I just installed it the way miceagol suggest in the first post.

Anyway, now I got the 5.1 and microphone working. This card is just brilliant. Absolutely no backround noise and clear sound. The microphone input is noiseless too. Good value for the money.

---

### Post by badbob100 on 2007-05-13
Something not right here..

edit figured out need to point to \tmp folder, now this isn't going any further

sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=ice1724 --with-oss=yes
sudo: ./configure: command not found

---

### Post by whiskybar on 2007-05-15
Does ekiga work for you guys? It doesn't work for me. I get sound in the test at the beginning but with [email]500@ekiga.net[/email] (the echo test), the sound is badly sampled. I can hear but noise in the right rhythm - both for the echo machine and for me.

I have asked this question on the ekiga forum and we have discovered something is wrong with my audio settings. I have even discovered setting "Multi Track Internal Clock" to 8000 makes ekiga work. However, then it does not work for the other applications; it should be 48000 for them.

Someone suggested putting

defaults.pcm.dmix_max_periods -1

to my .asoundrc but it does not help for me. Now, I don't know what this line does nor what "Multi Track Internal Clock" means. Can someone explain this to me?

Thank you,
Jiri

---

### Post by badbob100 on 2007-05-16
Does the digital output work fully? Does it pass PCM, Dolby Digital & DTS streams?
Also if anyone can shed some light on the above error code.

---

### Post by whiskybar on 2007-05-17
after you unpack the source, enter the directory it will create:

```
tar xjvf <filename>.tar.bz2
cd <filename>
./configure ....
....

```

---

### Post by DealerMan on 2007-05-22
Running sudo ./configure for alsa-utils gives the following error at the end:

checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library

I can add it, I just need to know the name of the package (there are a few choices in Synaptic Package Manager).

For what it's worth, the card worked right out of the box, but only on the right side of my headphones with the green out jack.

edit:  After rebooting, my headphones work just fine (haven't tried the headphone jack).  Sounds great, no more static on default sounds, and my music & videos sound like a million!

---

### Post by whiskybar on 2007-05-23
Okay, here is the golden rule: if it does what you want, don't touch it!

You have to compile things yourself (only) if you need something that only the development process provides. It was the input levels for me that did not work in the default version... I can go on giving you hints how to compile it though if you insist :-)

This time you could install the dependencies by

```
sudo apt-get build-dep alsa-utils
```

We just assume the development version needs the same packages as the current ubuntu version.

---

### Post by miceagol on 2007-05-23
> **whiskybar said:**
> after you unpack the source, enter the directory it will create:

```
tar xjvf <filename>.tar.bz2
cd <filename>
./configure ....
....

```

I'll add this detail to the HOWTO. :)

---

### Post by miceagol on 2007-05-23
> **DealerMan said:**
> Running sudo ./configure for alsa-utils gives the following error at the end:

checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library

I can add it, I just need to know the name of the package (there are a few choices in Synaptic Package Manager).

You need this package:
```
sudo apt-get install libncurses5-dev
```

---

### Post by DealerMan on 2007-05-23
Thanks Miceagol.  I did jump the gun though, my movies & music play fine, but sounds for games that I added through Synaptic don't (one compiled game does work).  I won't sweat it, unless the info you provided will fix that minor annoyance.

---

### Post by miceagol on 2007-05-23
> **DealerMan said:**
> Thanks Miceagol.  I did jump the gun though, my movies & music play fine, but sounds for games that I added through Synaptic don't (one compiled game does work).  I won't sweat it, unless the info you provided will fix that minor annoyance.

What games are you speaking of? I haven't tested much, but FlightGear had sound.

---

### Post by DealerMan on 2007-05-23
Emilia Pinball, lbreakout, and Gweled.  I can't remember if Freecell has sounds or not.  I'm running only Gnome if that makes a difference.  Tarball compiled gnuBG works fine.

---

### Post by dbd on 2007-05-26
miceagol: Thanks for the recommendation, I got this sound card to go with my new speakers and I'm VERY impressed :D
I'm running edgy and it all worked out of the box, without me having to do anything! :)
Only problem is I haven't worked out how to enable to digital out yet, but I'm sure I'll find out soon enough

Thanks again, miceagol, finding your posts saved me a lot of grief looking for a good linux sound card.

---

### Post by badbob100 on 2007-05-27
> Only problem is I haven't worked out how to enable to digital out yet, but I'm sure I'll find out soon enough

Then I'll never use Ubuntu for my HTPC, if digital out isn't working!:(

---

### Post by miceagol on 2007-05-28
> **DealerMan said:**
> Emilia Pinball, lbreakout, and Gweled.  I can't remember if Freecell has sounds or not.  I'm running only Gnome if that makes a difference.  Tarball compiled gnuBG works fine.

I tested Pinball and lbreakout on my PC, and sound worked with no hazzle. Gweled has no sound I recon. I guess your problem lies elsewhere than in the drivers, but I can't be sure since you didn't go through the HOWTO which I have. :)

---

### Post by miceagol on 2007-05-28
> **dbd said:**
> miceagol: Thanks for the recommendation, I got this sound card to go with my new speakers and I'm VERY impressed :D
I'm running edgy and it all worked out of the box, without me having to do anything! :)
Only problem is I haven't worked out how to enable to digital out yet, but I'm sure I'll find out soon enough

Thanks again, miceagol, finding your posts saved me a lot of grief looking for a good linux sound card.

Great that I've helped you getting a sound card you like. :)

Might I suggest that you go to #alsa on IRC and talk to a guy named wishie to fix the digital out when you've got some spare time. I haven't got digital speakers, so I can't test it myself. This HOWTO really needs some instructions on how to get the digital out to work.

---

### Post by BuffaloX on 2007-05-29
Strange, I have M-audio revolution 7.1
And all this fixed exactly nothing for me.

After boot I have no sound in left channel.
The sound appear if I notch volume just a little bit.
I got this fixed on an ancient driver, but I can't fix it since Edgy.
I'm using Ubuntu Studio, but the problem has been the same on
Edgy, Feisty and 7.04 Studio.

Some apps have cracking sounds, I test with S.C.O.U.R.G.E
Because it's immediately apparent, and I know it works with Sound-Blaster.
Normal audio and video players work OK.

I also have a Soundblaster Audigy 2 zs, which work perfectly.
But the audio quality of the M-audio is better,
and the windows drivers are light-years ahead of Creative.

I got audio output on 6 channels which is nice,
Currently I use only two speakers, so obviously not very important ATM.

I had really hoped to finally get rid of those bugs.
Everybody mention how well this card work with Linux,
and it's also marked green on the alsa page.
don't any of you have these issues? Is it only the 7.1 card,
or could it be because my card is from an early batch?

Anyways thanx to everybody that has contributed to making this card work better.
I learned much from reading this thread. :popcorn:

---

### Post by miceagol on 2007-05-29
> **BuffaloX said:**
> 
After boot I have no sound in left channel.


This is a known bug as I said in the HOWTO. Check out the [bug list of Alsa]("https://bugtrack.alsa-project.org/alsa-bug/") (bug #321) for updates on a fix for this bug. I'm not annoyed by this bug, as it doesn't take much time to adjust the volume a bit. Might even be possible to do that with a startup script. :)

> **BuffaloX said:**
> 
Some apps have cracking sounds, I test with S.C.O.U.R.G.E
Because it's immediately apparent, and I know it works with Sound-Blaster.
Normal audio and video players work OK.


I haven't got this issue at all. It might be your .asoundrc. I had crackling sound in Amarok (and some other programs) when I used the wrong .asoundrc

> **BuffaloX said:**
> 
I had really hoped to finally get rid of those bugs.
Everybody mention how well this card work with Linux,
and it's also marked green on the alsa page.
don't any of you have these issues? Is it only the 7.1 card,
or could it be because my card is from an early batch?


The only bugs I experience are listed in the HOWTO.

---

### Post by BuffaloX on 2007-05-29
=D> to **miceagol**

> **miceagol said:**
> This is a known bug as I said in the HOWTO. Check out the [bug list of Alsa]("https://bugtrack.alsa-project.org/alsa-bug/") (bug #321) for updates on a fix for this bug. I'm not annoyed by this bug, as it doesn't take much time to adjust the volume a bit. Might even be possible to do that with a startup script. :)

I haven't got this issue at all. It might be your .asoundrc. I had crackling sound in Amarok (and some other programs) when I used the wrong .asoundrc

The only bugs I experience are listed in the HOWTO.

Ups I didn't see the left speaker missing bug was mentioned, probably because I read it first very late last night, and didn't follow the howto until today.
Still weird it was fixable in an old driver, but not the more current drivers. I guess I&#314;l do the scrip thingy. ;)

Pointing me to .asoundrc was a VERY good tip.
I changed the rate to 44100 and voila no noise at all. :D
I tried to change other settings too, but they had no effect.
Then I changed it to 96000, and playback was too fast, and the noise reappeared.
Now I use 176400, and changed in alsamixer too.
Now it's only a question if AC3 is handled OK at this rate. It is not very important, because I don't use this system for movies. But I may test it out of curiosity. :p
Anyways if I need to change the rate, it takes less than a second for alsa to restart.

The headphone bug is not a problem for me, I'm not that selfish, everybody can listen in if they want. ;)

---

### Post by dbd on 2007-05-29
Digital out works! :D

I havn't managed to get it to be default for alsa (been playing around with the .asoundrc, but my guesses just lead to crashes), but I've got it working for amarok and mplayer, so I don't expect there will be any problems.

I googled around and found this howto:
[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)
You can skip the first bit, just go to "Use Your Device",  the device is 0,1
For amarok if you set the engine to alsa then for each of the "ALSA device configuration" options set the device to:
plughw:0,1

Also, I got mplayer to output Dolby Digital straight to my speakers, running it like this from the command line:
mplayer  -ac hwac3 -ao alsa:device=plughw=0.1

If anyone works out how to get digital out as default let me know. (It's probably pretty straightforward, I just havn't tried much yet).

Enjoy :popcorn:

**Edit:** When using Beryl the digital out from amarok is cuts out for a moment every few seconds. So if you have problems with digital out try not using beryl. (FYI I'm using Beryl + XGL + KDE with an ATI card using the proprietary ATI drivers).

---

### Post by dbd on 2007-05-30
**Edit: **Problem gone, don't know what I did to fix it though :)

[INDENT][I]Hmmm, and now it's broken. No idea what I did, it worked last night and then it didn't work this morning. Whenever I try to play sound (digital or not) it refuses to play, sometimes it repeats the first fraction of a second over and over, and sometimes it just refuses to play.
I must have mucked up my alsa settings, how do I reset them all? I tried deleting .asoundrc, but that didn't help.[/I][/INDENT]

---

### Post by monkman on 2007-06-07
what's about the headphone output? 

now i use the front l/r output where i attach my headphones. and i works too. but i think the power levels aren't right or somethink(nothing i hear, i'd rather think there is specific reason for the headphone jack, or ist it only for not switching around when using active speakers and headphones and they are the same?). 

for my ears this card rocks my old sb live 5.1 by far....

does anyone know whether there are demo files which are in 24bit 192khz stereo? would like to check out the quality

thx!

---

### Post by dbd on 2007-06-07
> **monkman said:**
> 
does anyone know whether there are demo files which are in 24bit 192khz stereo? would like to check out the quality
Not sure if this is exactly what you are looking for, but at the end of the Digital out wiki page I linked above there is a link to some DD/DTS tests, here's the link they gave:
[http://www.sr.se/cgi-bin/mall/index.asp?programid=2445](http://www.sr.se/cgi-bin/mall/index.asp?programid=2445)

---

### Post by willl on 2007-06-13
i will be pulling the trigger on ordering one of these 5.1's tonight. i am not going to give creative any of my paycheck in the course of replacing their unsupported x-fi card (got plenty of use out of it under windows, but that's history now that I'm dual booting). Whether i reinstall the x-fi if/when they release drivers, well, we'll cross that bridge when we come to it...

thanks for the rec and the guide. looking forward to getting my hands dirty.

---

### Post by willl on 2007-06-14
I've installed the 5.1 and it's working and sounding great...under Windows.

Now, with repect to Linux, I've upgraded to the latest Alsa drivers, lib, and utils according to the howto earlier in this thread. There was some trouble with the utils. Installing a curses package got me over the first hurdle, and then installing a bunch of gettext thingies enabled me to do the "make" command on utilsl, finally. So:

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14.
Compiled on Jun 14 2007 for kernel 2.6.20-16-generic (SMP).

I think the drivers are working and the volume is turned back up, because I'm getting test beeps through my onboard audio. But when I plug my speakers into the new card, no dice. Ubuntu knows the card is there (it's available in volume control>file>change device, and also in the device dropdown menu under default mixer tracks in Sound Preferences. Is there some black magic I have to do to activate/select the new card to get output?

------------------------------------

Edit:I failed to recognize that alsamixer controls each device independently, and I had turned up the volume for only my onboard card. After installing gnome-alsamixer, I've turned up the volume for the new card but still not test beeps.

------------------------------------

Edit: success!

I added two lines at the end of /etc/modprobe.d/alsa-base specifying my new card as index 1 and the onboard as index 2. The M audio is now working for me. For anyone else interested I found the info i needed here: [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449&")

---

### Post by BuffaloX on 2007-06-20
Just installed the new alsa driver 10.14 release with 10.14a lib.
I still got issues, like I don't have front and master volume control no matter what mixer I try.
I only have 

pcm?? -    First one has no label, is it master or is it front left and right?
lfe      (subwoofer)
center
side
back.

Is it possible to set delays for individual speakers, To finetune speaker setup?
Is it possible to get front speaker and master control to work properly.

The Audigy 2 driver works much better in Linux, Only reason I don't switch back, is because M-audio is superior in Windows XP, and M-audio has much clearer sound.

---

### Post by dbd on 2007-06-20
I'm having trouble finding the volume control for the microphone. It's very quite, and sometimes when speaking into it (well, shouting usually) I get the sound of a very loud pop coming out of my speakers, which is a bit worrying.

---

### Post by pentadrago on 2007-06-22
This HowTo and some more reviews on the net inspired me to buy a Terratec Aureon 5.1 Sky (uses the Envy24HT chip, just as the Revolution) and I'm getting very happy with it (better sound than my old Soundblaster PCI 512).
But suddenly I was missing sound from Doom 3 and Quake 4. After searching through the net and the console output I found out that increasing the buffer_size to 6652 solved the problem. Does this problem occur for the Revolution too? Should the .asoundrc in the HowTo be changed this way? Are there any negative effects to be feared when increasing the buffer size?

---

### Post by BuffaloX on 2007-06-22
Thanx I'll try and increase my buffersize.
Increasing Buffersize is mainly a problem for live music creation, as it increases latency a little.

---

### Post by c_martini on 2007-06-22
Thanks miceagol, great guide! My m-audio revo 5.1 works nearly perfect!

I would like to enable the on board sound chipset again though as I noticed the mic input for the revo has no mic boost feature. I will need this feature for skype, so I would like to have Skype use the onboard sound and have the revo handle all other sound.

You mentioned about adding the additional sound card(s)/on board chipsets by amending the following during the setup:

```
sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=ice1724,CMI8738 --with-oss=yes
```

 In my case, the additional on board chip is the C-Media CMI8738.

My question is how to add this chipset after the install? Must I go back and start from the beginning again?

:confused:

---

### Post by samuraiCat on 2007-06-23
Oh, crap! Please help!
 
I just installed an M-Audio Revolution 5.1 according to these directions on this thread:



> Installing the latest Alsa drivers

I'll show you how to install Alsa properly. First of all you should run
Code:

sudo /etc/init.d/alsa-utils stop

This stops the Alsa machinery. I didn't do this first time I installed the Alsa drivers, and got some severe problems because of it. It's important that you do not forget the above command. Now, download the latest development release of alsa-driver, alsa-lib and alsa-utils from the Alsa webpage, and do the following with all the tarballs in the order I listed the three tarballs:
Code:

tar xvf <filename>.tar.bz2
cd <filename>
sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=ice1724 --with-oss=yes
sudo make
sudo make install

If you have any other cards (like an onboard card), you can add it to --with-cards seperated by commas. After the installation is finished, do a complete reboot. Then run
Code:

cat /proc/asound/version

to check if you successfully upgraded Alsa. The first time you reboot after upgrading Alsa or installing a new system, you must increase the volume of all channels in alsamixer.

But I screwed up! I downloaded the tarballs to my desktop and installed the packages in /home/(my name)/Desktop/ !

Now I get this:

> anthony@anthony-desktop:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory
anthony@anthony-desktop:~$ sudo /etc/init.d/alsa-utils restart
Password:
 * Shutting down ALSA...                                                 [ OK ] 
 * Setting up ALSA...                                                    [ OK ] 
anthony@anthony-desktop:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory
anthony@anthony-desktop:~$ ls /proc/
1     2396  4618  4832  6123  6347         ide         self
10    2397  4639  4875  6124  6533         interrupts  slabinfo
11    2547  4655  4899  6128  7            iomem       stat
135   3     4656  4907  6131  798          ioports     swaps
164   3491  4662  5     6134  8            irq         sys
165   35    4663  5041  6140  9            kallsyms    sysrq-trigger
166   36    4670  5861  6142  acpi         kcore       sysvipc
167   37    4679  5862  6144  buddyinfo    key-users   tty
168   38    4682  5905  6146  bus          kmsg        uptime
2     3873  4696  5925  6152  cmdline      loadavg     version
2007  4     4709  5960  6156  cpuinfo      locks       version_signature
2008  4181  4724  5974  6158  crypto       meminfo     vmcore
2061  4182  4742  6     6159  devices      misc        vmstat
2062  4184  4743  6067  6160  diskstats    modules     zoneinfo
2063  4186  4759  6105  6180  dma          mounts
2106  4188  4772  6108  6183  driver       mtrr
2185  4189  4773  6109  6313  execdomains  net
2186  4447  4821  6111  6338  fb           opensound
2187  4558  4822  6114  6344  filesystems  partitions
2341  4616  4824  6116  6346  fs           scsi
anthony@anthony-desktop:~$ cat /proc/asound/
cat: /proc/asound/: No such file or directory
anthony@anthony-desktop:~$ cat /proc/
cat: /proc/: Is a directory
anthony@anthony-desktop:~$ 


Now all those folders are installed on my Desktop!

Can I fix this? What should I have done to install them correctly?

Thanks!

Edited to add: Should I have unpacked in /usr/src?

---

### Post by BuffaloX on 2007-06-23
it's probably just leftovers from make

Sudo nautilus
and then you can delete them.

---

### Post by samuraiCat on 2007-06-23
> **BuffaloX said:**
> it's probably just leftovers from make

Sudo nautilus
and then you can delete them.

Thanks, but no, there are a ton of files in each of those folders on my desktop. How do I uninstall them?

---

### Post by samuraiCat on 2007-06-23
Okay, I am starting from scratch. Part of the problem is that my Revolution 5.1 has different chipsets! I have a VT1722 and Envy24GT. That probably messed me up.

Second, I don't know which directory these should be in when I unpack them. /home/ maybe?

Thanks for the help!

By the way, here's some info on the card as of May 2007: [http://seehuhn.de/pages/revolution](http://seehuhn.de/pages/revolution)

---

### Post by Eastisle on 2007-06-28
Where did you guys buy your cards? How much did you pay?

---

### Post by samuraiCat on 2007-06-28
> **Eastisle said:**
> Where did you guys buy your cards? How much did you pay?

Just do a Google product search, and you'll find the cheapest price for the card you want at any of several online stores: [http://www.google.com/prdhp?tab=wf](http://www.google.com/prdhp?tab=wf)

---

### Post by hypnoticmorpheus on 2007-07-01
I use the m-audio revolution 7.1. Installed alsa 1.0.14 from source as documented in this thread, but still no mic available (I checked alsamixer and kmix).
Does somebody have a suggestion?
Thanx

---

### Post by samuraiCat on 2007-07-02
> **hypnoticmorpheus said:**
> I use the m-audio revolution 7.1. Installed alsa 1.0.14 from source as documented in this thread, but still no mic available (I checked alsamixer and kmix).
Does somebody have a suggestion?
Thanx


Yeah, and be careful. I have screwed up my kernel and reinstalled twice already, and now I'm going to have to do it again--all because I followed forum howto's that did not work for my system (including this one--sorry!).

---

### Post by fsck222 on 2007-07-05
> **miceagol said:**
> ```

mplayer -ao alsa:device=plug=dmix6 filename

```


Can you give us the output of mplayer please? I used your config but it doesn't work. I am getting "AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)" which is not want... details below:

```
$ mplayer -ao alsa:device=plug=dmix6 hero.mp3 
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing hero.mp3.
Audio file file format detected.
==========================================================================
Forced audio codec: hwac3
Forced audio codec: a52
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  11.1 (11.0) of 200.0 (03:20.0)  1.5% 

MPlayer interrupted by signal 2 in module: play_audio

```

---

### Post by spirilis on 2007-07-07
So I just bought an M-Audio Revolution 5.1, intended to go into my media center PC (Kubuntu 7.04 feisty).  Hooked it all up with the latest ALSA driver/lib/utils.  I am able to get S/PDIF sound output by using the 2nd device (plughw:0,1) rather than 0,0 or 0,2.  This is going into a Sony home theater receiver.

However, it's only 2 channel.  I ran the speaker-test app with -c6 and while I can hear the test sound for the left front, and left right speakers, it is mute for the rest of the channels.  In the current configuration, it is usable for playing MP3s and DVDs so long as I force it to use stereo output and simulate the surround using Dolby ProLogic IIx, but that is undesirable (just doesn't sound good).
All mixer volumes are turned up, although they don't seem to do anything (modifying the PCM master volume doesn't change the gain seen at the receiver before going through its own volume control)

All that said, the sound quality is superb, especially MP3s.  Guess I have the Sony receiver to thank moreso than the card though.

---

### Post by theorganloft on 2007-07-19
> **miceagol said:**
> I got sick and tired of having half working 5.1 sound cards, and bought a M-audio Revolution 5.1 after thorough research. ***I highly recommend the M-audio Revolution 5.1 for Ubuntu.*** There are three main reasons for choosing this card. With this card your *5.1 configuration works*, you get a *high quality* card and you *support a manufacturer* who releases the card's specs to the linux community. **Don't support Creative!** With their attitude towards Linux, they should not get our money. The Revolution 5.1 is a bit more expensive than a Creative eqvivalent, but it's worth the extra money.

This card should more or less work out of the box with an updated system. You should read on if you
[LIST]
[*] Still have Edgy
[*] Want to use the line in port
[*] Want to duplicate the front channel audio stream to the rear channels
[/LIST]

This card doesn't work well with Alsa versions older than 1.0.12. Since Edgy includes version 1.0.11, you should upgrade to the latest version. If you have Feisty installed, you should be ok. It comes with Alsa 1.0.13. The line-in port only works from 1.0.14rc1 or newer, so you should upgrade if you need that feauture.

_[SIZE="4"]Bugs and untested features[/SIZE]_

I should note that after any reboot, the front left channel is muted, but it's a known bug, and will probably be fixed in a future Alsa release. To fix it for the current session, you have to adjust the volume of the front channels in alsamixer, e.g. up and down once. There is one more known bug, which is the headphones output. It does not work. Unfortunately I'm not able to test the digital S/PDIF output. If somebody has information about this, please make a post about it here.

_[SIZE="4"]Installing the latest Alsa drivers[/SIZE]_

I'll show you how to install Alsa properly. First of all you should run
```

sudo /etc/init.d/alsa-utils stop

```
This stops the Alsa machinery. I didn't do this first time I installed the Alsa drivers, and got some [severe problems]("http://www.ubuntuforums.org/showthread.php?t=394124") because of it. [COLOR="Red"]It's important that you do not forget the above command.[/COLOR] Now, download the latest development release of *alsa-driver*, *alsa-lib* and *alsa-utils* from the [Alsa webpage]("http://www.alsa-project.org/"), and do the following with all the tarballs in the order I listed the three tarballs:
```

tar xvf <filename>.tar.bz2
cd <filename>
sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=ice1724 --with-oss=yes
sudo make
sudo make install

```
If you have any other cards (like an onboard card), you can add it to --with-cards seperated by commas. After the installation is finished, do a complete reboot. Then run
```

cat /proc/asound/version

```
to check if you successfully upgraded Alsa.  The first time you reboot after upgrading Alsa or installing a new system, you must increase the volume of all channels in *alsamixer*.

_[SIZE="4"]Duplicating the front channel audio stream to the rear channels[/SIZE]_

Now, you should have a working card. If you try play a DVD with Totem, you will hear 5.1 surround. :) If you want to duplicate the stereo stream in the front channels to the rear channels you should continue reading. 

To make that work you need to edit your *~/.asoundrc*. If it doesn't exist, create it. I went through a lot to find out what to add to the file. I tried to copy different .asoundrc files I found here at the forum and on the web, but no files worked correctly. Most of them did duplicate the speakers, but they also added a chipmunk effect, i.e. sound was playing slightly too fast. Sharon den Adel on speed. ;) Anyway, in addition any sound using the xine engine (e.g. amarok) was also choppy.

I ended up in the #alsa IRC channel at irc.freenode.net, and you have no idea how helpful they're there. I got some personal service, and was given this final working .asoundrc. It's fine-tuned for the M-audio Revolution 5.1 (and 7.1?) :)
```

# 6 channel dmix:
pcm.dmix6 {
     type dmix
        ipc_key 1024
        ipc_key_add_uid false
        ipc_perm 0660
        slave {
                pcm "hw:0,0"
                rate 48000
                channels 6
                period_time 0
                period_size 1024
                buffer_time 0
                buffer_size 5120
        }
     }

# upmixing: 
pcm.ch51dup {
        type route
        slave.pcm dmix6
        slave.channels 6
        ttable.0.0 1
        ttable.1.1 1
        ttable.0.2 1
        ttable.1.3 1
        ttable.0.4 0.5
        ttable.1.4 0.5
        ttable.0.5 0.5
        ttable.1.5 0.5
   }

pcm.duplex {
     type asym
     playback.pcm "ch51dup" # upmix first
     capture.pcm "hw:0"
}

# change default device:
pcm.!default {
     type plug 
     slave.pcm "duplex"
}

# for aoss
pcm.dsp "duplex"

pcm.dsp1 "duplex"

```
For the changes to take effect, run
```

sudo /etc/init.d/alsa-utils restart

```
and reopen any program using the sound card. Now **amarok** will duplicate the channels as default, and **totem** will play DVD movies with 5.1 surround as default. 

What you have to do with some other programs: 
[LIST]
[*] **xmms**: Open the preferences. Go to "output plugin" and click on "configure", and write default as audio device.
[*] **mplayer**: Files with a 2 channel audio stream will automatically be duplicated as default. To play a file with a surround stream (e.g. AC3), use the following command:
```

mplayer -ao alsa:device=plug=dmix6 filename

```
[/LIST]

I haven't figured out how to configure VLC correctly. If you know, post it here, and I'll include it in the HOWTO. The same applies for any other programs.

:KS miceagol :KS

Thank you for this great information.
My question is about your hardware. I intend to buy a M-audio Revolution 5.1 or 7.1.  I use my system for audio recording.  I was using and believing in the CL cards but I see that CL is really not interested in Linux systems so it is a major relief for me to find these sound cards. 

I have an ECHO MIA MIDI that is not recognized from the BIOS when the machine boots Ubuntu Studio.  It works with other Linux Distros but not with Ubuntu Studio.  

My main question is: What MOBO, Processor and Chipset are you basing your systems on? 

Do you know why it does not see my card during boot? I tried runnning the Alsa upgrades to no avail but now I see that I may not have stopped the engine before upgrading.  However, should the Ubuntu Studio install detect the Echo MIA PCI card even if it rejects it?:guitar:

---

### Post by Sockerdrickan on 2007-07-31
I can't get 5.1 with my Rev 7.1!!

---

### Post by fsck222 on 2007-07-31
can you get 7.1?

---

### Post by Sockerdrickan on 2007-07-31
No, I don't know what's wrong...

---

### Post by fsck222 on 2007-08-01
Can you get 2.0?

How are your speakers connected? I mean, are you using the TOSLINK to your amplifier or do you have your 5.1 speakers connected directly in the card?

---

### Post by whiskybar on 2007-08-01
I'm sorry it may or may not be relevant to the last couple of messages... which are your multi-channel outputs? I mean, how are your outputs ordered? I have 5.1 and they are

Front L+R  -  Rear L+R  -  Center+LFE

(when I look from above). I rebooted to Windows to play some games and I found out the two right jacks should be swapped! Actually, I looked closer at the icons on the back of the sound card to read

Front L+R  -  Center+LFE - Rear L+R

Now I don't understand it. Linux has it the first way (see also [http://seehuhn.de/pages/revolution](http://seehuhn.de/pages/revolution)) and Windows and the back of the card are the second way. Are there two models of the sound card?

Tux0r, have you tried all your sound card outputs?

---

### Post by chiisu on 2007-08-02
I added a bug report/feature request on Launchpad to have the M-Audio Revolution cards better supported for surround sound, please add any comments and such.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/124148](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/124148)

---

### Post by CrashintoDMB on 2007-08-02
I have an M-Audio Revolution 5.1 Sound card which is recognized and whatnot by Ubuntu (I'm running studio). However, when i play a song, no sound comes form the speakers. Even if I open up the sound panel and test the speakers, no sound is produced. Is there anything I could be doing wrong or does anyone know a way i could possibly fix this?

Thanks

Edit: By the way, I checked the sound levels and those are turned up, so it's not that.

---

### Post by whiskybar on 2007-08-02
Let's compare our mixer settings then! I'm getting the following settings when I type

```
amixer
```

in the console.

[http://rafb.net/p/NPj0Fk44.html](http://rafb.net/p/NPj0Fk44.html)

HTH!
(amixer is a command-line version of alsamixer)

---

### Post by CrashintoDMB on 2007-08-02
Got it fixed somehow. thanks.

---

### Post by Epeli on 2007-08-27
Hi,

I've got M-Audio Revolution 7.1. Since I don't have 7.1 speakers I'd like duplicate my front channels to rear/center what ever. So I could use 2.1 speakers and headphones without pluging and unpluging them.

Any one done this?

---

### Post by Larppa on 2007-10-17
Hi all! Thanks to this guide I got sound from all the channels with my revolution 7.1. Problem is I got too much sound from my subwoofer:)

I guess what I need is a low pass filter, but I couldn't get it to work. I tried to edit my asound.conf according to this site:

[http://alsa.opensrc.org/index.php/Low-pass_filter_for_subwoofer_channel_(HOWTO](http://alsa.opensrc.org/index.php/Low-pass_filter_for_subwoofer_channel_(HOWTO))

But after that I get no sound from the subwoofer at all. So does someone have a working low pass filter in the subwoofer channel with revo card? If so, could you share your asound.conf?

Thanks for any help:)

---

### Post by atf487 on 2007-10-21
Hi guys, I'm having trouble with my 5.1 card. Sound works fine, but for the life of me I cannot get the line in to work with my guitar pedal. It works in windows, but I've tried lots of different levels, recompiled the drivers to 1.5, and it still doesn't work. The OP says look if here if you are trying to record with the line in but has no info...

Any help would be greatly appreciated.

---

### Post by Sockerdrickan on 2007-11-12
Bump I want this to work now :D As I said I have Revolution 7.1
I am using Alsa 1.0.13

This is from amixer:

  Front Left: 128 [50%]
  Front Right: 128 [50%]
  Rear Left: 76 [30%]
  Rear Right: 76 [30%]
  Front Center: 64 [25%]
  Woofer: 64 [25%]
  Side Left: 0 [0%]
  Side Right: 0 [0%]
  Rear Center: 0 [0%]

Those with 0% can't be changed? Where? :(

---

### Post by fsck222 on 2007-11-12
> **Tux0r said:**
> Bump I want this to work now :D As I said I have Revolution 7.1
I am using Alsa 1.0.13

This is from amixer:

  Front Left: 128 [50%]
  Front Right: 128 [50%]
  Rear Left: 76 [30%]
  Rear Right: 76 [30%]
  Front Center: 64 [25%]
  Woofer: 64 [25%]
  Side Left: 0 [0%]
  Side Right: 0 [0%]
  Rear Center: 0 [0%]

Those with 0% can't be changed? Where? :(

Try 'alsamixergui' or 'alsamixer', It is shown as PCM rear and PCM side for me.

Cheers,

--
fsck222 [http://jajuk.info/](http://jajuk.info/)

---

### Post by Sockerdrickan on 2007-11-12
Hi, so we meet again (how could you reply this fast? :))
These are the ones that are changeable within any mixer
{
Front Left: 128 [50%]
Front Right: 128 [50%]
Rear Left: 76 [30%]
Rear Right: 76 [30%]
Front Center: 64 [25%]
Woofer: 64 [25%]
}

These are the ones I think are the actual speakers I want to change
{
Side Left: 0 [0%]
Side Right: 0 [0%]
Rear Center: 0 [0%]
}

:S Do you have Revolution 7.1?

I have Creative 5.1 speakers. They are connected to the sub woofer thingy.
Out comes 3 cords which I believe are correct inserted into my Revolution 7.1
I just can't get output for rear left right and center! :(

Ok update:
I can only get sound from the green output port. I tried the other two cords with it and they work. How do i enable the other two output ports? :(

Update 2:
I now have alsa 1.0.15 but it doesn't help

---

### Post by fsck222 on 2007-11-12
I have a 7.1 
What is you music file source? If you are trying with a stereo mp3, it is correct that you can only hear it on two speakers. To test your 5.1 or 7.1 you need an 5.1/7.1 ac3 file, and to play it mplayer/vlc are your friend . You can configure your speaker spacial configuration using a /etc/asound.conf and ~.asoundrc (see [http://alsa.opensrc.org/index.php/Ice1724](http://alsa.opensrc.org/index.php/Ice1724) ) . Also jack is your friend to have different sources on different spakers.
Good luck...

--
fsck222 [http://jajuk.info/](http://jajuk.info/)

---

### Post by Brebs on 2007-11-23
Proper 5.1 surround sound works with the M-Audio Revolution 5.1, with [this ~/.asoundrc](http://forums.gentoo.org/viewtopic-p-4534793.html#4534793).

It *might* help with other soundcards too. But, note that every soundcard is different.

---

### Post by kraymore on 2007-11-24
i have an m-audio revolution 5.1 soundcard and am running gutsy.  i compiled the alsa util alsa lib and alsa driver to the latest 1.0.15 according to the post in this thread.  i still find that my left speaker is often muted.  i have to spike up the volume in gnome audio control to get it to use both speakers.  ideally i would not have to do that to get sound in both channels working.  have 2.1 speaker system.  would appreciate some help.

---

### Post by Epeli on 2007-11-25
> **kraymore said:**
> i have an m-audio revolution 5.1 soundcard and am running gutsy.  i compiled the alsa util alsa lib and alsa driver to the latest 1.0.15 according to the post in this thread.  i still find that my left speaker is often muted.  i have to spike up the volume in gnome audio control to get it to use both speakers.  ideally i would not have to do that to get sound in both channels working.  have 2.1 speaker system.  would appreciate some help.

I had the same problem. Just run these commands on login.
```

amixer -q sset PCM 3+
amixer -q sset PCM 3-
```


For example in KDE create a file in ~/.kde/Autorun and put the commands to it. In Gnome you may use the session manager.

---

### Post by whiskybar on 2007-11-25
Well, I reset other four values because alsa won't remember them:

```
amixer set 'Multi Track Internal Clock',0 48000
amixer set 'PCM',0 87%
amixer set 'PCM Center',0 87%
amixer set 'H/W',3 'PCM Out'
amixer set 'Deemphasis',0 Off
```

I took me a while until I found what was wrong with (respectively):

[LIST]
[*]everything in slow, bass motion
[*]the left front channel quiet
[*]the front center somewhat quiet
[*]the rear left channel muted
[*]music just rusty for such a good card - turn the deemphasis off!
[/LIST]
HTH,  Jiri

---

### Post by spleffy on 2007-12-09
Hello everyone,

Can anybody help me configure my M-Audio Revolution 5.1? I already got it to work using the Ubunto Howto [http://ubuntuforums.org/showthread.php?t=400268](http://ubuntuforums.org/showthread.php?t=400268) . I can get SPDIF to work if I force Amarok to output Plughw:0,1 , but the music gets caught in a loop. It repeats the first 3 seconds!

Moreover I did not find any info on the web to get the headphone plug to work. I am using a 5.1 analog system and a digital link to my stereo. Since it is not possible with the revolution card to play digital and analog at the same time, I like to use the headphone output to link it to my stereo.

I am using the following alsa.conf ([http://ubuntuforums.org/attachment.php?](http://ubuntuforums.org/attachment.php?) ... 1177175900) and this .asoundrc:

# 6 channel dmix:
pcm.dmix6 {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 0660
slave {
pcm "hw:0,0"
rate 48000
channels 6
period_time 0
period_size 1024
buffer_time 0
buffer_size 5120
}
}

# upmixing:
pcm.ch51dup {
type route
slave.pcm dmix6
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 0.5
ttable.1.4 0.5
ttable.0.5 0.5
ttable.1.5 0.5
}

pcm.duplex {
type asym
playback.pcm "ch51dup" # upmix first
capture.pcm "hw:0"
}

# change default device:
pcm.!default {
type plug
slave.pcm "duplex"
}

# for aoss
pcm.dsp "duplex"

pcm.dsp1 "duplex"

How can I force the use of SPDIF in .asoundrc? Any help would be greatly appreciated.

Thx
Spleffy

---

### Post by jagular on 2008-02-04
Any body know how to get work (*censored*) mic on revo 7.1 pls??

---

### Post by element_G on 2008-02-05
Ok, first off I'd like to thank those of you that recommended the Revolution 5.1, everything is sounding nice so far, except Dolby 5.1 through S/PDIF Pass Through doesn't seem to be working (ie: no sound). I am using a 5.1 home theatre as my speaker set-up so to get surround I need S/PDIF Pass Through.

I have tried various .asoundrc 's including the one posted in this HOW-TO and this one [here]("http://forums.gentoo.org/viewtopic-p-4534793.html#4534793"). 
both of them cause Kaffeine and Amarok to complain telling me that xine cannot initialize alsa (I'm a KDE user) also, I am pointing both apps to the alsa device "default"

vlc reports this:
```
[00000357] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[00000323] alsa audio output error: write failed (Broken pipe)

```when trying to play A/52 over S/PDIF (i.e. S/PDIF passthrough)

when mplayer is run with:
```
mplayer -ac hwac3 -ao alsa:device=default VTS_01_2.VOB
```I get
```
Forced audio codec: hwac3
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to AC3, 448000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
==========================================================================
[AO_ALSA] alsa-lib: conf.c:3949: (snd_config_expand) Unknown parameters AES0=6
[AO_ALSA] alsa-lib: pcm.c:2145: (snd_pcm_open_noupdate) Unknown PCM default:AES0=6
AO: [alsa] 48000Hz 2ch ac3 (1 bytes per sample)
```here's my .asoundrc 

```
pcm.!default {
   type plug
   slave.pcm "dmixer"
}

pcm.dmixer  {
   type dmix
   ipc_key 1024
   slave {
      pcm "hw:1,1"
      format S32_LE
      period_time 0
      period_size 1024

# increased buffer_size because in my system 1024 cause bad
# audio performance (for totem media player and mplayer)
      buffer_size 8192

      rate 44100
   }
   bindings {
      0 0
      1 1
   }
}

ctl.dmixer {
   type hw
   card 1
   device 1
} 

pcm.!iec958 {
        type plug
        slave.pcm "hw:1,1"
        }


```I use this to send all audio out through the digital out (i.e. ICE958 ),
I have alsamixer setup to do that properly, and I do get sound out of the digital port, but I can't get Dolby 5.1 to be sent over the SPDIF pass through.

I've tried using alsa 1.0.14 , 1.0.15, and 1.0.16rc2 and none fixes the issue. (currently on 1.0.15)

[s]I've tried to use the onboard (hda-intel) SPDIF to do passthrough but that doesn't work either.[/s]
----UPDATE----
managed to get Dolby passthrough using the onboard card by removing my .asoundrc (onboard is then considered default) and letting xine use the default device
"iec958:AES0=0x6,AES1=0x82,AES2=0x0,AES3=0x2". This is OK now that I can get Dolby pass through but I still want The Revo to do it. I did a bit of snooping around in /usr/share/alsa/pcm there's iec958.conf :
```
#
#  Hardware output from iec958
#

pcm.!iec958 {
    @args [ CARD DEV AES0 AES1 AES2 AES3 ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_IEC958_CARD
                ALSA_PCM_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.pcm.iec958.card
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_IEC958_DEVICE
            ]
            default {
                @func refer
                name defaults.pcm.iec958.device
            }
        }
    }
    @args.AES0 {
        type integer
        # consumer, not-copyright, emphasis-none, mode=0
        default 0x04
    }
    @args.AES1 {
        type integer
        # original, PCM coder
        default 0x82
    }
    @args.AES2 {
        type integer
        # source and channel
        default 0x00
    }
    @args.AES3 {
        type integer
        # fs=48000Hz, clock accuracy=1000ppm
        default 0x02
    }
    type empty
    slave.pcm {
        @func refer
        name {
            @func concat
            strings [
                "cards."
                {
                    @func card_driver
                    card $CARD
                }
                ".pcm.iec958." $DEV ":"
                "CARD=" $CARD ","
                "AES0=" $AES0 ","
                "AES1=" $AES1 ","
                "AES2=" $AES2 ","
                "AES3=" $AES3
            ]
        }
    }
    hint {
        show {
            @func refer
            name defaults.namehint.basic
        }
        description "IEC958 (S/PDIF) Digital Audio Output"
        device $DEV
    }
}

```
which has different values for AES, so I figured they should be changed in .xine/config to :
iec958:AES0=0x04,AES1=0x82,AES2=0x00,AES3=0x02

but xine still complains that the device is busy when I use my .asoundrc with
```
pcm.!iec958 {
        type plug
        slave.pcm "hw:1,1"
        }
```
added to it. Even designating the Revo as card 0 and removing .asoundrc I still get the same result (with both forms of the iec958 device in xine)


any help at all is much appreciated :)

---

### Post by zizzdude on 2008-02-12
when configuring the alsa utils package, it said I needed the curses library. where can I get that?

---

### Post by miceagol on 2008-02-13
> **element_G said:**
> Ok, first off I'd like to thank those of you that recommended the Revolution 5.1, everything is sounding nice so far, except Dolby 5.1 through S/PDIF Pass Through doesn't seem to be working (ie: no sound). I am using a 5.1 home theatre as my speaker set-up so to get surround I need S/PDIF Pass Through.


I recently bought a digital 5.1 system myself, and it works great actually. Try the following .asoundrc:
```

pcm.!default {
       type plug
       slave.pcm "iec958:CARD=Revolution51,DEV=0" # taken from aplay -L
       #slave.rate 48000 # optional resampling to 48kHz
}

```

Check that slave.pcm "iec958:CARD=Revolution51,DEV=0" is correct on your system with 
```
aplay -L
```

Now S/PDIF will be default, and you need only run
```

mplayer <movie file>

```
to get digital out.

One irritating thing with the .asoundrc file here, is that you can only play audio from one source at a time, but I haven't had time to look into it yet.

PS: Sorry for my guide being a bit outdated. I promise to update it once this Master degree has been achieved. :)

---

### Post by miceagol on 2008-02-13
> **zizzdude said:**
> when configuring the alsa utils package, it said I needed the curses library. where can I get that?

Try
```

sudo apt-get install libncurses5-dev

```

---

### Post by element_G on 2008-02-15
> **miceagol said:**
> I recently bought a digital 5.1 system myself, and it works great actually. Try the following .asoundrc:
```

pcm.!default {
       type plug
       slave.pcm "iec958:CARD=Revolution51,DEV=0" # taken from aplay -L
       #slave.rate 48000 # optional resampling to 48kHz
}

```Check that slave.pcm "iec958:CARD=Revolution51,DEV=0" is correct on your system with 
```
aplay -L
```Now S/PDIF will be default, and you need only run
```

mplayer <movie file>

```to get digital out.

One irritating thing with the .asoundrc file here, is that you can only play audio from one source at a time, but I haven't had time to look into it yet.

PS: Sorry for my guide being a bit outdated. I promise to update it once this Master degree has been achieved. :)

Thanks for being quick, the code you posted does push everything down my digital out :)

However I don't think I'm getting 5.1 for the following reasons:
1. when I play a DVD with mplayer, voices come out of all speakers instead of just the centre. My Reciever does not tell me it is getting Dolby 5.1.
output from mplayer: 
```
mplayer dvd://
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz (Family: 6, Model: 15, Step
ping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
There are 54 titles on this DVD.
There are 17 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: dts (5.1) language: en aid: 138.
audio stream: 2 format: ac3 (mono) language: en aid: 131.
audio stream: 3 format: ac3 (mono) language: en aid: 132.
number of audio channels on disk: 4.
subtitle ( sid ): 0 language: en
number of subtitles on disk: 1
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
gnome_screensaver_control()=====================================================
=====================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Stream with high frequencies VQ coding
AUDIO: 48000 Hz,** [COLOR=Red]2 ch[/COLOR]**, s16le, 768.0 kbit/50.00% (ratio: 96000->192000)
Selected audio codec: [ffdts] afm: ffmpeg (DTS)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 854x480 Planar YV12
A:   0.6 V:   0.6 A-V:  0.008 ct:  0.015  12/ 10 ??% ??% ??,?% 0 0
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.
A: 147.8 V: 147.8 A-V:  0.002 ct:  0.096 2573/2570  2%  0%  3.7% 0 0

```2.xine gives no sound when the speaker arrangement "Pass-Through" is used. Changing the passthrough device to default gives no sound, but my surround reciever displays "DEC EROR" . I know this isn't a problem with the reciever since I had pass-through working
with the onboard sound. 

xine config:

```
#
# xine config file
#
.version:2

# Entries which are still set to their default values are commented out.
# Remove the '#' at the beginning of the line, if you want to change them.

# palette (foreground-border-background) to use for subtitles and OSD
# { white-black-transparent  white-none-transparent  white-none-translucid  yellow-black-transparent }, default: 0
#ui.osd.text_palette:white-black-transparent

# notify changes to the hardware mixer
# bool, default: 1
#audio.alsa_hw_mixer:1

# Audiodriver to use (default: auto)
# { auto  alsa  oss  pulseaudio  none  file }, default: 0
audio.driver:alsa

# Use software audio mixer
# bool, default: 1
#audio.mixer_software:1

# use A/52 dynamic range compression
# bool, default: 0
#audio.a52.dynamic_range:0

# downmix audio to 2 channel surround stereo
# bool, default: 0
#audio.a52.surround_downmix:0

# A/52 volume
# [0..200], default: 100
#audio.a52.level:100

# device used for mono output
# string, default: default
#audio.device.alsa_default_device:default

# device used for stereo output
# string, default: plug:front:default
audio.device.alsa_front_device:default

# alsa mixer device
# string, default: PCM
#audio.device.alsa_mixer_name:PCM

# sound card can do mmap
# bool, default: 0
#audio.device.alsa_mmap_enable:0

# device used for 5.1-channel output
# string, default: iec958:AES0=0x6,AES1=0x82,AES2=0x0,AES3=0x2
[COLOR=Red]** audio.device.alsa_passthrough_device:default**[/COLOR]

# device used for 4-channel output
# string, default: plug:surround40:0
#audio.device.alsa_surround40_device:plug:surround40:0

# device used for 5.1-channel output
# string, default: plug:surround51:0
#audio.device.alsa_surround51_device:plug:surround51:0

# speaker arrangement
# { Mono 1.0  Stereo 2.0  Headphones 2.0  Stereo 2.1  Surround 3.0  Surround 4.0  Surround 4.1  Surround 5.0  Surround 5.1  Surround 6.0  Surround 6.1  Surround 7.1  Pass Through }, default: 1
[COLOR=Red]** audio.output.speaker_arrangement:Pass Through**[/COLOR]

# offset for digital passthrough
# numeric, default: 0
#audio.synchronization.passthrough_offset:0

# play audio even on slow/fast speeds
# bool, default: 0
#audio.synchronization.slow_fast_audio:0

# method to sync audio and video
# { metronom feedback  resample }, default: 0
#audio.synchronization.av_sync_method:metronom feedback

# always resample to this rate (0 to disable)
# numeric, default: 0
#audio.synchronization.force_rate:0

# enable resampling
# { auto  off  on }, default: 0
#audio.synchronization.resample_mode:auto

# startup audio volume
# [0..100], default: 50
audio.volume.mixer_volume:100

# restore volume level at startup
# bool, default: 0
#audio.volume.remember_volume:0

# Videodriver to use (default: auto)
# { auto  dxr3  aadxr3  xv  XDirectFB  opengl  SyncFB  xshm  xxmc  none  sdl  fb  xvmc }, default: 0
#video.driver:auto

# pitch alignment workaround
# bool, default: 0
#video.device.xv_pitch_alignment:0

# disable exact alpha blending of overlays
# bool, default: 0
#video.output.disable_exact_alphablend:0

# disable all video scaling
# bool, default: 0
#video.output.disable_scaling:0

# horizontal image position in the output window
# [0..100], default: 50
#video.output.horizontal_position:50

# vertical image position in the output window
# [0..100], default: 50
#video.output.vertical_position:50

# deinterlace method (deprecated)
# { none  bob  weave  greedy  onefield  onefield_xv  linearblend }, default: 4
#video.output.xv_deinterlace_method:onefield

# MPEG-4 postprocessing quality
# [0..6], default: 3
#video.processing.ffmpeg_pp_quality:3

# device used for CD audio
# string, default: /dev/cdrom
#media.audio_cd.device:/dev/cdrom

# slow down disc drive to this speed factor
# numeric, default: 4
#media.audio_cd.drive_slowdown:4

# query CDDB
# bool, default: 1
#media.audio_cd.use_cddb:1

# CDDB cache directory
# string, default: /home/gary/.xine/cddbcache
#media.audio_cd.cddb_cachedir:/home/gary/.xine/cddbcache

# CDDB server port
# numeric, default: 8880
#media.audio_cd.cddb_port:8880

# CDDB server name
# string, default: freedb.freedb.org
#media.audio_cd.cddb_server:freedb.freedb.org

# directory for saving streams
# string, default:
#media.capture.save_dir:

# Number of dvb card to use.
# numeric, default: 0
#media.dvb.adapter:0

# Remember last DVB channel watched
# bool, default: 1
#media.dvb.remember_channel:1

# Last DVB channel viewed
# numeric, default: -1
#media.dvb.last_channel:-1

# default language for DVD playback
# string, default: en
#media.dvd.language:en

# region the DVD player claims to be in (1 to 8)
# numeric, default: 1
#media.dvd.region:1

# device used for DVD playback
# string, default: /dev/dvd
#media.dvd.device:/dev/dvd

# read-ahead caching
# bool, default: 1
#media.dvd.readahead:1

# play mode when title/chapter is given
# { entire dvd  one chapter }, default: 0
#media.dvd.play_single_chapter:entire dvd

# unit for seeking
# { seek in program chain  seek in program }, default: 0
#media.dvd.seek_behaviour:seek in program chain

# unit for the skip action
# { skip program  skip part  skip title }, default: 0
#media.dvd.skip_behaviour:skip program

# file browsing start location
# string, default: /home/gary
#media.files.origin_path:/home/gary

# list hidden files
# bool, default: 0
#media.files.show_hidden_files:0

# network bandwidth
# { 14.4 Kbps (Modem)  19.2 Kbps (Modem)  28.8 Kbps (Modem)  33.6 Kbps (Modem)  34.4 Kbps (Modem)  57.6 Kbps (Modem)  115.2 Kbps (ISDN)  262.2 Kbps (Cable/DSL)  393.2 Kbps (Cable/DSL)  524.3 Kbps (Cable/DSL)  1.5 Mbps (T1)  10.5 Mbps (LAN) }, default: 10
#media.network.bandwidth:1.5 Mbps (T1)

# Timeout for network stream reading (in seconds)
# numeric, default: 30
#media.network.timeout:30

# Domains for which to ignore the HTTP proxy
# string, default:
#media.network.http_no_proxy:

# HTTP proxy host
# string, default:
#media.network.http_proxy_host:

# HTTP proxy password
# string, default:
#media.network.http_proxy_password:

# HTTP proxy port
# numeric, default: 80
#media.network.http_proxy_port:80

# HTTP proxy username
# string, default:
#media.network.http_proxy_user:

# MMS protocol
# { auto  TCP  HTTP }, default: 0
#media.network.mms_protocol:auto

# automatically advance VCD track/entry
# bool, default: 1
#media.vcd.autoadvance:1

# VCD default type to use on autoplay
# { MPEG track  entry  segment  playback-control item }, default: 3
#media.vcd.autoplay:playback-control item

# CD-ROM drive used for VCD when none given
# string, default:
#media.vcd.device:

# VCD position slider range
# { auto  track  entry }, default: 0
#media.vcd.length_reporting:auto

# show 'rejected' VCD LIDs
# bool, default: 0
#media.vcd.show_rejected:0

# VCD format string for stream comment field
# string, default: %P - Track %T
#media.vcd.comment_format:%P - Track %T

# VCD debug flag mask
# numeric, default: 0
#media.vcd.debug:0

# VCD format string for display banner
# string, default: %F - %I %N%L%S, disk %c of %C - %v %A
#media.vcd.title_format:%F - %I %N%L%S, disk %c of %C - %v %A

# v4l radio device
# string, default: /dev/v4l/radio0
#media.video4linux.radio_device:/dev/v4l/radio0

# v4l video device
# string, default: /dev/v4l/video0
#media.video4linux.video_device:/dev/v4l/video0

# device used for WinTV-PVR 250/350 (pvr plugin)
# string, default: /dev/video0
#media.wintv_pvr.device:/dev/video0

# path to RealPlayer codecs
# string, default:
#decoder.external.real_codecs_path:

# display closed captions in MPEG-2 streams
# bool, default: 0
#subtitles.closedcaption.enabled:0

# closed captioning font size
# numeric, default: 24
#subtitles.closedcaption.font_size:24

# closed-captioning foreground/background scheme
# { White/Gray/Translucent  White/Black/Solid }, default: 0
#subtitles.closedcaption.scheme:White/Gray/Translucent

# center-adjust closed captions
# bool, default: 1
#subtitles.closedcaption.center:1

# standard closed captioning font
# string, default: cc
#subtitles.closedcaption.font:cc

# italic closed captioning font
# string, default: cci
#subtitles.closedcaption.italic_font:cci

# subtitle size
# { tiny  small  normal  large  very large  huge }, default: 1
#subtitles.separate.subtitle_size:small

# subtitle vertical offset
# numeric, default: 0
#subtitles.separate.vertical_offset:0

# font for subtitles
# string, default: sans
#subtitles.separate.font:sans

# encoding of the subtitles
# string, default: iso-8859-1
#subtitles.separate.src_encoding:iso-8859-1

# use unscaled OSD if possible
# bool, default: 1
#subtitles.separate.use_unscaled_osd:1

# default duration of subtitle display in seconds
# numeric, default: 4
#subtitles.separate.timeout:4

# frames per second to generate
# numeric, default: 14
#effects.goom.fps:14

# goom image height
# numeric, default: 240
#effects.goom.height:240

# goom image width
# numeric, default: 320
#effects.goom.width:320

# colorspace conversion method
# { Fast but not photorealistic  Slow but looks better }, default: 0
#effects.goom.csc_method:Fast but not photorealistic

# number of audio buffers
# numeric, default: 230
#engine.buffers.audio_num_buffers:230

# number of video buffers
# numeric, default: 500
#engine.buffers.video_num_buffers:500

# default number of video frames
# numeric, default: 15
#engine.buffers.video_num_frames:15

# priority for a/52 decoder
# numeric, default: 0
#engine.decoder_priorities.a/52:0

# priority for bitplane decoder
# numeric, default: 0
#engine.decoder_priorities.bitplane:0

# priority for dts decoder
# numeric, default: 0
#engine.decoder_priorities.dts:0

# priority for dvaudio decoder
# numeric, default: 0
#engine.decoder_priorities.dvaudio:0

# priority for dxr3-mpeg2 decoder
# numeric, default: 0
#engine.decoder_priorities.dxr3-mpeg2:0

# priority for dxr3-spudec decoder
# numeric, default: 0
#engine.decoder_priorities.dxr3-spudec:0

# priority for faad decoder
# numeric, default: 0
#engine.decoder_priorities.faad:0

# priority for ffmpeg-wmv8 decoder
# numeric, default: 0
#engine.decoder_priorities.ffmpeg-wmv8:0

# priority for ffmpeg-wmv9 decoder
# numeric, default: 0
#engine.decoder_priorities.ffmpeg-wmv9:0

# priority for ffmpegaudio decoder
# numeric, default: 0
#engine.decoder_priorities.ffmpegaudio:0

# priority for ffmpegvideo decoder
# numeric, default: 0
#engine.decoder_priorities.ffmpegvideo:0

# priority for flacdec decoder
# numeric, default: 0
#engine.decoder_priorities.flacdec:0

# priority for gsm610 decoder
# numeric, default: 0
#engine.decoder_priorities.gsm610:0

# priority for image decoder
# numeric, default: 0
#engine.decoder_priorities.image:0

# priority for mad decoder
# numeric, default: 0
#engine.decoder_priorities.mad:0

# priority for mpc decoder
# numeric, default: 0
#engine.decoder_priorities.mpc:0

# priority for mpeg2 decoder
# numeric, default: 0
#engine.decoder_priorities.mpeg2:0

# priority for nsf decoder
# numeric, default: 0
#engine.decoder_priorities.nsf:0

# priority for pcm decoder
# numeric, default: 0
#engine.decoder_priorities.pcm:0

# priority for realadec decoder
# numeric, default: 0
#engine.decoder_priorities.realadec:0

# priority for realvdec decoder
# numeric, default: 0
#engine.decoder_priorities.realvdec:0

# priority for rgb decoder
# numeric, default: 0
#engine.decoder_priorities.rgb:0

# priority for speex decoder
# numeric, default: 0
#engine.decoder_priorities.speex:0

# priority for spucc decoder
# numeric, default: 0
#engine.decoder_priorities.spucc:0

# priority for spucmml decoder
# numeric, default: 0
#engine.decoder_priorities.spucmml:0

# priority for spudec decoder
# numeric, default: 0
#engine.decoder_priorities.spudec:0

# priority for spudvb decoder
# numeric, default: 0
#engine.decoder_priorities.spudvb:0

# priority for sputext decoder
# numeric, default: 0
#engine.decoder_priorities.sputext:0

# priority for theora decoder
# numeric, default: 0
#engine.decoder_priorities.theora:0

# priority for vorbis decoder
# numeric, default: 0
#engine.decoder_priorities.vorbis:0

# priority for yuv decoder
# numeric, default: 0
#engine.decoder_priorities.yuv:0

# media format detection strategy
# { default  reverse  content  extension }, default: 0
#engine.demux.strategy:default

# memcopy method used by xine
# { probe  libc  kernel  mmx  mmxext  sse }, default: 0
engine.performance.memcpy_method:mmx

# percentage of discarded frames to tolerate
# numeric, default: 10
#engine.performance.warn_discarded_threshold:10

# percentage of skipped frames to tolerate
# numeric, default: 10
#engine.performance.warn_skipped_threshold:10

# allow implicit changes to the configuration (e.g. by MRL)
# bool, default: 0
#misc.implicit_config:0

# Font for OSD Messages
# string, default: sans
#osd.osd_font:sans

# Show OSD Messages
# bool, default: 1
#osd.osd_messages:1

# Size of OSD text
# { tiny  small  medium  large  very large  huge }, default: 1
#osd.osd_size:small

```

again, any help at all is much appreciated :smile:

---

### Post by cooper814 on 2008-03-09
This is the .asoundrc file I've hacked together in order to get SPDIF(coax) output working with a Revolution 5.1 and a digital surround sound speaker setup.  Many thanks to miceagol for doing most of the work. :)

```
# 6 channel dmix:
pcm.dmix6 {
     type dmix
        ipc_key 1024
        ipc_key_add_uid false
        ipc_perm 0660
        slave {
                pcm "!default"
                rate 48000
                channels 6
                period_time 0
                period_size 1024
                buffer_time 0
                buffer_size 8192
        }
    }

pcm.!default {
       type plug
       slave.pcm "iec958:CARD=Revolution51,DEV=0"
       slave.rate 48000
    }

# upmixing: 
pcm.ch51dup {
        type route
        slave.pcm dmix6
        slave.channels 6
        ttable.0.0 1
        ttable.1.1 1
        ttable.0.2 1
        ttable.1.3 1
        ttable.0.4 0.5
        ttable.1.4 0.5
        ttable.0.5 0.5
        ttable.1.5 0.5
   }

```

This configuration works with Amarok, XMMS, VLC and Totem as long as "dmix6" is specified as the plug.  The only slight problem I've noticed is a faint popping from the center channel that surfaces after music is played for long(er) amounts of time.  It might just be the manifestation of low bitrate (<192kbit) mp3 sound quality, though.

In terms of playing audio from more than one source, I think the bottom segment of the original .asoundrc posted by miceagol would work if "!default" wasn't used.  I have no way to test this .asoundrc configuration right now...the typical usage scenario is watching a youtube video while listening to an mp3 but flash support for amd64 is nil.

```

#pcm.duplex {
#     type asym
#     playback.pcm "ch51dup" # upmix first
#     capture.pcm "hw:0"
#}

# change default device:
#pcm.!default {
#     type plug 
#     slave.pcm "duplex"
#}

# for aoss
#pcm.dsp "duplex"

#pcm.dsp1 "duplex"

```

---

### Post by ParadoxPixel on 2008-03-28
I followed all the instructions here and I got SPDIF output, but it's only 2 ch.

My .asoundrc file looks like this:

```

# 6 channel dmix:
pcm.dmix6 {
     type dmix
        ipc_key 1024
        ipc_key_add_uid false
        ipc_perm 0660
        slave {
                pcm "!default"
                rate 48000
                channels 6
                period_time 0
                period_size 1024
                buffer_time 0
                buffer_size 8192
        }
    }

pcm.!default {
       type plug
       slave.pcm "iec958:CARD=Revolution51,DEV=0"
       slave.rate 48000
    }

# upmixing: 
pcm.ch51dup {
        type route
        slave.pcm dmix6
        slave.channels 6
        ttable.0.0 1
        ttable.1.1 1
        ttable.0.2 1
        ttable.1.3 1
        ttable.0.4 0.5
        ttable.1.4 0.5
        ttable.0.5 0.5
        ttable.1.5 0.5
   }

```

I tried to play a movie with DTS and I can see in the receiver that it's not a DTS  signal, same with Dolby Digital.

I'm on Ubuntu 7.10, Using Mplayer.
I also tried using Mplayer with -ac hwac3 for Dolby and hwdts for DTS but it didn't work.

Did anyone got this to work?

[Updated]
So after a lot of time I got it to work.
First go and compile the latest mplayer -> [http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

After that you can play all the video files with true DTS and Dolby and even mp3 ( the , is the fallback) with this command
```

 mplayer -ao alsa:device=plughw=0.1 -afm hwac3,

```

You can use gmplayer if you change the Device in alsa to plughw=0.1.
You will get an error message but it will work (Anyone knows how to remove or to fixe it?)

---

### Post by DShroud on 2008-05-10
So after reading many threads and other peoples solutions to problems similar to mine, I have discovered how to get SPDIF output working on a Maudio Revolution 7.1.

1.)  If you haven't done so already, create /etc/asound.conf, you must do this using sudo to enable Super User priviledges.

2.)  Copy and paste this into the file...

```
pcm.!default {
   type plug
   slave.pcm "dmixer"
}

pcm.dmixer  {
   type dmix
   ipc_key 1024
   slave {
      pcm "hw:0,1"
      format S32_LE
      period_time 0
      period_size 1024
      buffer_size 8192

      rate 48000
   }
   bindings {
      0 0
      1 1
   }
}

ctl.dmixer {
   type hw
   card 0
   device 0
}
pcm.dsp {
    type plug
    slave.pcm "dmixer"     # use our new PCM here
}
ctl.mixer {
    type hw
    card 0
}

```

3.)  I'm using Linux Mint FCE so I'm not sure how to get to the sound card setup in Ubuntu, but once you can find your Mixer Settings enable H/W,1.

That is it, enjoy!

EDIT:  Also, in my experience it is best to keep the PCM in alsamixer set to a dBgain of 0.00.  Usually if you adjust this it can cause popping and other anomalies.

---

### Post by c_martini on 2008-05-19
Has anyone figured out how to get the headphone output working or is this still unsupported in the ALSA driver?

---

### Post by ziojimmy on 2008-05-23
Hi guys, first post here in ubuntuforums, though you've already helped me a lot.
Bought yesterday a M audio revolution 7.1 (which i use on a 5.1 system, got to buy the 7.1 because it was used and on a really good price).
It works, the sound from my cds comes in a very clean way and, above all, from all the speakers. The thing that makes me upset is the irrilevant number of commands, not even a bass / high eq (which i had on my previous cheap soundblaster), but from my mixer i can only change these parameters:
PCM
PCM Center
PCM LFE
PCM Rear 
PCM Side

And after all, chaning one of those doesn't change nothing, except for the first one.

It makes me upset if i thing the quality and the quantity of the tweaking controls one can have using windows with the same card.

Am i missing something or this is all i can get?

---

### Post by Brebs on 2008-05-23
The equalizer [can be set](http://gentoo-wiki.com/HOWTO_Set_up_a_system-wide_equaliser_with_ALSA_and_LADSPA) in ~/.asoundrc, as can the relative volumes (using ttable entries).

---

### Post by ziojimmy on 2008-05-23
I forgot to mention..
The first time i installed the alsa drivers i wasn't using the revolution yet, so i discharged the icexxxx line in the ./configure command.
Now, even if i've recompiled everything with ice,  cat /proc/asound/version
gives me the old configuration. Can it influence something?

Now, regarding the equalizer, thanks buddy, that helped.
More than that, i hoped anyway that i could get something more complex, which i could expect from a 85 euro sound card.. something like deeper sound, 3d ultramegaplus surround, and other esoteric settings.
Picking up the user guide i read that installing it on windows with the drivers you get..
Bass management, 
Distance (this would be really great)
SRS TruSurround XT enabler (W00T)
SRS Dialog Enhancement 

and really a lot more. 

Is wishing something like this on ubuntu dreaming?

Poor linux users ·'(   (we can make cyclopic smiles instead ·D)

---

### Post by Brebs on 2008-05-23
The magic command you're probably missing is "make clean". But it's safer (i.e. prevents other mistakes) to delete the directory you ran ./configure in, and unextract the alsa tarball again.

"Bass management" is just part of the equalizer AFAIK. See above. If it means splitting the bass to just go through the bass speaker, see [my ~/.asoundrc](ftp://ftp.brebs.me.uk/linux/asoundrc) for how it's done.

"Distance" is presumably speaker-specific delays - [LADSPA](http://www.ladspa.org/) is your friend. Look at all [these lovely plugins](http://plugin.org.uk/ladspa-swh/docs/ladspa-swh.html). Search that page for "delay" ;)

SRS TruSurround - [not so good](http://www.avforums.com/forums/showthread.php?t=42719) it seems.

Anyway, see [my ~/.asoundrc](ftp://brebs.me.uk/linux/asoundrc) for lots of links and examples to get you started.

---

### Post by element_G on 2008-07-31
I would just like to say that **Pulse Audio** was the (eventual) solution to my issues with my revo5.1 card. 
My issue? How to use the SPDIF out on the revo as the (mainly)default device without disabling my on board sound which would have sacrificed my front headphone jack. 
 
This thread along with a lot of googling got me half-way there with nearly all sounds going out the SPDIF, but I could only have one program play sound at once. Whether or not that was a problem with my inability to fully understand ALSA I'm not sure, but it all works now with Pulse Audio. 
 
Getting Pulse Audio to work was not easy from a beginners view but after a couple of days I got it working with minimal modification to the default setup (my first couple of tries failed due to a few misleading threads). The only thing that I'm not sure about is AC3 passthrough, but when I play a DVD (with Dolby) PulseAudio shows I have 6 channels. I play with the sliders and my home theatre responds so I do have 6 channels going to my home theatre.
 
With ALSA I had 1 program at a time playing 2ch sound to my home theatre which upmixed with dolby PLII. Now with pulse I can have multiple programs playing sound and tell the sound where to go (front, digital, which card) and I have 6 channels from DVDs. :KS 
 
(sorry for the long post, just needed to show how excited Pulse Audio makes me) There are a lot of guides on Pulse (even on the Pulse Audio wiki) but I can write how I got pulse working if asked.

---

### Post by gorezz on 2008-09-22
sorry posted twice

---

### Post by gorezz on 2008-09-22
Hello!! It has been a while since i have posted 
I decided to try linux again -
still trying to get my REVO 5.1 set up in hardy heron - all i can get now is the left and right - and when the system first installed, when i pressed the volume down button on my keyboard it would turn the volume down - now - no dice..
So for me - i would like to be able to get surround sound out of my m-audio lx4 5.1 system
any ideas?
my version is 
Advanced Linux Sound Architecture Driver Version 1.0.16.
i tried the asource that you guys had, had set up on the first page - but it didnt work - maybe because its too old - i also didnt install those files on the first page because i figured i had newer ones since this thread started in 2007
thank you guys for youre help i would love to be able to fully use this system.
Grant

---

### Post by Jungleboss on 2008-10-10
Have anyone got this card to work well, including ac3 passthrough?

---

### Post by gadabyte on 2009-02-08
just did a fresh install of xubuntu 8.10 amd64, and my revolution 7.1 seems to be working near-flawlessly.

my only issues: 

xfce4-mixer closes instantly upon running (i just use alsamixer).

the volume control applet has no effect on the sound, no matter what settings i use.  (i just removed it, and use alsamixer).

it is ASTOUNDINGLY LOUD.  to have a volume level that is acceptable system-wide, i need to set PCM to 2% or 4% in alsamixer.  not really a problem, but having a range of acceptable volumes available in the mixer would be nice.

overall, however, i am VERY happy.  audio quality is amazing, and my only issues are exceptionally minor, and easy to ignore.

my advice (coming from someone who added the card to an existing system, and tried everything under the sun to get it working properly) - do a fresh install if you're having issues getting this card working (you do have a separate /home partition, right?)  it *just works* that way.


EDIT: i only have headphones right now, so i'm unsure of the surround performance - i imagine that, at most, i'll need to do the .asoundrc edit once i get my speakers.  i'm not interested in the digital out at this point, so i haven't tested it either.

---

### Post by kraymore on 2009-02-08
I found a script elswhere on this forum, I believe there are 64 and 32 bit versions, called "AlsaUpgrade-1.0.x-rev-1.16.sh"  it is truely awesome.  it will download, compile, and install the latest complete alsa system, for example 1.0.19, or the latest development snapshot.  After not being able to get flash to work after switching to OSS, this script, 
has been a champ. its great, it does all the work for you.  its been very reliable for me.  if i'm not mistaken it even has an option to revert to Ubuntu defaults.  

i will attach the 32 bit version, should anyone wish to try it.  

but use the search function of ubuntuforums.org to see the official thread.

---

### Post by gadabyte on 2009-02-08
here's the thread with the script:

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)


since i just got my card working, i'm wary of messing with anything (for now, anyway).  but i will say that before i got my revolution, and was using onboard sound, getting the new alsa via the script was easy and made a very audible difference in sound quality.  good stuff.

---

