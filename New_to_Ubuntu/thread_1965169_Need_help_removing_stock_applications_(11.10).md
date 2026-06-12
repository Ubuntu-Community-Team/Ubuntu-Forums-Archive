---
title: "Need help removing stock applications (11.10)"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by xTheAngrySockx on 2012-04-25
Hi all, I'm TheAngrySock.
I've been using a virtual box copy of ubuntu for quite some time now so I decided I would try and dual boot it. So I TRIED. After about an hour of flipping my ***** I decided to just install over windows 7. Because I use my laptop at school, I need to make sure I am following the school network terms and conditions. One of them is not having a bit torrent program. Seeing as ubuntu comes with transmission, I need somebody to tell me how to remove it. Sorry if this issue has been posted before as I am using my phone which doesn't like the idea of having to search.

Thank you,
xTheAngrySockx

---

### Post by forrestcupp on 2012-04-25
```
sudo apt-get --purge remove transmission-gtk
```

You can also look for installed apps in the Software Center and choose to remove them from there.

---

### Post by xTheAngrySockx on 2012-04-25
Alright, thank you for your help :)

---

