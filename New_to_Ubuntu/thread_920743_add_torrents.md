---
title: "add torrents ?"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by eric489 on 2008-09-15
Hi all !

Since i've switched to kubuntu, i got ktorrentz.
But I allready had deluge from gnome.

Some torrents are still running on deluge ( only uploads ), and some i've added to ktorrent.

I'd like to "sum them up", or to make all torrentz run under one program.
Is it possible ?
Can i take the upload running under deluge and add them to ktorrent, so they can continie uploading ? If yes how ?

Many thanks in advance.

---

### Post by Harisz750 on 2008-09-15
just download again the torrent file from the site... tell ktorrent to open it and choose to save data in the same folder your torrent data is.. for example if it is a movie... see where this movie is stored... and choose to be stored again in the same folder.. ktorrent will make a check, and then it will start seeding again

---

### Post by eric489 on 2008-09-15
> **Harisz750 said:**
> just download again the torrent file from the site... tell ktorrent to open it and choose to save data in the same folder your torrent data is.. for example if it is a movie... see where this movie is stored... and choose to be stored again in the same folder.. ktorrent will make a check, and then it will start seeding again

Thanks.
Does it work for any type of file ?

---

### Post by Harisz750 on 2008-09-15
yes

---

### Post by lovinglinux on 2008-09-15
You don't have to download all .torrent files again. All you need is to know where Deluge saved the .torrent files and add them to ktorrent. 

If you still have the ability to open Deluge, open it and go to [Edit > Preferences] and look the directory specified in the "Store all torrent files in". Open that directory and copy the .torrent files somewhere else and open them in ktorrent and follow the procedure explained by Harisz750.

---

### Post by kostkon on 2008-09-15
> **lovinglinux said:**
> You don't have to download all .torrent files again. All you need is to know where Deluge saved the .torrent files and add them to ktorrent. 

If you still have the ability to open Deluge, open it and go to [Edit > Preferences] and look the directory specified in the "Store all torrent files in". Open that directory and copy the .torrent files somewhere else and open them in ktorrent and follow the procedure explained by Harisz750.
Indeed. *Deluge* saves the torrent files in
```
~/.config/deluge/torrentfiles
```

---

### Post by lovinglinux on 2008-09-15
> **kostkon said:**
> Indeed. *Deluge* saves the torrent files in
```
~/.config/deluge/torrentfiles
```

By default, if he didn't choose another place.

---

### Post by kostkon on 2008-09-15
> **lovinglinux said:**
> By default, if he didn't choose another place.
Yes. I forgot to specify this.

---

### Post by Harisz750 on 2008-09-15
you are right...   i just use vuze and don't save torrents..  hehehe

---

