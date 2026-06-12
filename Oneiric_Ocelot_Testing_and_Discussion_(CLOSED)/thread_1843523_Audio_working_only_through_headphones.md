---
title: "Audio working only through headphones"
date: 2011-09-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lgp171188 on 2011-09-13
After installing oneiric beta1 through a clean install, audio has been working only through the headphones. alsamixer has 100% for master and speaker (there is no front option). Sound works through the speakers in Windows.

HP Pavilion dv9704tx

```
guruprasad@kal-el:~$ head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC268

==> /proc/asound/card0/codec#1 <==
Codec: Motorola Si3054
```

---

### Post by cariboo on 2011-09-14
Do you have the output connector set properly in sound preferences. See screenshot.

---

### Post by lgp171188 on 2011-09-14
> **cariboo907 said:**
> Do you have the output connector set properly in sound preferences. See screenshot.
Let me check that and get back. Thanks.

---

### Post by 10Digits on 2011-09-14
Or you could try to change the sound output hardware from here... I am also using ocelot and the sound is working fine...maybe you should switch it to something like Analogue Stereo Duplex. cuz otherwise the microphone won't work....

               on the other hand my microphone doesn't work even though I have it set to analogue stereo duplex...so try it out...screen-shot included for your convenience.

---

### Post by lgp171188 on 2011-09-14
> **10Digits said:**
> Or you could try to change the sound output hardware from here... I am also using ocelot and the sound is working fine...maybe you should switch it to something like Analogue Stereo Duplex. cuz otherwise the microphone won't work....

               on the other hand my microphone doesn't work even though I have it set to analogue stereo duplex...so try it out...screen-shot included for your convenience.
Let me try that too and get back. Thanks.

---

### Post by lgp171188 on 2011-09-14
> **cariboo907 said:**
> Do you have the output connector set properly in sound preferences. See screenshot.
Hi I checked my connector setting. The only options available are Analog speakers and Analog headphones. Mine is set to analog speakers. Setting it to analog headphones doesn't work either :-(

---

### Post by lgp171188 on 2011-09-14
> **10Digits said:**
> Or you could try to change the sound output hardware from here... I am also using ocelot and the sound is working fine...maybe you should switch it to something like Analogue Stereo Duplex. cuz otherwise the microphone won't work....

               on the other hand my microphone doesn't work even though I have it set to analogue stereo duplex...so try it out...screen-shot included for your convenience.
Mine is set to Analog stereo duplex and still it doesn't work :(

---

### Post by lgp171188 on 2011-09-14
Don't know what the issue was. I did a apt-get update && aptitude safe-upgrade which I do daily. In today's updates, there were pulseaudio updates along with some kernel updates. So after installing them and rebooting, audio through my laptop speakers is working.

---

### Post by newyorkcityjay on 2011-09-15
This keeps happening to me... I know the sound was working on headphones b/c I was watching Hulu, but when I unplugged the headphones and went to Pandora there was no sound.  Skype was dead too.  I logged out and back in (but not a full reboot) and the problem persisted.  I went to my settings and sound and noticed the same as above - my setting was switched to headphones.  I switched to speakers and it did not fix right away though.  When I changed the volume level - just nudged it - the sound came back on.

To repair:
1. Go to System Settings | Sound
2. On the Output tab switch the connector to Analog Speakers
3. Adjust the volume level

This still seems to be a bug, but at least the above is a workaround.

---

### Post by lemsto on 2011-09-18
Please see bug [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/852915](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/852915)

---

