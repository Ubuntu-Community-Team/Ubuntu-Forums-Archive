---
title: "How to get pSX to work on Jaunty"
date: 2009-07-29
forum: Outdated Tutorials &amp; Tips
---

### Post by rfrayer on 2009-07-29
Ill make this short and sweet

```

sudo apt-get install libgtkglext1-dev
wget http://psxemulator.gazaxian.com/pSX_linux_1_13.tar.bz2
tar xvjf pSX_linux_1_13.tar.bz2
sudo mv pSX /opt
cd /usr/share/pixmaps
sudo wget http://www.zodttd.com/wiki/images/d/dd/Icon-psx4iphone.png
cd ~
sudo gedit /usr/share/applications/pSX.desktop
```paist this in it

```
[Desktop Entry]
Name=pSX Emulator
GenericName=pSX
Comment=Play playstation games on ubuntu
Type=Application
Exec=pSX
Icon=/usr/share/pixmaps/Icon-psx4iphone.png
Terminal=false
Categories=Game;Emulators;
``````
sudo gedit /usr/bin/pSX
```paist this in it

```
#!/bin/bash

killall pulseaudio 
sleep 1
cd /opt/pSX
./pSX
sleep 1
pulseaudio -D
``````
sudo chmod 755 /usr/bin/pSX
```here comes the great part were gonna tweak pulseadio so that it doesnt keep restarting every dang time we kill it

this is a long code so **sudo su**

```
cp /etc/pulse/client.conf /etc/pulse/client.conf-old && grep -v 'autospawn = yes' /etc/pulse/client.conf > /etc/pulse/client.conf-new && echo 'autospawn = no' >> /etc/pulse/client.conf-new && rm /etc/pulse/client.conf && mv /etc/pulse/client.conf-new /etc/pulse/client.conf
```now add yourself to these groups and ya may need to reboot

pulse, pulse-rt and pulse-access

thats all your good to go as soon as ya find yourself some bios

or you can simply install the pre-build deb i mad

```
wget http://ubuntu.global-web.us/jaunty/binary/pSX-1.13~Jaunty2.deb
sudo dpkg -i pSX-1.13~Jaunty2.deb
```

---

### Post by kidux on 2009-07-31
Thank you. After following this, I only had to use getlibs to get the 32bit libgtkglex1 package (64bit Jaunty). After that, I was able to play Soul Reaver with no problems.

---

### Post by rfrayer on 2009-08-04
not a problem i figured i auta share this solution to a problem that gave me so mych head pounding grief lol

---

### Post by AetherSoup on 2009-09-12
just brought this post up to say thanks to the author

I used the deb package, restarted the computer and it works excellent.

---

### Post by rfrayer on 2009-09-18
not a problem i know i went nuts trying to figure that out honestly to me psx is way better than epsxe especially when it comes to iso/bin compatability

---

### Post by klikevil on 2009-12-18
soooo... i use OSS, and pSX doesn't get past the select language screen.

my terminal output looks like this:
```

seotechd@seotechd-desktop:~$ pSX
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
[src/linux/sound.cpp, line 582]: 'snd_pcm_open(&pcm_handle,dev->info->device_fname,SND_PCM_STREAM_PLAYBACK,0)' returned 'No such file or directory'
pSX: pcm_params.c:2259: snd_pcm_hw_refine: Assertion `pcm && params' failed.
/usr/bin/pSX: line 7:  7237 Aborted                 ./pSX
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
seotechd@seotechd-desktop:~$ 

```

I'm open to any and all suggestions lol.

---

### Post by rfrayer on 2010-01-28
> **klikevil said:**
> soooo... i use OSS, and pSX doesn't get past the select language screen.

my terminal output looks like this:
```

seotechd@seotechd-desktop:~$ pSX
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
[src/linux/sound.cpp, line 582]: 'snd_pcm_open(&pcm_handle,dev->info->device_fname,SND_PCM_STREAM_PLAYBACK,0)' returned 'No such file or directory'
pSX: pcm_params.c:2259: snd_pcm_hw_refine: Assertion `pcm && params' failed.
/usr/bin/pSX: line 7:  7237 Aborted                 ./pSX
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
seotechd@seotechd-desktop:~$ 

```I'm open to any and all suggestions lol.


not sure what to tell ya except pSX is only compatable with alsa

---

