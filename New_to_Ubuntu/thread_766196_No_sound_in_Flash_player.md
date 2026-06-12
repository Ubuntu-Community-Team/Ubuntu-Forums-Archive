---
title: "No sound in Flash player"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by rockstarrem on 2008-04-25
Hey guys,

Just installed a flash player for Firefox in my browser, even though under properties "Enable Sound" is checked I still don't hear sound. The flash player is laggy as hell too.

Any suggestions/fixes?

EDIT: It's ALL flash actions, I can turn the slider up on the volume in the YouTube SWF file but nothing happens for an example.

---

### Post by Saya on 2008-04-25
Are you on Hardy? 

If so, Preferences -> Sound -> Devices, change everything to ALSA -> Sounds, uncheck Enable software sound mixing (ESD). Restart or do pulseaudio -k.

---

### Post by rockstarrem on 2008-04-25
Thanks for the reply,

I did what you said and I got no audio at all, I reverted all to Multi Channel Playback and I got sound fine NORMALLY, but still not in Flash. Anything else I can do?

---

### Post by Saya on 2008-04-25
> **rockstarrem said:**
> I did what you said and I got no audio at all
Right. Sorry about that.

Did you install gnash or flashplugin-nonfree?

---

### Post by rockstarrem on 2008-04-25
No I haven't done that, I'm sorry for the noob question but is it just apt-get gnash and apt-get flashplugin-nonfree?

---

### Post by Saya on 2008-04-25
> **rockstarrem said:**
> Just installed _a flash player_
This is what I'm asking about. Try sudo apt-get remove gnash and sudo apt-get install flashplugin-nonfree. (mind that it is in the multiverse repository, which you have to enable in System -> Administration -> Software Sources)

---

### Post by Xiong Chiamiov on 2008-04-25
Gnash is an open-source version of flash; you only need one or the other.  Are you seeing flash animations, just not hearing them?  If you, then you already have either gnash or flash installed (open synaptic and search for them to see which one it is).  If not, [here]("http://www.psychocats.net/ubuntu/flash")'s a good tutorial to getting it.

Aside from that, Adobe refuses to fix flash for Linux so that it will work properly, so blame them.

---

### Post by rockstarrem on 2008-04-25
It says that I have neither but I'm seeing Flash, just not hearing it. Should I try installing one? I swear I did from the Missing Plugins menu and even manually from Adobe's tar.bz2. 

If I should install one, which one should it be?

---

### Post by Saya on 2008-04-25
> **rockstarrem said:**
> If I should install one, which one should it be?
flashplugin-nonfree, unless you're a open source purist. Gnash is inferior in every way.

---

### Post by rockstarrem on 2008-04-25
It said it just installed the installer, where can I find this in my file system?

---

### Post by Saya on 2008-04-25
> **rockstarrem said:**
> It said it just installed the installer, where can I find this in my file system?

System -> Software Sources -> Check "Software restricted by copyright or legal issues (multiverse)"
Reload the package list and install flashplugin-nonfree with apt-get or Synaptic. Nothing else required.

---

### Post by rockstarrem on 2008-04-25
Hmm, I'm getting this error:

> 
E: Invalid operation flashplugin-nonfree


I'm running:

> 
sudo apt-get flashplugin-nonfree


Is there something I'm doing wrong?

---

### Post by Saya on 2008-04-25
> **rockstarrem said:**
> Is there something I'm doing wrong?
Yeah, you need to do sudo apt-get install flashplugin-nonfree

---

### Post by rockstarrem on 2008-04-25
Ah, it is already installed :P.

Still not getting audio though, I'll try a restart.

---

### Post by rockstarrem on 2008-04-25
You're not going to believe this but it's a flash problem. I just figured it out now, I'm on ImageShack and using their flash browser no actions work. So, any suggestions?

---

### Post by HunterThomson on 2008-04-25
You did check you alsa mixer and setting/configure and tick everything and turn everything up right?

---

### Post by rockstarrem on 2008-04-25
> **HunterThomson said:**
> You did check you alsa mixer and setting/configure and tick everything and turn everything up right?

Thanks for the reply,

How would I do that?

---

### Post by HunterThomson on 2008-04-25
click on the sound icon in the top bar on the screen. Double right click it or like left click it and open up the mixer window (I use KDE Kubuntu not Gnome Ubuntu little different) when the window opens with all the volume sliders. Click on settings in the top. Then click on settings then click on configure/or what ever... you should now have a window open that has a bunch of names like PCM mic front.... tick them all and close.... then un-mute all and turn all up. Then try again.... PCM is the one I am pretty sure. Should work sound like a sound problem not a flash problem.

