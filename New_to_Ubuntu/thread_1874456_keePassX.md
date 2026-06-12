---
title: "keePassX"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by dunbrokin on 2011-11-03
Cannot get KeePassX to work with 11.10. Have un-installed and reinstalled...still no luck.The KeePassX site is of little use.

---

### Post by mike555 on 2011-11-03
Keepassx works on my Xubuntu 11.10 install.

---

### Post by alco75 on 2011-11-03
Yeah, works for me just fine on Xubuntu Oneiric too.

I installed it with: ```
sudo apt-get install keepassx
```

---

### Post by dave0109 on 2011-11-03
Like the others, I have it working in Xubuntu, and also in Ubuntu with Unity.

When you say it's not working, presumably nothing is showing up when you click or double click on the corresponding icon.

Have you tried running it from a command line to see if that yields any error information?

---

### Post by dunbrokin on 2011-11-03
yes tried running from command line....same thing?

I end up with an icon in the task bar...but when I click on it I just get lock workspace or quit.

I

---

### Post by kellemes on 2011-11-04
> **dunbrokin said:**
> yes tried running from command line....same thing?

I end up with an icon in the task bar...but when I click on it I just get lock workspace or quit.

I

Try deleting config-file..
~/.config/keepassx/config.ini

Edit: By the way.. you can also use KeePass2 if you wish.

---

### Post by dunbrokin on 2011-11-04
Thanks....that worked like a charm....

---

### Post by dave0109 on 2011-11-05
Can you use the thread tools to mark the topic as Solved.  It'll be useful for the archives.

---

