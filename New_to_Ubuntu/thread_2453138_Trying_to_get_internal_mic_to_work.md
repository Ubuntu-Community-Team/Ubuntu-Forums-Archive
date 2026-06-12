---
title: "Trying to get internal mic to work"
date: 2020-11-03
forum: New to Ubuntu
---

### Post by zashinoff on 2020-11-03
Hi,

I'm new to Linux. Have installed Ubuntu 20.04 LTS on my new laptop to use as a programming environment and to learn more about programming and computer science.

First, there was no sound coming out of my speakers. So, I used emacs to edit the file /etc/modprobe.d/alsa-base.conf and appended the line "options snd-hda-intel dmic_detect=0" to the end of the file, and then rebooted the system. Alas! There was sound!

Now, I'm having trouble getting my internal microphone working. At first, there was no input device showing up under the Ubuntu>Settings>Sound menu. So I appended the line
"options snd-hda-intel model=laptop-dmic" to the end of the alsa-base.conf file. Then, I rebooted the system and it listed the built-in microphone as an input device. But when I test the mic, there's no sound coming from it. There are no orange input light bars lighting up under Sound settings when I speak into the mic. And when I run alsamixer from the terminal I made sure the mic is not muted and I even boosted the mic input. Still no sound. I don't know what else to do.

Can someone please help?

Thanks in advance!

---

