---
title: "problems with kernel compile"
date: 2005-09-16
forum: Programming Talk
---

### Post by neighborlee on 2005-09-16
hi..

memtest shows badram so I had to get source for default ubuntu kernel and apply badram patch and thats done..issuing sudo make and I'm getting:

drivers/media/dvb/frontends/dib3000mb_priv.h:354:2: invalid preprocessing directive #defind ????

which is easy to fix and I just did, but that should not be happening considering that Im using the : config-2.6.10-5-386 from /boot, from having copied it to /usr/src/linux-source-2.6.10 and renamed it to config ( and .config in case it needed the . as I wasn't sure since I have not done this in ages )

Isn't this the config that is running the default installed ubuntu kernel ? ( hence it should compile cleanly and just boot or so I was told in IRC )

Something is wrong here because when I checked 'file systems' section , EXT3 was set to "M" and thats not going to work because / needs to be set as Y to work.

anyone know whats up here ?

thx
nl

---

