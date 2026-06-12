---
title: "No Sound HDMI HD6850"
date: 2013-05-08
forum: New to Ubuntu
---

### Post by exadmasta on 2013-05-08
Hello, I'm having issues getting sound working with my HD6850 through HDMI to the TV. I did a bit of research and found a solution that seems to work for most people but it doesn't seem to work for me. I'm using ubuntu 13.04 64 bit

when I do aplay -l I get 

card 0: PCH [HDA Intel PCH], device 0: ALC898 Analog [ALC898 Analog]  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC898 Digital [ALC898 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So I created /etc/asound.conf with:

pcm.!default {
   type hw
   card 1
   device 3
}

Then sudo alsa reload

Then unmuted ATI R6xx HDMI in alsamixer

But it didn't seem to make a difference.

I'm at a loss, anyone have any ideas as to what may be going wrong?

---

### Post by 0N3 on 2013-05-09
Are you using closed source drivers (AMD) or the open source drivers that were installed when you installed Ununtu?

---

### Post by deri on 2013-05-09
Try the ati drivers, closed ones. I only need to install those to get audio work via hdmi. I am using amplifier, not tv.

---

### Post by exadmasta on 2013-05-09
I'm using the latest stable closed source ati drivers. Sorry, I fell asleep lol

---

### Post by 0N3 on 2013-05-09
Im using the beta drivers but to get then to work I had to use the alsa daily ppa

```
sudo add-apt-repository ppa:ubuntu-audio-dev/alsa-daily 

sudo apt-get update && sudo apt-get upgrade
```

Worked for me

---

### Post by exadmasta on 2013-05-09
Thanks a million, I'll try that as soon as I get home and update the thread as to whether or not it worked for me.

---

### Post by 0N3 on 2013-05-09
Cool best of luck

---

### Post by exadmasta on 2013-05-09
Hmm, unfortunately, that didn't have any effect for me. I must be missing something.

---

### Post by 0N3 on 2013-05-09
Can you download [COLOR=#000000]pavucontrol and install it and under the output settings it should look something similar to my screen shot

```
sudo apt-get install [/COLOR][COLOR=#000000]pavucontrol[/COLOR]
```

Are you selecting the HDMI option from the sound menu?

If you could upload a screenshot like mine please.

---

### Post by 0N3 on 2013-05-09
```
sudo apt-get install [COLOR=#000000]pavucontrol[/COLOR]
```


Sorry corrected my mistake

---

### Post by exadmasta on 2013-05-09
> **0N3 said:**
> ```
sudo apt-get install [COLOR=#000000]pavucontrol[/COLOR]
```


Sorry corrected my mistake

when i had originally installed the drivers, i did an automatic install, ive since done a proper distro specific install which went smoothly and seems to display my card.

so i installed pavucontrol but have no hdmi output to select. i didnt in the default sound settings either.

[ATTACH=CONFIG]242407[/ATTACH]

*edit* i did more research. seems to be a kernel bug ugh... ill probably downgrade to 12.04 until its fixed or downgrade kernel to 3.8.0-17.
[http://askubuntu.com/questions/285920/no-sound-through-hdmi-out-13-04](http://askubuntu.com/questions/285920/no-sound-through-hdmi-out-13-04)

---

### Post by 0N3 on 2013-05-09
Post results of

```
[COLOR=#000000][FONT=Ubuntu Mono]aplay -l[/FONT][/COLOR]
```

---

### Post by exadmasta on 2013-05-09
> **0N3 said:**
> Post results of

```
[COLOR=#000000][FONT=Ubuntu Mono]aplay -l[/FONT][/COLOR]
```

i actually fixed it by downgrading the kernel. can now select hdmi in sound devices and sound works,

Thanks again for all your help. It's greatly appreciated.

---

