---
title: "Is headphone jack sense working for you?"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by effenberg0x0 on 2011-10-05
Is the headphone jack sense working for you guys? In my PC it plays audio together with the front speakers. The motherboard is ASUS m4A89GTD Pro/USB3, which uses **Realtek ALC892** 8-channel HD Audio Codec. The specs mention it supports jack sense and front panel connectors retasking.

Alsamixer is OK, Sense is activated, sound modules are loaded. I have tried the standard (previously working) settings on /etc/modprobe.d/alsa-base.conf (options snd-hda-intel model=Realtek ALC892, options snd-hda-intel model=asus, options snd-hda-intel model=auto) and there's no change in the way it behaves.

Options in analog-output.conf, analog-output-headphones.conf, analog-headphones2.conf at /usr/share/pulseaudio/alsa-mixer/paths seem right too.

I could not find a bug report (besides mine) pointing out something specific about this sound card. I wanted to hear from you guys if its something that affects other sound cards as well before starting to really mess with the system here.

Thanks,
Effenberg

---

### Post by rapiertg on 2011-10-05
Jack sensing is working for me on my laptop, but dont on my desktop. It occurs the problem lies in old pc case which has front panel that dont support this feature. If you want to check it try booting windows and try it there.

---

### Post by BwackNinja on 2011-10-05
It was working for me for the first time a while earlier this cycle, but not after that. Sensing is definitely working, I can see that by running something like pavucontrol, but muting of my speakers isn't happening. I've got a Realtek ALC889 and I've given up to the point of writing a script to switch between the two manually instead.

---

### Post by effenberg0x0 on 2011-10-05
> **rapiertg said:**
> Jack sensing is working for me on my laptop, but dont on my desktop. It occurs the problem lies in old pc case which has front panel that dont support this feature. If you want to check it try booting windows and try it there.

Hey,

Works on Windows 7 64 as expected. My case is new, supports the MB 6 jacks in the rear, 2 in front (analog, digital) plus internal spdif. I guess I'm gonna upgrade alsa, pulseaudio, etc. There's something different about alc892, maybe new versions already cover it.

Thanks,
Effenberg

---

### Post by effenberg0x0 on 2011-10-05
> **BwackNinja said:**
> It was working for me for the first time a while earlier this cycle, but not after that. Sensing is definitely working, I can see that by running something like pavucontrol, but muting of my speakers isn't happening. I've got a Realtek ALC889 and I've given up to the point of writing a script to switch between the two manually instead.

Ah, good tip. I was only looking at alsamixer. On Pavucontrol, I can see some sliders move as plug the headphone. But line-out and HP are tied together (they shouldn't). 

Regards,
Effenberg

---

### Post by ikt on 2011-10-08
Yes, it's not working.

My Xonar STS output isn't picked by the gnome sound utility AT ALL.

I have to go into alsamixer, choose output as headphone 1 and then it works.

edit: my bug report:

[https://bugzilla.gnome.org/show_bug.cgi?id=661268](https://bugzilla.gnome.org/show_bug.cgi?id=661268)

---

### Post by effenberg0x0 on 2011-10-12
Turns out there's was a bug, a typo in the Kernel driver, which was detected and sent upstream. 

So Realtek snd-hda-intel and, in specific, ALC892 users will have a better support for headphone / jack sense as soon as the fix is released  (for users that upgrade to the latest upstream code). 

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/871582](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/871582)

Regards,
EFfenberg

---

### Post by BwackNinja on 2011-10-13
Thank you, this has been the only thing on my computer that has had any problems on linux. Glad to see it will be fixed once and for all.

---

