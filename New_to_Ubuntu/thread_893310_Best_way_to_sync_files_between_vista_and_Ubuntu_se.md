---
title: "Best way to sync files between vista and Ubuntu server"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Gravidar on 2008-08-18
There's probably a simple tool for this which is why I'm posting here.

I'm editing web pages on a windows vista pc and looking for a simple way to sync these with /var/www (for the apache web server root) frequently during development. 

FTP was my first thought but it's a bit manual.

Would love it if there was an even easier sync method using ssh instead of ftp perhaps, is rsync suitable for a n00b, will it run between windows and Ubuntu?

should I be looking at a source control system instead?

Any suggestions for someone trying to ease the way from vista to Ubuntu?

Cheers

---

### Post by renzokuken on 2008-08-18
i'd say rsync was probably the best way to do it.....there are tons of guides on the net that should help, i think there is also a front-end for rsync but i cant remember the name right now.

---

### Post by hyper_ch on 2008-08-18
rsync wouldn't work well as windows doesn't keep the timestamp the way linux filesystems do. So it would end up, IMHO, syncing all files all the time.

---

