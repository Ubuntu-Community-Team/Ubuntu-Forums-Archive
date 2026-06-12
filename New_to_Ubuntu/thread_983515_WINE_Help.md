---
title: "WINE Help"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Sly-.- on 2008-11-15
Hey, I want to use WINE, never have done before. I just installed Ubuntu 8.10, and install WINE from Applications > Add/Remove. Can someone please help me to configure it correctly to use my Windows applications, or link me to a guide. 

If I go to Configure WINE, and go to my C drive where Windows is installed, go to Program Files, it don't have any of my Windows apps there. Am I missing something?

Thanks.

---

### Post by shifty_powers on 2008-11-15
you've installed wine, which is a bunch of libraries to enable you to run windows apps. however it doesn't install any windows apps in of itself.

if you want to configure wine then

```
winecfg
```

in a terminal will do the trick. what do you want to install?

---

### Post by Sly-.- on 2008-11-15
I get this when entering that.

> err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer


I want to run Photoshop, and some games.

Thanks.

---

### Post by shifty_powers on 2008-11-15
[http://appdb.winehq.org/](http://appdb.winehq.org/)

will give you all the info you need on whether you can run individual apps :D

---

### Post by Kellemora on 2008-11-15
Hi Sly

I'm not sure, but I don't think Photoshop will run in Wine because it probably makes API calls.  Numerous games also make API calls so they won't run either!

TTUL
Gary

---

### Post by shifty_powers on 2008-11-15
earlier versions run quite well, cs1 and before.

but the cs2 and cs3 editions are only rated bronze...

---

### Post by Sly-.- on 2008-11-15
Thanks, I've just added all the libraries, the thing you told me to do before didn't work, any idea why?

---

### Post by sirjoebob on 2008-11-15
There are a lot of good resources for wine including full walk throughs. This may be better than asking on a forum. I have found plenty of excellent program-specific and general wine tutorials in the past but do not have them to link right now.

---

