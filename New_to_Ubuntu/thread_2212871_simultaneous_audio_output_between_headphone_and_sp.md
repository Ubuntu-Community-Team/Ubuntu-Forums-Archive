---
title: "simultaneous audio output between headphone and speaker Panasonic Toughbook cf-74"
date: 2014-03-23
forum: New to Ubuntu
---

### Post by lou1 on 2014-03-23
Hello, I am having an issue with the audio coming from both the speaker and the headphone outputs when I plug in my earbuds on a Panasonic Toughbook cf-74. I am running ubuntu 12.04 LTS and I have tried setting the model by editing /etc/modprobe.d/alsa-base.conf by putting "options snd-hda-intel model=panasonic" (without the quotes) at the end of the file, as per the information on the ubuntu wiki:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

The exact model for my laptop was in the document located here in the panasonic entry:
[http://lxr.linux.no/linux+v3.2.19/Documentation/sound/alsa/HD-Audio-Models.txt](http://lxr.linux.no/linux+v3.2.19/Documentation/sound/alsa/HD-Audio-Models.txt)


I'm still having the same issue and am wondering if there is anyone here who knows what the deal is, or if I have to do other things and whatnot. I've seen other information that mentions jack sensing or something like that, and that it isn't being detected. This issue doesn't surface on windows XP and that's what has gotten me thrown for a loop.

Thank You.

---

### Post by meathdeath on 2014-03-23
I had this problem once. What I did to fix it was to use duct tape. Not even joking. Just open up the laptop (make sure it's off first and battery is removed) and then cut the wire leading from the motherboard to the speaker. If it's integrated you could just remove it. Only problem comes in when you actually WANT to have sound come out of your laptop. Hope that helps. 

-meathdeath

---

### Post by lou1 on 2014-03-27
I think the issue seems to have resolved itself. I updated the alsa driver to the latest from a ppa here: [https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily](https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily).

I also tried the newest beta, 14.04 amd64 and it didn't have that issue.

---

