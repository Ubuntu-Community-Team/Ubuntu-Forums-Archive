---
title: "Is there a way to do this with torrents?"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by DMzda on 2008-08-14
I am dual booting Ubuntu and Win XP, and I a using Transmission and uTorrent on each respectively.

Is there a way of continuing downloads started on one client with the other?

Thanks in advance.

---

### Post by tamoneya on 2008-08-14
yes.  If you have a half downloaded file point the new client at the directory as well as giving it the same torrent file.  The new torrent client should then check the integrity of files by performing checksums and then download the missing pieces.  You may have better luck though if you use the same client. For example azuerus is cross platform or using utorrent in wine.

---

### Post by linkmaster03 on 2008-08-14
You should be able to boot up the uTorrent installation from your Windows partition through WINE.

---

### Post by DMzda on 2008-08-14
Thanks for the quick replies. I will try to do that.

---

### Post by DMzda on 2008-08-15
I tried opening the same torrents and saving at the same location. Transmission found the pieces downloaded by uTorrent, but uTorrent didn't detect the segments downloaded from Transmission.

Any Help?

---

### Post by phantomjoker on 2008-08-15
it may sound silly, but are you sure your downloading and downloaded locations are the same? 

for instance you can have a folder for files while they are downloading in one place, and once completed the files move to another location? 

if you have separate locations, make sure you've selected your _downloading_ folder

---

### Post by DMzda on 2008-08-15
Thanks for the reply.

I removed the download in uTorrent, and added it again. It says that the same file already exists, and asks if I use it, start from scratch or abort. I used it, and it checked the files without error :)

Another question: Does this mean that I have to add the torrents in Transmission first?

[Edit]
Oh and is there a way to automatically forward the web UI to IPADDRESS:PORT/GUI/ when uTorrent is on, and to IPADDRESS:PORT/TRANSMISSION/GUI/ when Transmission is on?

---

### Post by DMzda on 2008-08-15
Any Help?

---

### Post by DMzda on 2008-08-17
Bump

---

### Post by DMzda on 2008-08-17
> **DMzda said:**
> Bump

Any Help?

---

