---
title: "I think I've got three drivers installed (i need to remove them)"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by koba101 on 2008-05-05
Hi,



I'm trying to resolve the issue where i need the sound to be muted from the headphone once i plug the mic in.

Someone suggested that i should install alsa 1.0.16 which is what i did.  However, I might've not installed it correctly.  I then installed 1.0.15.  Some changes happened but to the worse.  All what changed was that I can't control the sound from the keyboard (it seems that the keyboard is still working on the old version of 1.0.14).

In addition to all of this, when i type alsaconf, I get the message that thsi is 1.0.15.

So i think i'm having 3 drivers installed at once, my intention is to remove all three of them and install the newest (probably 1.0.16)



Can anyone help me out here?  I've got gutsy installed and this is really annoying

---

### Post by TeoBigusGeekus on 2008-05-05
How did you install them? The way of installation dictates the way of unistallation...

---

### Post by kwacka on 2008-05-05
How did you install them?

If you used Add/Remove Programs or Synaptic it would remove old/install latest version.

A graphic interface (such as gnome-alsamixer) might be useful

---

### Post by koba101 on 2008-05-06
The way I've installed is download the ta.gz folder which has three folders one for utils the other for drivers the other for itself. 

the tried

```
./configure
./sudo make
./sudo make install
```

I did this for both 1.0.15 and 1.0.16.

Of course 1.0.14 was there by default when I installed gutsy

---

### Post by TeoBigusGeekus on 2008-05-06
In their original folders type
```
sudo make uninstall
```

---

### Post by koba101 on 2008-05-06
i'll try this as soon as i get home...the thing is, i want to uninstall 1.0.14 as well in order to put the latest in.  how do i do that?

---

