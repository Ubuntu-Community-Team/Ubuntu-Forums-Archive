---
title: "Choices"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by dgerwin11 on 2008-11-08
A wealth of options.  I have a computer with Ubuntu 8.04 (no Windows at all), which works fine except even with a ton of help from y'all, I can not get my HP All in One F4240 to work, but it does work on this Windows machine.  

I am going to upgrade to 8.10.  However, I am not sure if I should use Ubuntu, Kubuntu, or Xubuntu.  I use that machine mainly for email (gmail), spreadsheets (Google Docs) and general web surfing. I don't use it for music, videos, gaming etc.

Which OS is the most appropriate for my needs.  I am no tech hotshot, just an independent business man with relatively simple computing needs.

Thanks

---

### Post by tvtech on 2008-11-08
Ubuntu is the most thoroughly supported, Kubuntu although offically supported I have found it lacking.  xubuntu is for less intense hardware, want to save battery life go xubuntu.  otherwise stick with ubuntu, it's easy and if you really want you can install another windows manager ontop of it later.

---

### Post by Zzl1xndd on 2008-11-08
Kubuntu: I'm not a big KDE fan and even if I was Kubuntu is not the best KDE distro I have seen, so I wouldn't recommend it (if you like KDE I find Madriva does a good job with it).

Xubuntu: is very good on older hardware.

Ubuntu: Still the king IMHO

---

### Post by dgerwin11 on 2008-11-08
What is a Windows manager, and do I need it to get printer/scanner to work?

---

### Post by rbradt on 2008-11-08
Well, I do agree with tvtech about the derivatives of Ubuntu.  I personally use Xubuntu on my laptop that I use for school which I do mostly email, openoffice, and general web surfing (just as you described).  Xubuntu is made for less intense hardware like tvtech said, but if it's used on more advanced hardware, it's supposed to perform even better.  So, really it's all about preference.  For your uses, Xubuntu wouldn't be a bad choice because it is pretty minimal.

As far as your printer situation, have your installed any HP drivers?  I have a HP All-In-One F4100 which I share with all my other Ubuntu systems, and it works just fine.  So I'm just wondering what the main problem is.

-rbradt

---

### Post by Zzl1xndd on 2008-11-08
> **dgerwin11 said:**
> What is a Windows manager, and do I need it to get printer/scanner to work?

This might help with that question 

[http://en.wikipedia.org/wiki/Desktop_environment](http://en.wikipedia.org/wiki/Desktop_environment)

And no it wont help with your printer.

---

### Post by dgerwin11 on 2008-11-08
I too wish I knew what the main problem is.  I wnt thru all the hplip hoops and I could not get it to work.  It sais it printed 40+ jobs, but not one actually printed.  I think that the shop that built it for me may have botched something.  Unfortunately I haven't had time to takr it back for them to check it out.

---

### Post by kansasnoob on 2008-11-08
If you're used to Ubuntu stick with Ubuntu!

As far as your printer it should be supported:

[http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f4200_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f4200_series.html)

So first of all:

```
sudo apt-get install --reinstall hplip
```

And then:

```
sudo apt-get -f install
```

If you want the toolbox:

```
sudo apt-get install hplip-gui
```

---

