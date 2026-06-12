---
title: "[SOLVED] Update medibuntu error..."
date: 2008-07-28
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-07-28
I get this error when i check for updates on hardy...

```
Failed to fetch http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz  404 Not Found [IP: 87.98.249.30 80]
Failed to fetch http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz  404 Not Found [IP: 87.98.249.30 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```

So whats all this mean? lol


Thanks in advance

---

### Post by Elfy on 2008-07-28
I thinks it's down again - it was like it earlier today and alos last week I think.

---

### Post by billgoldberg on 2008-07-28
Their servers were/are down.

When I tried updating this morning, they were down.

A while ago they were back up.

It seems as they are down again.

--

Does anyone what's going on with them?

--

It would be a small disaster for most if they were to disappear.

---

### Post by kamitsukai on 2008-07-28
Oh right thankyou, just checking that i hadn't broken my install...again:lolflag:

**Edit** @ forestpixie

> You installed everything that was in synaptic
yes.. lol ... i didn't know what i was doing
just out of interest how long did it take ?
Euh about 10 hours

Did someone really do that?:shock:

---

### Post by Elfy on 2008-07-28
No - unless you broke medibuntu for the rest of us :)

> Does anyone what's going on with them?I haven't heard anything lately, but I have a vague recollection of a thread in omgpp- but of course you can't search there ;)

I agree it would cause a bit of a problem if it went, but there isn't any - 'we're off' type of notice on the launchapd page that I could see.

---

### Post by gunashekar on 2008-07-28
It works now.. good

---

### Post by kamitsukai on 2008-07-28
> **gunashekar said:**
> It works now.. good

Yep:D

---

### Post by Elfy on 2008-07-28
Good - kamitsukai - someone close to home then - where on the island do you claim to be from then

---

### Post by WRDN on 2008-07-28
I've had that message multiple times, and I solved it immediately by using the commands:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

This is used to add the GPG key for the repo(s), and solved the problem.

---

### Post by chronniff on 2008-07-28
I still can't get it to update, although it pings fine....any ideas?

---

### Post by kamitsukai on 2008-07-28
> **forestpixie said:**
> Good - kamitsukai - someone close to home then - where on the island do you claim to be from then

Well born in Reading but i live in Shanklin now :D (small coastal town on the isle of wight)

---

### Post by Elfy on 2008-07-28
> (small coastal town on the isle of wight)Many a beer I've consumed in pubs there over the years - I'm in Lymington. Nice to know there are people nearby :)

---

### Post by kamitsukai on 2008-07-28
Makes a change to chat with someone local :P

---

### Post by w0ng on 2008-07-28
Is medibuntu still down guys? i still can't update...

---

### Post by Elfy on 2008-07-28
Yep - looks like it's down again.

---

### Post by lone.ranger69 on 2008-07-28
its down again..unless I am doing something wrong then..
:confused:

---

### Post by lone.ranger69 on 2008-07-28
its up again!..

wow!but real slow..:neutral:

---

### Post by Elfy on 2008-07-28
> **kamitsukai said:**
> **Edit** @ forestpixie
Did someone really do that?:shock:

Yes :lol:

---

### Post by darksoul7 on 2008-07-28
Still down for me. Here's what I get - 

GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz)  404 Not Found [IP: 87.98.249.30 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz)  404 Not Found [IP: 87.98.249.30 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by kamitsukai on 2008-08-14
is medibuntu down again?

**edit**
never mind it's working now...(after 10mins of trying)

---

### Post by Elfy on 2008-08-14
Rather than being on a roll I think that medibuntu is in fact on a bounce and perhasp should be renamed tiggerbuntu lol

---

