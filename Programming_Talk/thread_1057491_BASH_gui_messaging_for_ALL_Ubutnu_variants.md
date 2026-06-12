---
title: "BASH gui messaging for ALL Ubutnu variants"
date: 2009-02-01
forum: Programming Talk
---

### Post by hammer v2 on 2009-02-01
Hi guys,
I need a way to add a GUI to a bash script that will work in Ubuntu, Kubuntu and xubuntu.

I've got zenity down...but that doesn't work in kubuntu.

Anything else I can use?

It doesn't have to be pretty, just clear and GUI (N-curses is not an option)

Thanks!

---

### Post by cabalas on 2009-02-01
have you looked at dialog/Xdialog, it might do what you want a quick google search brings up some tutorials/articles such as [http://www.linuxjournal.com/article/2807](http://www.linuxjournal.com/article/2807)

---

### Post by hammer v2 on 2009-02-01
That would work fine...but is dialog installed by default in xubuntu, ubuntu and kubuntu?

---

### Post by maximinus_uk on 2009-02-02
> **hammer v2 said:**
> That would work fine...but is dialog installed by default in xubuntu, ubuntu and kubuntu?

No. But xmessage is, and it does what you need.

```
xmessage -buttons yes,no Hello

```

*man xmessage* for the rest

---

### Post by hammer v2 on 2009-02-02
Perfect! Xmessage it is! Thanks so much Maximus!! :)

---

