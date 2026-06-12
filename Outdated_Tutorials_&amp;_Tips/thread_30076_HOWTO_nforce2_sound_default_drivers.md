---
title: "HOWTO: nforce2 sound default drivers"
date: 2005-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by RastaMahata on 2005-04-27
This used to be posted in the desktop forum. I think it deserved to be posted here for people to search :)

I found a .asoundrc file that allowed me to play several sounds. Here are the steps Followed (I have an **nforce2** chipset)

1. **killall esd**
2. System > preferences > sound > the sound server thing: unchecked
3. **gedit ~/.asoundrc** (or /etc/asound.conf), and paste this:
```
pcm.nforce-hw {
    type hw
    card 0
}

pcm.!default {
    type plug
    slave.pcm "nforce"
}

pcm.nforce {
    type dmix
    ipc_key 1234
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 1024
        buffer_size 4096
        rate 44100
    }
}

ctl.nforce-hw {
    type hw
    card 0
}
```
3. **sudo gedit /etc/libao.conf**, and where it says esd, type alsa:
```
default_driver=alsa
```
4. System > preferences > multimedia: Select ALSA above, OSS below. This way you can record with your mic. ;)
5. After you've changed /etc/asound.conf, use Synaptic to perform a smart pakage install. Install the libesd-alsa0 and all dependecies. (Thanks Ranime)
6. That's it, no need to reboot

test by playing a movie _and_ a song (totem + rhythmbox)...

anyway, gaim sounds seem choppy / bad quality, but totem movies play excellent (no audio delay). I've learnt how to live with it, though. :D (Maybe changing the sounds could work...)

---

### Post by Ranime on 2005-05-14
No prob! 

Just glad I could help!!

 ;-)

---

### Post by Majlo on 2005-05-15
At last my microphone finally works  \\:D/

---

### Post by SAMsan on 2005-05-24
[QUOTE=RastaMahata]This used to be posted in the desktop forum. I think it deserved to be posted here for people to search :)

I found a .asoundrc file that allowed me to play several sounds. Here are the steps Followed (I have an **nforce2** chipset)

1. **killall esd**
2. System > preferences > sound > the sound server thing: unchecked
3. **gedit ~/.asoundrc** (or /etc/asound.conf), and paste this:
```
pcm.nforce-hw {
    type hw
    card 0
}

pcm.!default {
    type plug
    slave.pcm "nforce"
}

pcm.nforce {
    type dmix
    ipc_key 1234
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 1024
        buffer_size 4096
        rate 44100
    }
}

ctl.nforce-hw {
    type hw
    card 0
}
```
3. **sudo gedit /etc/libao.conf**, and where it says esd, type alsa:
```
default_driver=alsa
```
4. System > preferences > multimedia: Select ALSA above, OSS below. This way you can record with your mic. ;)
5. After you've changed /etc/asound.conf, use Synaptic to perform a smart pakage install. Install the libesd-alsa0 and all dependecies. (Thanks Ranime)
6. That's it, no need to reboot

test by playing a movie _and_ a song (totem + rhythmbox)...

anyway, gaim sounds seem choppy / bad quality, but totem movies play excellent (no audio delay). I've learnt how to live with it, though. :D (Maybe changing the sounds could work...)[/QUOTE]
 Wow !! great !!!

+++
Samsan.

---

### Post by logan2004 on 2005-05-25
awesome thanks!!!!

---

### Post by NaitoNeko on 2005-05-26
[QUOTE=RastaMahata]This used to be posted in the desktop forum. I think it deserved to be posted here for people to search :)

I found a .asoundrc file that allowed me to play several sounds. Here are the steps Followed (I have an **nforce2** chipset)

1. **killall esd**
2. System > preferences > sound > the sound server thing: unchecked
3. **gedit ~/.asoundrc** (or /etc/asound.conf), and paste this:
```
pcm.nforce-hw {
    type hw
    card 0
}

pcm.!default {
    type plug
    slave.pcm "nforce"
}

pcm.nforce {
    type dmix
    ipc_key 1234
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 1024
        buffer_size 4096
        rate 44100
    }
}

ctl.nforce-hw {
    type hw
    card 0
}
```
3. **sudo gedit /etc/libao.conf**, and where it says esd, type alsa:
```
default_driver=alsa
```
4. System > preferences > multimedia: Select ALSA above, OSS below. This way you can record with your mic. ;)
5. After you've changed /etc/asound.conf, use Synaptic to perform a smart pakage install. Install the libesd-alsa0 and all dependecies. (Thanks Ranime)
6. That's it, no need to reboot

