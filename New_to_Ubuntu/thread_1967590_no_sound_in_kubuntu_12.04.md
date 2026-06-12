---
title: "no sound in kubuntu 12.04"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by aravind4j on 2012-04-28
[SIZE="3"][B]hey i'm fairly new to ubuntu and i updated it to 12.04 yesterday but there was no sound in 11.04 & 12.04

i've tried using rm command and it seems to work until next reboot 
i have a sound blaster 5.1VX sound card and even after trying the rm pulse audio command the rear speakers are not working 

i've uploaded the stats to [/B][/SIZE]

[SIZE="4"]*[http://www.alsa-project.org/db/?f=a9770a14f51d94f91f3850a79104e202d26baf5b](http://www.alsa-project.org/db/?f=a9770a14f51d94f91f3850a79104e202d26baf5b)*[/SIZE]

PLEASE HELP !!

---

### Post by iseijin on 2012-04-28
What do you mean you used the rm command? What were you removing? Do you mean you were trying to uninstall pulse audio? If you are trying to uninstall something you should use:

```
sudo apt-get purge <package_name>
```

This should remove any configuration files/folders associated with the package.

If you want to keep the files then you can use:

```
sudo apt-get remove <package_name>
```

I personally don't use pulse audio and stick with Alsa. The following shows how you can remove it if that is your wish.
[https://wiki.ubuntu.com/PulseAudio]("https://wiki.ubuntu.com/PulseAudio")

---

### Post by aravind4j on 2012-04-30
i was following the instructions given in [http://ubuntuforums.org/showthread.php?t=1845555](http://ubuntuforums.org/showthread.php?t=1845555)
but it makes my sound system work only problem is that i've to input command every time i login to make it work !!

---

### Post by vipin.balakrishnan on 2012-05-01
Hi aravind4j

From your ALSA log. I can find you have two sound card.

!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_ca0106

Which soundcard selected in Kubuntu 12.04 for playing sound?

The problem might be you are not selected the appropriate sound card in setting.

One more question, are you getting any sound while playing audio file(or mp3 file)??

---

### Post by aravind4j on 2012-05-04
i've selected prefer ca0106 in phonon and followed instructions in ubuntu troubleshooting page so yes i can hear mp3 sound now but the only problem now is there is no sound in rear speakers !!

---

### Post by aravind4j on 2012-12-21
The issue has been solved thank you people ):P 
It was because the sound settings that i had failed to adjust :o

Thank you :)

---

