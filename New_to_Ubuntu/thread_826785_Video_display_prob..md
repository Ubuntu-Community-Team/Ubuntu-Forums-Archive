---
title: "Video display prob."
date: 2008-06-12
forum: New to Ubuntu
---

### Post by nnjond on 2008-06-12
Hi, can anyone help me ?

Movie Player only runs the sound of my .avi files and Mplayer won't double size or fullscreen. Any suggestions please.

---

### Post by alienexplorers on 2008-06-12
have you tried using VLC?

---

### Post by bijeeshvs on 2008-06-12
try installing vlc from synaptic or u can get it here
[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

its an excellent thing with a lot of codecs...............

---

### Post by billgoldberg on 2008-06-12
In a terminal (applications -> accessories)

```
sudo apt-get install ubuntu-restricted-extras
```

then click on the link in my signature called "media" enter the first 2 commands

then do

```
sudo apt-get install non-free-codecs
```

and

```
sudo apt-get install libdvdcss2
```

If you still want you could install vlc after doing these steps, but this will alow movie player (aka totem) to play everything (including embedded media files in firefox).

---

### Post by nnjond on 2008-06-12
Thanks for your interest. Where is My Signature?

---

### Post by sharks on 2008-06-12
go to ur User cp and edit ur signature

---

### Post by nnjond on 2008-06-12
Don't see media as an option under Edit Signature.

---

### Post by nnjond on 2008-06-12
Sorry I don't understand this direction. 

"then click on the link in my signature called "media" enter the first 2 commands"

Could you please explain more fully?

---