---

### Post by HunterThomson on 2008-04-25
I use the adobe flash with no problems....

---

### Post by Xiong Chiamiov on 2008-04-25
Also run ```
alsamixer
``` in the terminal.  You can navigate left and right with the arrow keys, and adjust volumes with up and down.

Flash seems to be a mixed bag.  Either it works great, or absolutely terribly.  It also doesn't seem to have anything to do with certain configurations, but rather strikes at random.

---

### Post by rockstarrem on 2008-04-25
Ahh, I figured out it wasn't a sound problem though, it's flash itself. Actions aren't recognized. Like, pulling the slider on YouTube.

---

### Post by mister_pink on 2008-04-25
Dont think anyones posted this - you need to install libflashsupport to get sound working properly in flash.

---

### Post by Saya on 2008-04-25
> **mister_pink said:**
> Dont think anyones posted this - you need to install libflashsupport to get sound working properly in flash.
However this will make it very unstable, which is why it was removed as a dependency. See [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888)

---

### Post by rockstarrem on 2008-04-25
Installed it, tried it, but Flash still isn't recognizing actions.

---

### Post by rockstarrem on 2008-04-25
I'm going to be heading to bed, if I can't still sleep I'll be up again. I'll definitely check in about 4-5 hours though.

---

### Post by Comreak on 2008-04-25
I'm also using Flash 9 and Hardy, and I'm having the same issue with sound in flash apps.  I'm not having any issues with flash controls or widgets, however.  I've tried everything suggested so far, no luck.  I've also tried using apt-get's 'purge' command with flashplugin-free and installing the plugin manually (as mentioned in another thread), no luck there either.  Sound works fine in other apps. (like Rhythmbox, for example).

---

### Post by Comreak on 2008-04-25
Alright, I got sound working in flash, here's what I did (thanks to a suggestion by ikkefc3 in [this]("http://ubuntuforums.org/showthread.php?t=745221") thread):

-Install the 'libflashsupport' package using Synaptic

-Set everything to 'PulseAudio Sound Server' under 'System>Preferences>Sound'

-Rename the '.pulse' folder under your home directory to something else (like '.pulse-bak') using the following:
```
mv .pulse .pulse-bak
```
Or, alternatively remove it using:
```
rm -r .pulse
``` 

After doing all this for myself, audio worked in Flash apps.  

There seem to be stability issues with libflashsupport, though.  Pressing the backward and forward button several times while watching a YouTube video eventually caused firefox to crash.  At least audio is working in flash, though!

---

### Post by duojet on 2008-04-28
This seems to be a relatively common issue, doesn't it? Here's what I've tried so far on my kubuntu 8.04 upgrade (from dapper)

un/reinstalling flash-plugin (which won't re-install anymore in adept)
un/reinstalling gnash
un/reinstalling flashplugin-nonfree
manually installing flashplugin-nonfree
switching sound servers (although I don't see an option to select Pulse)
editing the firefox rc file (to alsa, then alsa-oss, then aoss)
downgrading libflash
re-upgrading libflash
renaming the .pulse file

none of this has worked. 
any other ideas?

---

### Post by rootie on 2008-05-14
> **Saya said:**
> Are you on Hardy? 

If so, Preferences -> Sound -> Devices, change everything to ALSA -> Sounds, uncheck Enable software sound mixing (ESD). Restart or do pulseaudio -k.

I had been having strange problems with audio. I couldn't play videos in totem while using Pidgin with sound alerts or while watching something on YouTube. (Then, both system sounds and Pidgin were set to ALSA.) I followed the instructions in your post (and also changed Pidgin's sound method to "automatic") and solved a problem I'd been bearing with since Hardy's release. Thanks very much. :D

---

### Post by marko on 2008-05-19
I have nothing to offer other than I sympathize completely. I am in the same boat as you guys.  Kubuntu - Heron - KDE4.  Nonfree Flash, libsupport installed, no sound.

This is a bummer.  Hoping new release of Flash will be available soon and might fix this.  Kinda weird to have a box that can do avi, quicktime, etc, but no flash..  YUK.

---

### Post by Hypo_Mix on 2008-05-19
Same issue here, full sound except for youtube (probably all fash but i havent tested it)

using USB headset.

---

