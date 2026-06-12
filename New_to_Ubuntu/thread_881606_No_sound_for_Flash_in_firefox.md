---
title: "No sound for Flash in firefox?"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by idodos on 2008-08-06
just installed Ubuntu but whenever i try to run a flash file from firefox like in Youtube, I don't have sound.
anyone knows a possible solution for this?

Thanks in advance.

---

### Post by kestrel1 on 2008-08-06
Do you have the latest version of flash player?
I think this is the latest: Shockwave Flash 9.0 r124
Does sound work for other things?

---

### Post by sharks on 2008-08-06
just install flashplugin-nonfree from synaptic

---

### Post by mevets on 2008-08-06
For some people, and myself, pulseaudio can mute flash. An easy workaround is to change everything to ALSA in System > Preferences > Sound

Im just throwing that out there because a lot of people run into that problem on this forum.

---

### Post by spaceship.rodeo on 2008-08-06
I'm getting this problem too.  I just did a clean install of hardy, and the only thing wrong is that there's no sound in any flash applications.  I have flashplugin-nonfree already install and I just changed everything to ALSA and that also didn't do anything.

---

### Post by ktrnka on 2008-08-06
you will also need libflashsupport

```
sudo apt-get install libflashsupport
```

and then pulseaudio will work

(Don't forget to completely close and then reopen firefox)

---

### Post by philinux on 2008-08-06
> **ktrnka said:**
> you will also need libflashsupport

```
sudo apt-get install libflashsupport
```

and then pulseaudio will work

IIRC thats installed by default.

---

### Post by ktrnka on 2008-08-06
> **philinux said:**
> IIRC thats installed by default.

I have always had to manually install it. It hasn't once been installed as a dependency, (at least for me). I really wish it would.

---

### Post by spaceship.rodeo on 2008-08-06
Yeah, it wasn't installed for me either.  It did work though, so thanks.

---

### Post by ktrnka on 2008-08-06
> **spaceship.rodeo said:**
> Yeah, it wasn't installed for me either.  It did work though, so thanks.

Did you switch back from alsa to pulsaudio? Did you also make sure firefox was completely closed after you installed it? Including the "Download" window?

---

