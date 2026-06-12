---
title: "Puppy Linux perofrmance?"
date: 2007-06-01
forum: Other OS Talk
---

### Post by elfstone214 on 2007-06-01
Hey all,

I am currently using ubunbtu but I just recently tried puppy linux and was EXTREMELY impressed with it's speed. However I still prefer ubuntu because it is easier for me to manage it and I also prefer the synaptic package manager. However I was wondering if there was a way to make ubuntu as fast (or close) as puppy linux (ie. loading programs). I suppose puppy linux has most if not all loaded to RAM memory already, I have quite a bit of RAM, is there a way to automatically load programs that are often used straight to RAM on bootup like Vista does I believe?

Thanks!

P.S. I wasn't too sure in which forum to post this, sorry.

---

### Post by pbw on 2007-06-01
preload will keep commonly used apps in ram for you. ```
sudo apt-get install preload
``` 
No configuration needed.

You can also create a ramdisk.

--pbw

---

### Post by elfstone214 on 2007-06-01
cool thanks!

---

### Post by meng on 2007-06-01
GNOME is somewhat heavier than other DEs, so that may explain the speed difference to an extent.

---

### Post by smoker on 2007-06-01
hi, puppy loads completely to ram, but the full distro is only around 80mb approx, before customising, so this can be done quite easily. i would imagine in a few years time, with ram size increasing, the price falling, and motherboards able to utilise more, then eventually a distro like ubuntu should be able to do the same.

it would be good to know how much ram you would need to do this, and if it can be done easily, anybody?

---

### Post by elfstone214 on 2007-06-01
> **smoker said:**
> hi, puppy loads completely to ram, but the full distro is only around 80mb approx, before customising, so this can be done quite easily. i would imagine in a few years time, with ram size increasing, the price falling, and motherboards able to utilise more, then eventually a distro like ubuntu should be able to do the same.

it would be good to know how much ram you would need to do this, and if it can be done easily, anybody?

I agree with the way RAM prices are falling I don't think it will be long for that to be possible 2GB DDR2 now is dirt cheap and even 4GB are coming down in price. ;)

---

### Post by RAV TUX on 2007-06-01
> **elfstone214 said:**
> Hey all,

I am currently using ubunbtu but I just recently tried puppy linux and was EXTREMELY impressed with it's speed. However I still prefer ubuntu because it is easier for me to manage it and I also prefer the synaptic package manager. However I was wondering if there was a way to make ubuntu as fast (or close) as puppy linux (ie. loading programs). I suppose puppy linux has most if not all loaded to RAM memory already, I have quite a bit of RAM, is there a way to automatically load programs that are often used straight to RAM on bootup like Vista does I believe?

Thanks!

P.S. I wasn't too sure in which forum to post this, sorry.

Last time I used Puppy it included the Synaptic Package manager, unless my memory is mistaken?

---

### Post by justin whitaker on 2007-06-01
> **RAV TUX said:**
> Last time I used Puppy it included the Synaptic Package manager, unless my memory is mistaken?

Not anymore. DSL still does, but Puppy switched to a T2 base. 

[http://www.t2-project.org/](http://www.t2-project.org/)

It's source based, very flexible, and CPU optimized. 

What Puppy does instead of Synaptic is PupGet, which allows you to download application packages and install them on the fly.

---

### Post by nonewmsgs on 2007-06-02
puppy runs with 128mb of ram.  i use it on my old p2 256mb 266mhz laptop.  it does the job and the initial program selection is great.  on that computer though i do use opera as my browser since it seems to get a slightly higher perfomance.

---

### Post by Dark-Ace on 2007-06-03
Yeah i actually use puppy on my flashdrive ,it really is fast.i like it but i wish it had a BootSkin.

---

