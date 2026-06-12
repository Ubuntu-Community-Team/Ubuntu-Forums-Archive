---
title: "Having the Partial Update problem again"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by deadlySniper on 2008-07-31
This time give the reason, not to mention that linux is being slower than usual from the last update.

---

### Post by daimaru on 2008-07-31
> **deadlySniper said:**
> This time give the reason, not to mention that linux is being slower than usual from the last update.
great to know , but I have not followed your posts so I do not know what your talking about. If by any chance you were not able to download some updates (failed) during update then you should change the server by going to "System -> Administration -> Software Sources " under the Ubuntu Software tab there's a drop down menu that reads: Download From: --> just select a different server since the one you are using might be down. That worked for me every time I had problems with updates. If this is absolutely not what you were  asking for, --- please include your question in your post :) thx

---

### Post by deadlySniper on 2008-08-02
I have switched to different servers and I still get

Not all updates can be installed
Run a partial upgrade, to install as many updates as possible

This can be casue by
A previous upgrade which didnt complete
Unofficial software [ackages not provided by Ubuntu
Normal changes of a pre-release version of Ubuntu


I havent installed any unofficial software on Xubuntu. The othere thing is I dont plan on upgrading unless that is what will fix this issue.

P.S. I have noticed this happens when virtual box is installed.

---

### Post by sayakb on 2008-08-02
You might have all update sources enabled. Goto software sources and **uncheck** backports and proposed updates (or just proposed updates)

---

### Post by deadlySniper on 2008-08-02
it was the backports that was causeing the partial update. The only problem with it is that GIMP cant get updated without the backport

---

### Post by chuckyp on 2008-08-02
Thats not necessarily a bad thing that you can't get all the updates. It may be that they are just upping them to the server as you are trying to upgrade. I would just wait a few minutes and try again.

---

### Post by deadlySniper on 2008-08-02
I am sticking with 7.10 Xubuntu. Unless you mean upgrading the other software other than the OS

---

