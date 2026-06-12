---
title: "Optical Drive - Cannot read from resource"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Dark006 on 2008-07-08
I'm having a problem with the optical drive on my HP laptop not playing DVD's. It will play music, and recognize a DVD, but not play it. I've also tried the same DVD with an external USB drive, and it still doesn't work. It will open Totem Movie Player but says, "Cannot read from resource" when it tries to play. 

Any ideas anyone?

---

### Post by ChameleonDave on 2008-07-08
You may have a codec problem.  Have you added the Medibuntu repositories to your list?  

If not, do so.  Open your repository list with a command such as the following:

(to edit entirely on the command line)
```
sudo nano /etc/apt/sources.list
```

(for Ubuntu/GNOME)
```
gksudo gedit /etc/apt/sources.list
```

(for Kubuntu/KDE)
```
kdesudo kwrite /etc/apt/sources.list
```

(for Xubuntu/Xfce)
```
gksudo mousepad /etc/apt/sources.list
```

Then, paste the following lines into it:
```

## Repositories for proprietary media
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

```

Save.

Then do the following commands in a terminal:

```

sudo apt-get update && sudo apt-get install libdvdcss2 non-free-codecs

```

---

### Post by NLCarrII on 2008-07-08
I did the same thing as above this morning.  Installed the medibuntu, libdvdcss2, and all the dvd codecs I could find using synaptic.  It did not work after that.  I gave up, shut down the comp and when I came back this afternoon, it worked.  I guess all it needed was a restart.

---

### Post by reeseslover531 on 2008-07-08
you can also try and use vlc to test stuff as well, I am pretty sure VLC can play DVDs.

---

