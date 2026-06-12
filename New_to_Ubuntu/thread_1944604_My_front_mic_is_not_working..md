---
title: "My front mic is not working."
date: 2012-03-21
forum: New to Ubuntu
---

### Post by venom104 on 2012-03-21
Okay here is the deal, my brother bought me this new computer for my birthday, and I installed Ubuntu 10.04 LTS x64 on it. The sound at first did not work, I had to put this ( options snd-hda-intel model=generic)  in my /etc/modprobe.d/alsa-base.conf file. The sound then worked (from the back ports). 

If I try pretty much any other model (I've tired 6stack, 3stack, and auto), alsamixer will not work and I wont have any sound. I've tried some of the suggestions on this page, and I still can't figure it out ( [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845) ).

Here is the output of cat /proc/asound/card0/codec#* | grep Codec 
"Codec: Realtek ID 887"

Here is the output of aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I COULD HAVE SWORN I entered the first command and I got the output ACL887, so I think that is the chipset that I am using.

Please help me, I've googled this for hours and have found no reponse to my query.

And if you're going to tell me to google it, please include the phrase, because I've tried multiple searches with no avail.

---

### Post by HiImTye on 2012-03-21
is this a USB mic or just a mic connected with a headphone type jack?

---

### Post by venom104 on 2012-03-23
> **HiImTye said:**
> is this a USB mic or just a mic connected with a headphone type jack?


SORRY for the late response, I had a bunch of work to do for the 5 class I'm taking. Anyway, no it's not a USB mic, it's just one of those two prong headsets that they sell on ebay for 2 bucks. You put one end in the microphone slot, and one end in the speaker port.

---

### Post by mapeper on 2012-06-28
actually i got the same chip and could get the microphone to work (but with a lot of noise) by choosing
```
options snd-hda-intel model=asus
```
int /etc/modprobe.d/asus-base.conf

(this was an educated guess, because the Motherboard, that comes with the chipset is from ASUS, but should not be considered a final solution)

---

### Post by jmfal on 2012-06-28
If that doesn't work open alsamixer and make sure the "mic" control is not muted, and increase the volume to about 75-80

---

### Post by mapeper on 2012-07-01
The problem with that solution is, that the mic is working, but also the labels in the mixer are mixed up.
I dont have any sound input, if i mute either Digital OR Front Mic. 
I have to set booth to a >0 value, to have the mic working, but with a lot of noise, that gets less loudly, if i pull down Digital, but with it also the Mic input goes down.

---

