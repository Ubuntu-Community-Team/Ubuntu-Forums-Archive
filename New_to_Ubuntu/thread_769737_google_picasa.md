---
title: "google picasa"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by bmann11 on 2008-04-26
does anyone know anything about picasa for linux.  I used to use it with windows and loved it.

If it's equally good for ubuntu, does someone have download/install directions.  Thanks, Bmann

---

### Post by hackle577 on 2008-04-26
Google is your friend: [http://picasa.google.com/linux/download.html](http://picasa.google.com/linux/download.html)

---

### Post by frup on 2008-04-26
There is a linux version which uses Wine internally. I tried it way back when it first was released and it seemed acceptable, but why don't you give f-spot a try. I discovered how awesome it was yesterday. I think I prefer it over picasa well and truly.

---

### Post by Joeb454 on 2008-04-26
I believe it runs perfectly well in Wine. So search Add/Remove or Synaptic for Wine :)

You need all repositories enabled for this (System>Administration>Software Sources) **except** Source Code & CD Media.

Then you go to the Picasa site, and download and install it that way :) I believe that is the official Google recommendation of getting it on Linux

_EDIT:_ My post seems pretty pointless now - I haven't used Picasa in a long time :p

---

### Post by miwaypet on 2008-04-26
First off, google has a version of Picasa that works exactly like MS. 

Start here:[http://www.google.com/linuxrepositories/apt.html]("http://www.google.com/linuxrepositories/apt.html")

Copy the key to a file, say documents. Ignore the
 other instructions on the page. You just want the key.

Follow these steps:[tp://www.google.com/linuxrepositories/ubuntu704.html]("tp://www.google.com/linuxrepositories/ubuntu704.html")

Don't worry, they will work for you in Hardy. After refreshing open terminal and type;

sudo apt-get update; sudo apt-get upgrade

When it is through type:

sudo apt-get install picasa

Thats it. Hope it helps. Remember, just follow the link to the signing key in the first link above. The other instructions are useful for distro's without ubuntu's software sources utility.

---

### Post by Monicker on 2008-04-26
> **Joeb454 said:**
> I believe it runs perfectly well in Wine. So search Add/Remove or Synaptic for Wine :)

You need all repositories enabled for this (System>Administration>Software Sources) **except** Source Code & CD Media.

Then you go to the Picasa site, and download and install it that way :) I believe that is the official Google recommendation of getting it on Linux

_EDIT:_ My post seems pretty pointless now - I haven't used Picasa in a long time :p

Actually, Google Picasa for Linux has its own self contained version of wine which it uses when it installs.

---

### Post by Joeb454 on 2008-04-26
Oh so I was sort of right :lolflag:

---

