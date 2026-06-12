---
title: "No sound from Computer"
date: 2013-12-07
forum: New to Ubuntu
---

### Post by tirab on 2013-12-07
Hi everyone.

I've run Ubuntu 13.04 and now 13.10 on my desktop computer and both do not produce any sound at all.
I have a dual boot system with windows 8 and on windows 8 there is no problem with the sound.

Any advice would be appreciated.
Thanks
tirab

---

### Post by asus-user on 2013-12-09
> **tirab said:**
> Hi everyone.

I've run Ubuntu 13.04 and now 13.10 on my desktop computer and both do not produce any sound at all.
I have a dual boot system with windows 8 and on windows 8 there is no problem with the sound.

Any advice would be appreciated.
Thanks
tirab

Hello, 

Please provide some information about your computer specifications (sound card, mother board, etc.)

---

### Post by kulen19 on 2013-12-09
Hi. 

I remember I had a problem like this myself, some years ago. I fixed it with installing "padevchooser", which enables you to choose from where you want the sound to be played from(in case you have several sound-cards). You can check it out, as long as it's still available in the repositories(try sudo apt-get install padevchooser from the command-line)

EDIT: A quick Google-search indicates that it's removed from the repo, unfortunately([https://bugs.launchpad.net/ubuntu/+source/padevchooser/+bug/851695](https://bugs.launchpad.net/ubuntu/+source/padevchooser/+bug/851695)). I'm sorry I couldn't be of more help to you.

---

### Post by philinux on 2013-12-09
padevchooser is in my 13.10.
```
apt-cache policy padevchooser
padevchooser:
  Installed: (none)
  Candidate: 0.9.4-1.1
  Version table:
     0.9.4-1.1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy/universe
```

---

### Post by andrej1741 on 2013-12-09
Open terminal and start
```
alsamixer
```
then turn on "Maser" and select maximum volume, use arrow keys.
write
```
pulseaudio
```
output here.

---

### Post by tirab on 2013-12-09
Hi. 

Thanks for the response.

I am a newbie so I'm not quite sure how to read the output of lspci but here is what seems important:

Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Juniper HDMI Audio [Radeon HD 5700 Series]

In system settings: Memory = 3.9 GiB
                           CPU = Intel core i7 CPU 860 @ 2.80 GHz * 8

---

### Post by codenine75a on 2013-12-09
I would use the test button on window manager sound effects options and just tap it a few times, maybe test to see if the speakers are on, tap some more, make sure they are plugged in.. normal first step IT troubleshooting.

---

### Post by asus-user on 2013-12-09
> **tirab said:**
> 
Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Juniper HDMI Audio [Radeon HD 5700 Series]


The problem might be different things, I advise you to force reload Alsa (_A_dvanced _L_inux _S_ound _A_rchitecture)  which is used by Ubuntu for managing sound output, and that can be done with the following command in Terminal:
```

sudo alsa force-reload

```
Make a reboot after this command, and test sounds to see if it works. 
If did not, try re-installing Alsa and Pulse audio using the following commands in Terminal:
1. Remove first in case they were installed before:
```
sudo apt-get remove --purge alsa-base pulseaudio
```
2. Install them again:
 ```
sudo apt-get install alsa-base pulseaudio

```
3. Force reload Alsa again after the new installation:
```

sudo alsa force-reload

```
4. Reboot your system.

If the previous steps did not work for you, I think it is better to go step by step troubleshooting which is explained in details in the following link:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

This might take sometime, but it is worth it.
Report back here if it worked and at what stage.

---

### Post by tirab on 2013-12-10
Okay.

Tried the steps that asus-user outlined.

These didn't work so I followed the link [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I got to step 5. I tried: [COLOR=#333333][FONT=UbuntuMono]find /lib/modules/`uname -r` | grep snd 
in the terminal but got: [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]find /lib/modules/`uname -r` | grep snd

Tried: [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]sudo apt-get install linux-restricted-modules-`uname -r` linux-generic
Got:
[/FONT][/COLOR]Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
E: Unable to locate package linux-restricted-modules-3.11.0-14-generic
E: Couldn't find any package by regex 'linux-restricted-modules-3.11.0-14-generic'

Not sure what to do now. Any help would be appreciated.

Thanks
tirab

---

### Post by asus-user on 2013-12-10
> **tirab said:**
> 
I got to step 5. I tried: [COLOR=#333333][FONT=UbuntuMono]find /lib/modules/`uname -r` | grep snd 
in the terminal but got: [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]find /lib/modules/`uname -r` | grep snd[/FONT][/COLOR]


Sorry I didn't understand, what did you get exactly after using the command?: ```
find /lib/modules/`uname -r` | grep snd
```

---

### Post by asus-user on 2013-12-10
After executing: 
```
find /lib/modules/`uname -r` | grep snd
```
> You should see a large list of items come up. If you don't, it means that the install process did not install the sound modules for you. 

> **tirab said:**
> 
Tried: sudo apt-get install linux-restricted-modules-`uname -r` linux-generic
Got:
Reading package lists... DoneBuilding dependency tree
Reading state information... Done
E: Unable to locate package linux-restricted-modules-3.11.0-14-generic
E: Couldn't find any package by regex 'linux-restricted-modules-3.11.0-14-generic'


Do these commands in Terminal first:
```

cd
sudo apt-get update
sudo apt-get dist-upgrade
```
Then:
```
sudo apt-get install linux-restricted-modules-`uname -r` linux-generic
```

Hope it works now :)

---

### Post by tirab on 2013-12-10
Sorry.

When I input: find /lib/modules/'uname -r' | grep snd
I get:
find: &#8216;/lib/modules/uname -r&#8217;: No such file or directory

Just tried the steps above but final output was:
E: Unable to locate package linux-restricted-modules-3.11.0-14-generic
E: Couldn't find any package by regex 'linux-restricted-modules-3.11.0-14-generic'

---

### Post by tirab on 2013-12-10
Okay. Sorry didn't realise before that: [COLOR=#000000]find /lib/modules/'uname -r' | grep snd
[/COLOR]required the tilde ( ` ) and not an inverted comma ( ' ). Maybe this should be explicitly stated in the docs
so that new users what get this wrong like I did.

Anyway, when I entered the command, a list of items came up so that means that the modules are installed.
[COLOR=#000000][/COLOR]Step 6 also worked properly.

Yet still no sound.

Furthermore I checked again that on Windows 8.1 sound plays normally.
I have an acer screen connected via HDMI to the computer chasis. The speakers built-in to the screen play
the sound in Windows 8.1 but no sound in Ubuntu 13.10.

---

### Post by kulen19 on 2013-12-11
> **tirab said:**
> Okay. Sorry didn't realise before that: [COLOR=#000000]find /lib/modules/'uname -r' | grep snd
[/COLOR]required the tilde ( ` ) and not an inverted comma ( ' ). Maybe this should be explicitly stated in the docs
so that new users what get this wrong like I did.

Anyway, when I entered the command, a list of items came up so that means that the modules are installed.
Step 6 also worked properly.

Yet still no sound.

Furthermore I checked again that on Windows 8.1 sound plays normally.
I have an acer screen connected via HDMI to the computer chasis. The speakers built-in to the screen play
the sound in Windows 8.1 but no sound in Ubuntu 13.10.

Sorry to hear it isn't fixed yet. Did you try the padevchooser-package?

---

### Post by tirab on 2013-12-11
Tried the padevchooser package and it shows that the sound cards are detected and should be playing sound.
Even tried turning one off via padevchooser and playing with the different settings, but still no sound.

Not sure what to do from here.

---

