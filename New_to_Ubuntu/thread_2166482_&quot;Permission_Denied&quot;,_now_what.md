---
title: "&quot;Permission Denied&quot;, now what?"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by nosto53 on 2013-08-09
My 2008 desktop:
Athlon64 X2 3.0GHz, 4GB ram, 36GB Raptor(OS), 250GB Barracuda(data)
was on Hardy Heron for 6 years, now in 12.04LTS.

The Raptor HD (/dev/sda1) and OS is fine; can put a old 2GB Flash drive on and put data on (docs,music....) with easy,
but the Barracuda HD can't.  Can only get "Permission Denied" for any data put there. Did 'fsck' and came up clean.

The partition (in GParted) has one partition (/dev/sdb1), a extended (/dev/sdb3) and a 8GB swap (/dev/sdb5).  Mount point
is at "/media/Server250" (one day I will buy a new desktop and use the old one as a server, maybe..) and "LABEL" is 'Server250'.

Do I have something wrong with my mount point and label being the same name? Or should I format and start over again?
RickO

---

### Post by carl4926 on 2013-08-09
Let's say your username is: kevin

Open a terminal and cd to the location /media

Now try this

```
sudo chown -R kevin [COLOR=#000000]Server250[/COLOR]
```

---

### Post by nosto53 on 2013-08-10
Carl4926,
Thank you!
sudo chown -R myname Server250  ----  did not work..... But.....
sudo chown -R myname:myname /media/Server250 ........ DID!
(Of course you get a free bean for that.  !!)
RickO

---

### Post by carl4926 on 2013-08-10
> **nosto53 said:**
> Carl4926,Thank you!sudo chown -R myname Server250  ----  did not work..... But.....sudo chown -R myname:myname /media/Server250 ........ DID!(Of course you get a free bean for that.  !!)RickORight - OK Good

---

