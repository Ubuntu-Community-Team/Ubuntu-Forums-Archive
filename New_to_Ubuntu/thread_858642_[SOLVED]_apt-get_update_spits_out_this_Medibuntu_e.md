---
title: "[SOLVED] apt-get update spits out this Medibuntu error, been at it all day."
date: 2008-07-13
forum: New to Ubuntu
---

### Post by philinux on 2008-07-13
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

run apt-get update to fix it. 

Google says wait. Well no fix so far.

---

### Post by Kilz on 2008-07-13
> **philinux said:**
> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

run apt-get update to fix it. 

Google says wait. Well no fix so far.

Medibuntu is not part of Ubuntu. You may want to contact them to let them know of the issue.

---

### Post by Rocket2DMn on 2008-07-13
I can run apt-get update and apt-get upgrade just fine.  I'm actually getting some updated packages from the Medibuntu repos as I type this.

---

### Post by Bodsda on 2008-07-13
Im not sure if this will solve it but it may be worth a try.

[http://ubuntuforums.org/showthread.php?t=764906]("http://ubuntuforums.org/showthread.php?t=764906")

look at the second post

Hope this helps

Bodsda

---

### Post by philinux on 2008-07-13
Well if waiting or that did it I'm not sure but sorted anyway.

This was a fresh install too.

---

### Post by Rocket2DMn on 2008-07-13
Funny, I did the updates, edited something in Software Sources, and now  I'm getting
```
Failed to fetch http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz  510 Not Extended [IP: 87.98.242.10 80]
Failed to fetch http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz  510 Not Extended [IP: 87.98.242.10 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```
But it's still ok when I run apt-get update

After removing the Medibuntu entries from the list and re-adding them(see [uhelp]community/Medibuntu[/uhelp]), I still get the error.

---

### Post by inselaffe on 2008-07-14
I've been getting this intermittently for a week or so now. As far as I understand it, a 5xx HTTP error indicates a server-side error, so there's nothing to do other than hope they fix their server.

---

### Post by philinux on 2008-07-14
ARRRGGGHHH, it's back again this morning. :confused:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Their site seems to be down.

---

### Post by zivley on 2008-07-14
Yep, their site seems to be down, I don't even get a proper resolving to their domain "www.medibuntu.org"
Darn!

---

### Post by philinux on 2008-07-14
Looks like they've been upgrading their site.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Looks good.

---

### Post by Rocket2DMn on 2008-07-14
Looks pretty slick.

---

