---
title: "[SOLVED] ubuntu-restricted-extras"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by cocopeanut on 2008-10-04
There were some programs that were easy to install by going to synaptic and installing " ubuntu-restricted-extras ".

However, I can't find it now. Did it get removed? I'm running ubuntu 8.04.

If so, how can I go about installing the programs that were included in that package?

Thanks!

-=-Oscar-=-

---

### Post by Ryadt on 2008-10-04
> **cocopeanut said:**
> There were some programs that were easy to install by going to synaptic and installing " ubuntu-restricted-extras ".

However, I can't find it now. Did it get removed? I'm running ubuntu 8.04.

If so, how can I go about installing the programs that were included in that package?

Thanks!

-=-Oscar-=-
Enable mutiverse in Software Sources. Then update. Retry the installation after that.

---

### Post by JoshuaRL on 2008-10-04
Hey Oscar.  So could you tell me what the output is when you try this from the terminal:
```

sudo apt-get install ubuntu-restricted-extras

```

---

### Post by porchrat on 2008-10-04
> **cocopeanut said:**
> There were some programs that were easy to install by going to synaptic and installing " ubuntu-restricted-extras ".

However, I can't find it now. Did it get removed? I'm running ubuntu 8.04.

If so, how can I go about installing the programs that were included in that package?

Thanks!

-=-Oscar-=-

I don't really understand...are you saying that you can't install it?...or that you have installed it and that now you can't find the programs that were installed when you installed ubuntu-restricted-extras?

What programs in particular are you looking for?  ubuntu-restricted-extras just installs support for various fonts, JREs, and audio formats.  To my knowledge it doesn't install anything you can just use as a program.

For example with it you can play mp3's...from your existing audio playing applications.  It doesn't install a new audio playing application.

---

### Post by Paqman on 2008-10-04
[Details of what's in ubuntu-restricted-extras](http://packages.ubuntu.com/hardy/ubuntu-restricted-extras).

That info is also available in Synaptic, btw.

---

### Post by cocopeanut on 2008-10-04
> **JoshuaRL said:**
> Hey Oscar.  So could you tell me what the output is when you try this from the terminal:
```

sudo apt-get install ubuntu-restricted-extras

```

Actually that worked. I just could not find it under Synaptic Package Manager. I thought I was able to search for it before, but this time when I search for it, no hits are available.

Thank you for the terminal command though. :)

-=-Oscar-=-

---

### Post by aysiu on 2008-10-04
For future reference, this is how you install it without using the terminal:
[http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree)

---

### Post by cocopeanut on 2008-10-04
> **aysiu said:**
> For future reference, this is how you install it without using the terminal:
[http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree)

Thank you, I guess I was looking in the wrong area. :)

-=-Oscar-=-

---

### Post by JoshuaRL on 2008-10-05
> **cocopeanut said:**
> Thank you, I guess I was looking in the wrong area. :)

-=-Oscar-=-

You also should be able to find it in Add/Remove Applications by searching for "restricted".

---

