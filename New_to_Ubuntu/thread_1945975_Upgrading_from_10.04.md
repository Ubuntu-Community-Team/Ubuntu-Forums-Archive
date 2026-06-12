---
title: "Upgrading from 10.04"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by asmvday on 2012-03-24
I am currently at 10.04. I would like to upgrade. The catalyst for this choice is I want to go back to playing EVE online which seems to require wine 1.4 which *I think* requires ubuntu to be a higher version. Also, you know, it's a couple versions out of date,  and I would like to be current.

The problem is twofold:

1. On update, alsa / esound will be removed and pulse audio will be re-installed. The whole reason I tried to get rid of pulse audio in the first place was to for EVE in the first place. Is there any way to avoid this during a version upgrade?

2. nvidia-current will be uninstalled. I am way about this because last time I did something like this it was replaced with some default driver that did not work at all and I had to do a complete re-install.

Am I just going to get screwed if I let it update?

---

### Post by Bucky Ball on 2012-03-24
You could try looking rather than guessing. Wine 1.4 seems to have no problem running in 10.04 LTS:

[http://au.search.yahoo.com/search?p=wine%201.4%2010.04&fr2=sb-top&fr=altavista]("http://au.search.yahoo.com/search?p=wine%201.4%2010.04&fr2=sb-top&fr=altavista")

Incidentally, if you have a functioning system, why are you upgrading? If Wine 1.4 is the only reason I wouldn't bother. Just upgrade Wine. (Take note: if you are thinking of upgrading to 12.04 LTS I wouldn't recommend it. Unstable, still testing and not released for another month; and I would wait a couple of months after that. Expect breakages if you take that road.)

10.04 LTS is stable, the current long-term support release and is supported for another 13 months ... (with a one-click upgrade to 12.04 LTS when it's stable).

---

### Post by asmvday on 2012-03-24
> **Bucky Ball said:**
> You could try looking rather than guessing. Wine 1.4 seems to have no problem running in 10.04 LTS:

[http://au.search.yahoo.com/search?p=wine%201.4%2010.04&fr2=sb-top&fr=altavista]("http://au.search.yahoo.com/search?p=wine%201.4%2010.04&fr2=sb-top&fr=altavista")

Incidentally, if you have a functioning system, why are you upgrading? If Wine 1.4 is the only reason I wouldn't bother. Just upgrade Wine. (Take note: if you are thinking of upgrading to 12.04 LTS I wouldn't recommend it. Unstable, still testing and not released for another month; and I would wait a couple of months after that. Expect breakages if you take that road.)

10.04 LTS is stable, the current long-term support release and is supported for another 13 months ... (with a one-click upgrade to 12.04 LTS when it's stable).

I had guessed wine 1.4 could not be installed on 10.04 because it does not seem to work for me. I had followed the instructions to add the wine ppa and the end result was

```
Package wine1.4 is not available, but is referred to by another package.
```

I had assumed that meant I had to upgrade? Perhaps that was in error. If I can update wine independently then yes, that is what I would like to do. However, if I have to compile it, I've had a lot of bad experiences compiling wine in the past.

---

### Post by zombifier25 on 2012-03-24
> **asmvday said:**
> I had guessed wine 1.4 could not be installed on 10.04 because it does not seem to work for me. I had followed the instructions to add the wine ppa and the end result was

```
Package wine1.4 is not available, but is referred to by another package.
```I had assumed that meant I had to upgrade? Perhaps that was in error. If I can update wine independently then yes, that is what I would like to do. However, if I have to compile it, I've had a lot of bad experiences compiling wine in the past.

Try installing wine1.3 . It might be the real 1.4. Just look at the version number of that package.

---

### Post by asmvday on 2012-03-24
> **zombifier25 said:**
> Try installing wine1.3 . It might be the real 1.4. Just look at the version number of that package.

How do I check the version number of the package without installing it?

Edit: Nevermind, I decided to live dangerously and just install anyway and it turns out you were right! It is 1.4 I am still curious as to how to check the real version number though: that is not something I would have thought to do.

---

### Post by madjr on 2012-03-24
hmm, instead of upgrading i would test the new LTS in a new partition.

Lots has changed from 10.04

I like the new UI, but i had time to get used to it.

But if you want to have gnome-panel (classic), you will be able to:

[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/)

once you have things the way you like it, then just migrate.

---

### Post by zombifier25 on 2012-03-24
> **asmvday said:**
> How do I check the version number of the package without installing it?

Edit: Nevermind, I decided to live dangerously and just install anyway and it turns out you were right! It is 1.4 I am still curious as to how to check the real version number though: that is not something I would have thought to do.
In the commandline:
```
apt-cache show pkgname
```
or
```
apt-cache showpkg pkgname
```
The information provided are different, but they both contain the version number.

Or the GUI way, use Synaptic.

---