test by playing a movie _and_ a song (totem + rhythmbox)...

anyway, gaim sounds seem choppy / bad quality, but totem movies play excellent (no audio delay). I've learnt how to live with it, though. :D (Maybe changing the sounds could work...)[/QUOTE]
 Thnx a lot .... there is not a lot of info about this .... it seams nforce2 mobos has lack of specificacions, so you help a lot.

---

### Post by cachorro on 2005-06-13
It works fine for me, but... I've time investigating about make the volume slider (the one that appear when we click on the little loudspeaker, beside the date) and I couldn't get anything!!!  ](*,) 
I downloaded official nVidia linux drivers, I followed the instructions, since Ubuntu is not a "recognized" distribution to nVidia I had to install kernel-headers and recompile, to properly install the driver, but... I can't do it work following the instructions. They refer to a file called  **/etc/modprobe.conf** and another one **/etc/modules.conf** that I obviously cannot find (I used to see in older distributions like Knoppix 3.2). **How can I keep the nVidia instructions to finish the official nVidia driver and make work the "nvmixer", "audio control panel" and my volume slider?**
Someone that make it work?
Thanks in advance!!!

Cachorro. \\:D/ 

FREEDOM=LINUX

---

### Post by RastaMahata on 2005-06-13
are you sure? I have done this guide at least 7 times in different pcs. I have never had that problem. When you right click on it > properties, do you select the Alsa device? (nforce2)

---

### Post by GazaM on 2005-06-14
Will this guide work on an nForce4 motherboard?

---

### Post by RastaMahata on 2005-06-14
[QUOTE=GazaM]Will this guide work on an nForce4 motherboard?[/QUOTE]
 from what I've heard, It should... :/

---

### Post by ::DoGG:: on 2005-06-17
You really made my day man !!!
After 2 days digging in the net and trying anything ( well, somehow i felt that this all sound server stuff is bad...) i tried that and worked great. At last ! no delays on video playback, they should fix it in another release, cause it gives a lot of people the problem when they use esd as the output in the video players, once they change to alsa or oss no delays, but i couldn`t get alsa working, so this howto is great !!!!!!!!

P.S. I`m on amd64 release and nForce3 - so it works in this chipset too.

---

### Post by RastaMahata on 2005-07-13
[QUOTE=::DoGG::]You really made my day man !!!
After 2 days digging in the net and trying anything ( well, somehow i felt that this all sound server stuff is bad...) i tried that and worked great. At last ! no delays on video playback, they should fix it in another release, cause it gives a lot of people the problem when they use esd as the output in the video players, once they change to alsa or oss no delays, but i couldn`t get alsa working, so this howto is great !!!!!!!!

P.S. I`m on amd64 release and nForce3 - so it works in this chipset too.[/QUOTE]
 heh :P no problem

---

### Post by hevtig on 2005-08-21
Thanks alot for your descrition howto make my nforce2 sound work.

But I still have some problems with multiple sounds...

XMMS froze with ESD, now works fine with ALSA, but I still can´t use another program using sound.

I tried XMMS (worked) then started "Teamspeak2". This programms uses OSS as standard and I didn´t get it work on ALSA. Strange is, Teamspeak starts only at the moment XMMS stops.
i.e. I start XMMS and TeamSpeak, but TS only starts, when XMMS quits. Someone got experience in this?

It seems that I´ve have no multiple sound at all. even gaim sound does not appear, when XMMS is started.

got some advice? I´m not a pro in Linux...

thanks a lot

---

### Post by Axklor on 2005-08-21
PLEASE NOTE!

This method of playing multiple sounds (mixing) through the ALSA driver is referred to as "software mixing"

while there is no ALSA driver that supports the nforce2 APU fully, this driver makes good use of the codec and allows you to cleverly play multiple sounds via "software mixing".

