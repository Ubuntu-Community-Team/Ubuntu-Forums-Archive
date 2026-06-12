---
title: "[SOLVED] cannot save nvidia prefs to xorg.conf; awn doesnt open"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by Zopiac on 2008-06-28
in the nvidia settings, i cannot save the prefs to the file, therefore cannot, say KEEP the res., etc. anyone know a way to do this? for some reason this doesnt work:

```
sudo gedit /etc/X11/xorg.conf
```

replies

```
cannot open display:
Run 'gedit --help' to see a full list of available command line options.
```



also, awn doesnt open. well, it DOES open....for about 2 seconds. then it just closes!

---

### Post by fs3rp4 on 2008-06-28
> **Zopiac said:**
> in the nvidia settings, i cannot save the prefs to the file, therefore cannot, say KEEP the res., etc. anyone know a way to do this? for some reason this doesnt work:

```
sudo gedit /etc/X11/xorg.conf
```

replies

```
cannot open display:
Run 'gedit --help' to see a full list of available command line options.
```



also, awn doesnt open. well, it DOES open....for about 2 seconds. then it just closes!


Try this:

alt+F2

gksu gedit /etc/X11/xorg.conf

---

### Post by aimpau on 2008-06-28
I think editing your xorg.conf requires the **dpkg** something command...

---

### Post by Elfy on 2008-06-28
Use nvidia-settings as root

```
gksudo nvidia-settings
```

> I think editing your xorg.conf requires the dpkg something command...
no you should be able to edit with any editor as long you give it root rights to do so.


All that aside do you have problems opening gedit anyway?

No idea about awn I'm afraid.

---

### Post by Zopiac on 2008-06-28
> **forestpixie said:**
> Use nvidia-settings as root

```
gksudo nvidia-settings
```
All that aside do you have problems opening gedit anyway?


no...i should mark this thread a solved.

It seems that it just couldnt overwrite/delete the backup of the file, but it saved it just fine. wierd.

---

### Post by madhi19 on 2009-07-01
How hard could it be to make the Nvidia settings app load as sudo just like the update manager and many other administration application!

---

