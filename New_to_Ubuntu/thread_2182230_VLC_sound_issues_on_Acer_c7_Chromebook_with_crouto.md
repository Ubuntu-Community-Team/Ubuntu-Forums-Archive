---
title: "VLC sound issues on Acer c7 Chromebook with crouton installed"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by tigerucla on 2013-10-20
Please be gentle with me- I am an absolute newbie.  I have an Acer C710-2856 with ubuntu 12.04 XFCE.  I installed VLC so I could watch video (duh!) and am having problems with the sound.  (No problem watching Youtube videos- I've installed restricted extras.)  When I try to watch a video (.vob or .mov) at first it seems as if there is no sound.  Then if I turn the volume way up, I can hear sound, but it's in and out and seems to be a continuous 1-2 second loop.  Sometimes I get a very loud crackly sound instead.

I've tried changing the audio settings in VLC (tools/preferences/audio- both output module and device) with no luck.

Thanks for your help.

---

### Post by tigerucla on 2013-10-22
OK, so if no one has any ideas how to fix this, would uninstalling and reinstalling VLC likely fix the issue?  If so, what is the best way to uninstall/reinstall?

Thanks

---

### Post by newb85 on 2013-10-22
I would try

```
 sudo apt-get purge vlc
sudo apt-get autoremove
sudo apt-get install vlc 
```

---

### Post by tigerucla on 2013-10-22
Thanks newb85.  I did that, and now I have no sound at all in VLC.  Still have normal sound in Youtube, for example.

Anyone?  Anyone?

---

### Post by newb85 on 2013-10-22
Hmm...  In VLC, under Tools>Preferences - Audio, what is the Output Mode?

---

### Post by tigerucla on 2013-10-23
Currently it's "default".  But I've tried them all, including ALSA.

---

### Post by tigerucla on 2013-10-24
Well, I'm not sure how, but it's now fixed.  I installed Totem and uninstalled VLC (using purge then autoremove as suggested).  Totem worked, but I was not completely happy with the quality.  So I again reinstalled VLC.  I was planning on trying some things I saw on other threads.  But after reinstalling again, it works!  I don't know if unistalling/reinstalling again did the trick.  Or maybe there was something which happened when installing Totem to change how VLC works.  All I know is that I'm glad.  Thanks newb85 for your help.

---

### Post by josh37 on 2014-02-19
I have a HP chromebook 14 (crouton-xfce) and was having the same issue so I tried the following:

sudo apt-get install totem
sudo apt-get purge vlc
sudo apt-get autoremove
sudo apt-get install vlc

And now it works.  I have no idea why or what part fixed it but it works...

---

### Post by Opalinus on 2014-02-27
> **josh37 said:**
> I have a HP chromebook 14 (crouton-xfce) and was having the same issue so I tried the following:

sudo apt-get install totem
sudo apt-get purge vlc
sudo apt-get autoremove
sudo apt-get install vlc

And now it works.  I have no idea why or what part fixed it but it works...

tried but still same issue. Then I installed the jack server which seems to fail when I try to start the video with totem (before installation of pulseaudio the sound was clear but very very low but after pulseaudio installation (btw it still told me it couldnt be started) just cracking...)

but it works now with vlc like a charm.

so for me worked:

sudo apt-get install pulseaudio

thanks for you all :)

---

### Post by David_Zhou on 2015-01-28
Thank you Josh37, your recipe helped me. I have a Toshiba Chromebook 2 (crouton+xfce4) and have exactly same issue, and the recipe of installing totem, following by removing and then reinstalling vlc did the wonders. Many thanks!

> **josh37 said:**
> I have a HP chromebook 14 (crouton-xfce) and was having the same issue so I tried the following:

sudo apt-get install totem
sudo apt-get purge vlc
sudo apt-get autoremove
sudo apt-get install vlc

And now it works.  I have no idea why or what part fixed it but it works...

---

