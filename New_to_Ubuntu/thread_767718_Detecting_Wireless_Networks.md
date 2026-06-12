---
title: "Detecting Wireless Networks"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Reactor5 on 2008-04-25
I've got my wireless card set up and configured but I can't figure out how to detect wireless networks on it.  What program should I use?

---

### Post by Monicker on 2008-04-25
If your card is working properly you can do it from a terminal:

sudo iwlist eth1 scan , for example.


If you are looking for a bit more detail and features, look into Kismet.  Its in the repos.

---

### Post by stalkier on 2008-04-25
> **Reactor5 said:**
> I've got my wireless card set up and configured but I can't figure out how to detect wireless networks on it.  What program should I use?

If you have the drivers enabled etc you should be able to detect any wireless networks in your area automatically. Mine wouldn't show up and I couldn't figure out how. Then I though hmm let me unplug it and plug it back in (my router) and poof there it was. :D You might try that if it is not working.

---

### Post by Miljet on 2008-04-25
Stalkier is right, it should automatically detect available networks. Most wireless problems are caused by people attempting to "configure" their cards (myself included.)

This is an old post but it is priceless:
[http://ubuntuforums.org/showthread.php?t=603154&highlight=gilf](http://ubuntuforums.org/showthread.php?t=603154&highlight=gilf)

---

### Post by Reactor5 on 2008-05-09
Thanks everyone, I was just not looking in the right place.  I was trying to use a program that was already open.

---