The official nvidia driver includes an OSS driver, which includes full hardware mixing and 5.1 with DTS for the nforce2 "SoundStorm" chipset, while OSS is now deprecated as a driver, some will probably find the official nvidia driver a little better, i have noticed better quality through the OSS driver, but as some may say, if its not broke, dont fix it.

I am currently using the ALSA driver, but from my experiences with other distro's and the OSS driver I am going to give it a try, so look out for a howto soon showing you how to get it working.

---

### Post by mega on 2005-08-21
I still cant record, no matter what I do I cant boost the mic volume, I can hear it, but I have to crank the speakers wide open

---

### Post by hevtig on 2005-09-06
[QUOTE=][/QUOTE]
 I have still the problem told above.

ESD doesn´t work
ALSA works, but I cant´t start another programm using the soundcard
OSS works, XMMS and Teamspeak starting, but only XMMS working, muted in teamspeak
nforce drive - install didn´t work ´cause you need kernel sources... sorry, but I´m new to this.

Somebody can help me?
What is the best way to get this thing work?

---

### Post by djnitro on 2005-09-08
[QUOTE=hevtig]I have still the problem told above.

ESD doesn´t work
ALSA works, but I cant´t start another programm using the soundcard
OSS works, XMMS and Teamspeak starting, but only XMMS working, muted in teamspeak
nforce drive - install didn´t work ´cause you need kernel sources... sorry, but I´m new to this.

Somebody can help me?
What is the best way to get this thing work?[/QUOTE]

Same problem here, only I can't install the network drivers for my NForce Motherboard

-/\/-

---

### Post by fragmental on 2005-09-12
[QUOTE=RastaMahata]This used to be posted in the desktop forum. I think it deserved to be posted here for people to search :)

I found a .asoundrc file that allowed me to play several sounds. Here are the steps Followed (I have an **nforce2** chipset)

1. **killall esd**
2. System > preferences > sound > the sound server thing: unchecked
3. **gedit ~/.asoundrc** (or /etc/asound.conf), and paste this:
```
pcm.nforce-hw {
    type hw
    card 0
}

pcm.!default {
    type plug
    slave.pcm "nforce"
}

pcm.nforce {
    type dmix
    ipc_key 1234
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 1024
        buffer_size 4096
        rate 44100
    }
}

ctl.nforce-hw {
    type hw
    card 0
}
```
3. **sudo gedit /etc/libao.conf**, and where it says esd, type alsa:
```
default_driver=alsa
```
4. System > preferences > multimedia: Select ALSA above, OSS below. This way you can record with your mic. ;)
5. After you've changed /etc/asound.conf, use Synaptic to perform a smart pakage install. Install the libesd-alsa0 and all dependecies. (Thanks Ranime)
6. That's it, no need to reboot

test by playing a movie _and_ a song (totem + rhythmbox)...

anyway, gaim sounds seem choppy / bad quality, but totem movies play excellent (no audio delay). I've learnt how to live with it, though. :D (Maybe changing the sounds could work...)[/QUOTE]
 The driver for the nvidia spu is the i8x0 driver, isn't it?  and it uses the "ac97_codec"?  My nforce2 board actually uses a cmi9761a chipset and it uses the i8x0 driver.  In windows, I can use the nvidia sound driver, but it seems like some of the functionality doesn't work right so I use the drivers from c-media.  It's really kind of confusing.  The manual just says "ac'97 codec".

