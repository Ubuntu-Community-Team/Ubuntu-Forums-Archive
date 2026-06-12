---
title: "Reinstalling /etc/apche2"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by IceTeaGX on 2008-05-08
I've got a little problem with an apache server, on ubuntu 7.10 server
.
I've tried reinstalling the default /etc/apache2 configuration files, by uninstalling and reinstalling apache. This however did not replace the configuration files. So, in my infinite stupidity I removed the /etc/apache2 directory, expecting it to magically reappear with a new install of apache2.
They didn't...
So I'm a bit stuck now, and I'm not feeling like reinstalling the entire server, can anyone help me out?

---

### Post by Nxion on 2008-05-08
Ok. Try this. This should fix it.

First:

```
sudo apt-get remove apache2
```

Second:

```
sudo apt-get autoremove
```

Third:

```
sudo dpkg --purge apache2
```

Fourth:

```
sudo apt-get install apache2
```

Did it help?

---

### Post by IceTeaGX on 2008-05-08
Well, it placed some directory in there, but it is not complete.
It has a httpd.conf, but no apache2.conf, so the apache2 server still errors.

I don't have much time at the moment however, but I'll try later.
I'll probably end up reinstalling a full install anyway.

---

### Post by Nxion on 2008-05-08
> **IceTeaGX said:**
> Well, it placed some directory in there, but it is not complete.
It has a httpd.conf, but no apache2.conf, so the apache2 server still errors.

I don't have much time at the moment however, but I'll try later.
I'll probably end up reinstalling a full install anyway.


What is the error that you get? Can you post it here. We will get this fixed for you so you don't have to reload!! :)

I ran into the same issues when I was first playing with Apache.

---

