---
title: "[SOLVED] Mounting to /"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by rockstarrem on 2008-07-21
Hello guys,

I've seen around the forums people have a /home partition amongst others. I have 1 partition mounted to "/" and was wondering if I'm all set or if I'm losing anything by not having that "/home" partition. Sorry for the noob question, I'm learning slowly!

---

### Post by jordanmthomas on 2008-07-21
The advantage to having a separate partition mounted to /home is this:  say you want to reinstall Ubuntu.  The way you've got it set up, it would require you to backup all your settings and files (in /home/yourname) to some other partition, reinstall, and then put them back in place.

If you were to have /home as another partition, you could reinstall and have your settings back immediately upon reinstallation.  Also, if you boot many distros at once, you can share your home directory between them and always have the same setup.

Having a separate /home is nice, but not necessary.  I don't do it this way.

---

### Post by rockstarrem on 2008-07-21
Ah, I see! Is it easy to mount your old /home and overwrite it etc? Is there instructions somewhere?

Thanks!

---

### Post by tamoneya on 2008-07-21
no need to make a separate home partition except when installing.  No real need to do it once you are already installed.  I think in addition to what was already mentioned above it can also help during boot times since it is quicker to mount smaller partitions.  Therefore mounting / is quicker since the partition is smaller.

---

### Post by rockstarrem on 2008-07-21
Alright, thanks! I hope this helps someone else out too, I'll make another topic for my next question. You learn something new every hour :P.

---

### Post by jordanmthomas on 2008-07-21
> **rockstarrem said:**
> Ah, I see! Is it easy to mount your old /home and overwrite it etc? Is there instructions somewhere?

Thanks!

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

This is a semi-old guide, but should still work.
Just a few differences, like when you boot off the Ubuntu liveCD, you don't have to install gparted or ntfsprogs and your current install may already be mounted for you.

Be sure you understand what you're doing before you do it, of course.

---

### Post by jordanmthomas on 2008-07-21
> **tamoneya said:**
> it is quicker to mount smaller partitions.  
I did not know this.  Any proof or links explaining why perhaps?

---

### Post by tamoneya on 2008-07-21
I followed this guide by K.Mandla: [http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/](http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/)

It was part way through that is said smaller partitions mount quicker.

---