Does anyone know how to get 5.1 sound to work?  I used to use this asroundrc with my soundblaster live.
```

pcm.!default {
    type plug
    #slave.pcm "sound51"
    slave.pcm "dmix"
}

pcm.dmixs51 {
        type dmix
        ipc_key 1024
        slave {
                pcm "hw:0,1"
                rate 48000
                channels 6
                period_time 0
                period_size 1024
                buffer_time 0
                buffer_size 4096
        }
}

pcm.s51 {
   type plug
   slave.pcm "dmixs51"
}

pcm.dsp0 {
   type plug
   slave.pcm "dmixs51"
}

pcm.sound51 {
    type route
    slave.pcm s51
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

It might still work, but I'm nto sure how to combine the multisound configuration for the multiple sounds and the 5.1 configuration.  Too bad there's not a good Alsa tool to set up things like this.

---

### Post by BLTicklemonster on 2005-10-09
Cool. Now to see if teamspeak works with ubuntu, and if I can use yahoo voice conferencing with it.

---

### Post by wammy on 2005-11-10
ok,
i have an msi kt7n2 nforce2 mobo

i followed the instructions from here:
[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

and changed the asound.conf with the info from here but still cant mix things.

for example, teamspeak works but prevents all other apps to use OSS or ALSA so i cant play games on cedega :(

also,
i didnt have any asound.conf files before i tried all this... is this normal? what is it used for anyway and how come it used to work without thise conf files?

futhermore,
some people claim to set the multimedia thing both to alsa, here iread to set it to alsa and oss, what up with that.

these sound troubles remind me of what windows was 10 years ago.
sometimes i really love linux, sometimes i like to throw it out of the windows (pun intended) and i've been playing with it off and on for at least 5 years now.

---

### Post by linuxwhatsthat on 2005-11-11
[QUOTE=wammy]ok,
i have an msi kt7n2 nforce2 mobo

i followed the instructions from here:
[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

and changed the asound.conf with the info from here but still cant mix things.

for example, teamspeak works but prevents all other apps to use OSS or ALSA so i cant play games on cedega :(

also,
i didnt have any asound.conf files before i tried all this... is this normal? what is it used for anyway and how come it used to work without thise conf files?

futhermore,
some people claim to set the multimedia thing both to alsa, here iread to set it to alsa and oss, what up with that.

these sound troubles remind me of what windows was 10 years ago.
sometimes i really love linux, sometimes i like to throw it out of the windows (pun intended) and i've been playing with it off and on for at least 5 years now.[/QUOTE]

I have this same board and cant install the audio driver pakage from nvidia anyone that can help it would be appreciated

---

### Post by cafevincent on 2005-11-27
[QUOTE=RastaMahata]This used to be posted in the desktop forum. I think it deserved to be posted here for people to search :)

I found a .asoundrc file that allowed me to play several sounds. Here are the steps Followed (I have an **nforce2** chipset)

1. **killall esd**
2. System > preferences > sound > the sound server thing: unchecked
3. **gedit ~/.asoundrc** (or /etc/asound.conf), and paste this:
```
pcm.nforce-hw {
    type hw
    card 0
}

pcm.!default {
    type plug
    slave.pcm "nforce"
}

pcm.nforce {
    type dmix
    ipc_key 1234
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 1024
        buffer_size 4096
        rate 44100
    }
}

ctl.nforce-hw {
    type hw
    card 0
}
```
3. **sudo gedit /etc/libao.conf**, and where it says esd, type alsa:
```
default_driver=alsa
```
4. System > preferences > multimedia: Select ALSA above, OSS below. This way you can record with your mic. ;)
5. After you've changed /etc/asound.conf, use Synaptic to perform a smart pakage install. Install the libesd-alsa0 and all dependecies. (Thanks Ranime)
6. That's it, no need to reboot

test by playing a movie _and_ a song (totem + rhythmbox)...

anyway, gaim sounds seem choppy / bad quality, but totem movies play excellent (no audio delay). I've learnt how to live with it, though. :D (Maybe changing the sounds could work...)[/QUOTE]

I installed using these instructions but I get no sound. I'm using Ubuntu 5.10 with updates and ASUS A7N8X-something with nForce2 connected with optical S/PDIF.

---

### Post by Godzig on 2007-04-26
Just for the record this worked for me:
feisty 7.04, nVidia nForce2 AC97 Multimedia Controller

sometimes it's nice to see recent posts to older threads...

---

### Post by havoc3d on 2007-07-01
I've got several problems trying to follow these instructions...I'm running Feisty fully updated...

In the System>Preferences>Sound window, i have no check box talking about any kind of service....only check boxes are under the "Sound" Tab, a check box for "Enable Software sound mixing" (assuming this is the one i need to uncheck?) and in the "System beep" tab for "Enable System Beep"

Next problem....i don't seem to have an a file on my system called asound.conf or asoundrc anywhere....i DID find a command that's just asoundconf, but it didn't seem very helpful...like a utility for editing the config file, but i'm not sure how to use it.

My system has no System>Preferences>Multimedia....i've been seeing and using ubuntu since dapper, and never have seen this menu....(He talking about system>preferences>sound again here?)

If anyone has any ideas why my system is apparently different than the rest of the world please let me know...

---

