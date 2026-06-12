---
title: "Ubuntu 11.10, Thunderbird and no calender?"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by jermza on 2011-11-16
I did a fresh install of 11.10 and noticed that Thunderbird doesn't come with a calender (Lightning). This is pretty important, especially if you're using Thunderbird, and that nothing is available even in the Software Centre seems near-sighted.

Is there a way to install Lightning in 11.10?

---

### Post by Jacobonbuntu on 2011-11-16
I noticed too. you can download the lightning add on from the site of mozzilla :)
[https://addons.mozilla.org/nl/thunderbird/addon/lightning/](https://addons.mozilla.org/nl/thunderbird/addon/lightning/)

by the way, I always take my .thunderbird folder (in your personal folder) on to the next installation. That way you take all your email, but also all the add-ons with you, and they are updated automatically :)

---

### Post by jermza on 2011-11-16
> **Jacobonbuntu said:**
> I noticed too. you can download the lightning add on from the site of mozzilla :)
[https://addons.mozilla.org/nl/thunderbird/addon/lightning/](https://addons.mozilla.org/nl/thunderbird/addon/lightning/)

Not compatible with Thunderbird 7.01, which comes with 11.10.

So now what?

---

### Post by Jacobonbuntu on 2011-11-16
..That is indeed quite stupid!
I found a compatible version here
[https://addons.mozilla.org/nl/thunderbird/addon/lightning/versions/?page=1#version-1.0b7](https://addons.mozilla.org/nl/thunderbird/addon/lightning/versions/?page=1#version-1.0b7)
it is a Dutch site, but I think it is clear where the download link is .... (versie 1.0b7, it is the same version that works perfectly on my thunderbird 7 in Oneiric)

if not let me know, I can send you mine

---

### Post by Frogs Hair on 2011-11-16
I'm using lightning 1.0b7 with Tbird 7.0.1 on 11.10 , I read that it may not be compatible or has caused problems with Tbird 8 .

---

### Post by Jacobonbuntu on 2011-11-16
> **Frogs Hair said:**
> I'm using lightning 1.0b7 with Tbird 7.0.1 on 11.10 , I read that it may not be compatible or has caused problems with Tbird 8 .

I just read that too, we'll probably have to be careful with the next installation. Good to know that I cannot just transfer my .thunderbird directory next time :)
edit: it should update automatically when automatic updates of add-ons is switched on

---

### Post by surfer on 2011-11-16
try this:

```
$ sudo apt-get install xul-ext-lightning
```

---

### Post by BillyBoa on 2011-11-16
I don't use Thunderbird on Ubuntu but in Windows I installed Lightning through the addons, the same way you can do it for Firefox.

---

### Post by Jacobonbuntu on 2011-11-16
> **BillyBoa said:**
> I don't use Thunderbird on Ubuntu but in Windows I installed Lightning through the addons, the same way you can do it for Firefox.

oh yeah, forgot to tell OP, installation is easy, just choose add-ons, then push the grey button next to "search all add-ons", navigate to the downloaded xpi- file and open it...
it is a little different from how it was in older versions, but still quite easy

---

### Post by ajgreeny on 2011-11-16
I am using Thunderbird v8 on Lucid from the ppa repos for the stable versions of TB and FF.  For TB v8 there is a new stable v1.0 of lightning, no longer a beta version.

I don't know if it is possible to use those same ppa repos in Oneiric, but if so you should then get the opportunity to upgrade lightning to v1.0 when you first start TB new version.

See [https://addons.mozilla.org/en-US/thunderbird/addon/lightning/?src=hp-dl-featured](https://addons.mozilla.org/en-US/thunderbird/addon/lightning/?src=hp-dl-featured)

---

### Post by Jacobonbuntu on 2011-11-16
> **ajgreeny said:**
> I am using Thunderbird v8 on Lucid from the ppa repos for the stable versions of TB and FF.  For TB v8 there is a new stable v1.0 of lightning, no longer a beta version.

I don't know if it is possible to use those same ppa repos in Oneiric, but if so you should then get the opportunity to upgrade lightning to v1.0 when you first start TB new version.

See [https://addons.mozilla.org/en-US/thunderbird/addon/lightning/?src=hp-dl-featured](https://addons.mozilla.org/en-US/thunderbird/addon/lightning/?src=hp-dl-featured)

sounds good, where did you get the ppa for TB8?

---

### Post by pqwoerituytrueiwoq on 2011-11-16
```
sudo apt-add-repository ppa:mozillateam/thunderbird-stable
sudo apt-get update
sudo apt-get install thunderbird xul-ext-lightning
```easiest way to get lightening is via synaptic since you probably need the 64bit version

---

### Post by surfer on 2011-11-16
again: lighnting is in the repository! no need to add a ppa.

install it either in the shell:
```
sudo apt-get install xul-ext-lightning
```

or search in the software center for "lightning" click in "show .. technical items" and install xul-ext-lightning.

---

### Post by Jacobonbuntu on 2011-11-16
> **surfer said:**
> again: lighnting is in the repository! no need to add a ppa.

install it either in the shell:
```
sudo apt-get install xul-ext-lightning
```or search in the software center for "lightning" click in "show .. technical items" and install xul-ext-lightning.

I see, but I meant the ppa for TB8 :)

---

### Post by Jacobonbuntu on 2011-11-16
look here:
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=thunderbird](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=thunderbird)

TB8 is not yet available from the repos

---

### Post by surfer on 2011-11-16
oh, my mistake. sorry!

tb8 should hit the default repository in the next few days. and - i hope - lightning will get updated at the same time.

---

