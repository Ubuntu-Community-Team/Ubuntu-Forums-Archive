---
title: "Help With Totem"
date: 2006-01-21
forum: Programming Talk
---

### Post by newtonfn on 2006-01-21
Hi..

I was watching some movies last night using totem and i wanted to see and play around with Totem source code just to convince myself that I will not be able to fix one or two things that's bothers me. (I am a windows pseudo-programmer.. have a lot to learn about Linux / X.org / C)

I did a "apt-get source totem" to download totem source code, and then tried a ./configure

But, while checking my system, fails saying that could not find something related with gstreamer (I Want gstreamer.. not xine.. but i don't really know the difference)

The last line says:
configure: error: you need the GStreamer or the xine-lib development packages installed

I don't know how to get that, I searched the repository but didn't find something related (or maybe I don't know how to search in the repo nor what I am looking for.)

I will appreciate any kind of help.
Lot's of thanks.

---

### Post by joselin on 2006-01-21
Hi,

You need libxine-dev or libgstreamer0.8-dev. You can download it with apt.

Regards.

---

### Post by newtonfn on 2006-01-21
Thanks Joselin but..

I do have libgstreamer0.8-dev and libgstreamer-gconf0.8-dev installed through apt-get, but I still get the same error..

Anyway thanks for the fast reply.

---

### Post by newtonfn on 2006-01-21
Solved:

Just downloaded latest Totem sources from gnome site and when I executed ./configure told me a lots of packages I was missing.

Installed those packages and everything went right since then. Even with Totem 1.2 with is the one apt-get source get me.

Sorry about my english.

---

