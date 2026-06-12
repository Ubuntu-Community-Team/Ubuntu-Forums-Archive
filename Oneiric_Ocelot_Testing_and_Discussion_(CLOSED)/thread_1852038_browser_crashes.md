---
title: "browser crashes"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ioca100 on 2011-09-29
[ ]("http://www.google.com/search?hl=pt-BR&client=ubuntu&hs=tG0&channel=fs&sa=X&ei=rqOETpzsBKrv0gG8oPTcDw&ved=0CBUQBSgA&q=After+update,+Firefox+doesn%27t+work+,+it+crashes+,+only+works+like+root.&spell=1")

After updates Firefox doesn't work, it crashes, only works like root.

---

### Post by cariboo on 2011-09-29
Why link your post to a google search? Have you tried creating a new firefox profile? What is the output in a terminal when you start firefox from it?

---

### Post by ioca100 on 2011-09-29
/usr/lib/firefox-7.0.1/firefox: symbol lookup error: /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: undefined symbol: gdk_error_trap_pop_ignored

The same mistake happens with banshee;

(Banshee:2160): libsoup-CRITICAL **: soup_message_headers_append: assertion `strpbrk (value, "\r\n") == NULL' failed
banshee: symbol lookup error: /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: undefined symbol: gdk_error_trap_pop_ignored

---

### Post by VinDSL on 2011-09-29
It seems that the latest libcanberra upgrades are to blame.

I just booted, did an update, and now breakage abounds - all pointing to libcanberra.

Banshee quit working.  Dittos for Chromium, Firefox, and the list goes on...

Luckily, the libcanberra upgrades didn't affect Opera-Next.

I saw an error message, during the (apt-get) updates, saying one of the libcanberra files or folders didn't exist.

I'll go try Synaptic and see if it corrects the problem (broken packages, etc).

EDIT

No dice!  Synaptic is broken too.

EDIT

No joy with aptitude, either.

Guess I'll wait for further updates...

---

### Post by FerroPower on 2011-09-29
I can open Synaptic Package Manager how to select older version of libcanberra

---

### Post by VinDSL on 2011-09-29
> **FerroPower said:**
> I can open Synaptic Package Manager how to select older version of libcanberra
If it was me - if I had the time...

I would go look up the previous version on Launchpad:  [https://launchpad.net/ubuntu/+source/libcanberra](https://launchpad.net/ubuntu/+source/libcanberra)

And, install the older .deb file from CLI...  ;)

Unfortunately, I'll have to wait until later - and by then, they'll probably issue a fix.

So, only time will tell the proper course.

---

### Post by PaulW2U on 2011-09-29
Bug [https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/862553](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/862553) already being discussed in thread [http://ubuntuforums.org/showthread.php?t=1852054](http://ubuntuforums.org/showthread.php?t=1852054) and affecting not only Firefox.

---

