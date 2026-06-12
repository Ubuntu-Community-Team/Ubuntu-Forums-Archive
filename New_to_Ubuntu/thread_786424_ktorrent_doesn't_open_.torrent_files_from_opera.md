---
title: "ktorrent doesn't open .torrent files from opera"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by netimen on 2008-05-08
I have configured my opera that it opens .torrent files with ktorrent. But ktorrent says 
> An error occurred while loading the torrent. The torrent is probably corrupt or is not a torrent file.
/home/netimen/.opera/cache4/temporary_download/[torrents.ru].567360.torrent

But if I download the file, save it and then open with ktorrent -all is OK

---

### Post by hyper_ch on 2008-05-08
seems a conflict between the Opera cache and ktorrent opening it

---

### Post by netimen on 2008-05-08
> **hyper_ch said:**
> seems a conflict between the Opera cache and ktorrent opening it

but what can I do with it?

---

### Post by hyper_ch on 2008-05-08
setup a watchfolder for ktorrent and save the .torrent files into that folder...

---

### Post by Dani Filth on 2008-05-08
I believe Opera has its own torrent program, so by default, if you download the .torrent file with Opera, it will automatically use its program.
So, to avoid this, either :
1. Right click on the link and choose "Save target as" to somewhere then open it with KTorrent.
2. Use other browser (e.g FF)

I don't think this is a really annoying matter, ain't it?

---

### Post by netimen on 2008-05-08
> **Dani Filth said:**
> I believe Opera has its own torrent program, so by default, if you download the .torrent file with Opera, it will automatically use its program.
So, to avoid this, either :
1. Right click on the link and choose "Save target as" to somewhere then open it with KTorrent.
2. Use other browser (e.g FF)

I don't think this is a really annoying matter, ain't it?

No I configured opera to use ktorrent instead of it's own client.
of course it's not very annoying, but to open them directly is more convenient

---

### Post by hyper_ch on 2008-05-08
why not set a watchfolder in ktorrent and set opera to automatically download/save .torrent files to that watchfolder?

---

### Post by netimen on 2008-05-08
> **hyper_ch said:**
> why not set a watchfolder in ktorrent and set opera to automatically download/save .torrent files to that watchfolder?

yeah, the idea is clear but how to add the watch folder?

---

### Post by hyper_ch on 2008-05-08
It's been a long time since I used ktorrent but I'm pretty sure you can set a watch folder there (too). Otherwise I'd tend to think it's pretty deprecated.

---

### Post by netimen on 2008-05-08
> **hyper_ch said:**
> why not set a watchfolder in ktorrent and set opera to automatically download/save .torrent files to that watchfolder?
yeah this helped, thanks!

---

