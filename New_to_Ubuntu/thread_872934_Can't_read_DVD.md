---
title: "Can't read DVD"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by clipeuh on 2008-07-28
When I insert a dvd in my Acer Laptop and try to view it with VLC or Totem, it doesn't work. I tried with many different DVD. When I had Windows, my dvd drive worked perfectly. And last week I burned a CD with Ubuntu and it worked also.

---

### Post by halitech on 2008-07-28
have you installed the restricted codecs? will it read a data dvd?

---

### Post by clipeuh on 2008-07-28
I think I have installed the codecs.
I can access to the VIDEO_TS files and I see the DVD on my desktop.

---

### Post by halitech on 2008-07-28
ok, so you are able to read the dvd, doesn't mean the codecs are installed though

```
sudo apt-get install ubuntu-restricted-extras
```

more info is here:[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by eightmillion on 2008-07-28
Try installing libdvdcss2
> sudo apt-get install libdvdcss2

---

### Post by clipeuh on 2008-07-28
I installed the codecs and I still can't :(
Ubuntu said he could not find libdvdcss2 thing...

---

### Post by eightmillion on 2008-07-28
> **clipeuh said:**
> I installed the codecs and I still can't :(
Ubuntu said he could not find libdvdcss2 thing...

To install libdvdcss2, you have to enable the medibuntu repository. You can do that by entering 
> gksudo gedit /etc/apt/sources.list
and removing the #'s in front of these lines...
> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

Then save the file and run this command...
> 
sudo apt-get update && sudo apt-get install libdvdcss2

---

### Post by clipeuh on 2008-07-28
> **eightmillion said:**
> To install libdvdcss2, you have to enable the medibuntu repository. You can do that by entering 

and removing the #'s in front of these lines...

Then save the file and run this command...

Those lines are not in the file..

---

### Post by eightmillion on 2008-07-28
Add them...
```

## Medibuntu - Ubuntu 7.10 "hardy gibbon"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy free non-free

```

---

### Post by clipeuh on 2008-07-28
OMG ! It work ! Thank you so much ! :)

---

