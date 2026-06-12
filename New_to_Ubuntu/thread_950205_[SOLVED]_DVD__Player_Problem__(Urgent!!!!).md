---
title: "[SOLVED] DVD  Player Problem  (Urgent!!!!)"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by donaldshelton on 2008-10-16
I want to show a DVD (commercial) to my class tomorrow.

I have Ubuntu 8.10 installed, with Movie Player, MPlayer, Dragon Player, 

Kaffiene, and Ogle installed.  None of these play my DVD.

Any help to get this going will be appreciated.

None of these recognize that there is a DVD in the drive.  An icon appears on the desktop.

---

### Post by eternalnewbee on 2008-10-16
> **donaldshelton said:**
> I want to show a DVD (commercial) to my class tomorrow.

I have Ubuntu 8.10 installed, with Movie Player, MPlayer, Dragon Player, 

Kaffiene, and Ogle installed.  None of these play my DVD.

Any help to get this going will be appreciated.

None of these recognize that there is a DVD in the drive.  An icon appears on the desktop.

What does the icon say?

---

### Post by GuitarRocker2562 on 2008-10-16
install vlc, great for DVD playing, and everything else too. But it sounds like you need to install a package called libdvdcss (or smething there about)

---

### Post by eternalnewbee on 2008-10-16
> **GuitarRocker2562 said:**
> install vlc, great for DVD playing, and everything else too. But it sounds like you need to install a package called libdvdcss (or smething there about)

Yes, something like that.
Try searching for "dvd playback" in Add/REmove or in Synaptic.

---

### Post by Flynn555 on 2008-10-16
taken from [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support)

**Multimedia Support**
type the following in terminal
```

 sudo apt-get update
 sudo apt-get install ubuntu-restricted-extras

```

**DVD Support**
add these lines to the end of /etc/apt/sources.list
```

  ## Medibuntu - Ubuntu 8.04 "hardy" 
  ## Please report any bug on https://bugs.launchpad.net/medibuntu/ 
  deb http://packages.medibuntu.org/ hardy free non-free

```

then, type the following in terminal
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

sudo apt-get update 
   
sudo apt-get install libdvdcss2

```

**Installing VLC** *recommended*
type the following in terminal
```

sudo apt-get install vlc

```

i hope this helps

---

### Post by donaldshelton on 2008-10-16
[B]Thanks to all who helped me solve this problem

Kaffiene works great with this,as I am able to go to the title menu and choose both subtitles and Spanish for the audio.  I teach Spanish, and this allows the kids to hear the Spanish and read the English.

Muchas gracias a todos!!!!!:guitar::guitar::guitar:[/B]

---

### Post by GuitarRocker2562 on 2008-10-16
de nada

---

### Post by Flynn555 on 2008-10-16
no prob ;)

---

