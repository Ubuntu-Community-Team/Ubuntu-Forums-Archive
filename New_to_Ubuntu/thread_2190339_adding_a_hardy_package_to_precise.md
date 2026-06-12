---
title: "adding a hardy package to precise"
date: 2013-11-26
forum: New to Ubuntu
---

### Post by acodea on 2013-11-26
Could anyone give me a reply to this question: I would like to have Google gadgets added to my Precise(12.04) Operating System. Is this possible? There is only this ppa: ppa:googlegadgets/ppa located here: [https://launchpad.net/~googlegadgets/+archive/ppa](https://launchpad.net/~googlegadgets/+archive/ppa)

I would install them in synaptic:
```
deb http://ppa.launchpad.net/googlegadgets/ubuntu hardy main
deb-src http://ppa.launchpad.net/googlegadgets/ubuntu hardy main

```


If I use command-line, ```
sudo add-apt-repository ppa:googlegadgets/ppa
```,
I get a 404 error

---

### Post by deadflowr on 2013-11-26
Seeing as to hardy is dead now, the 404 is apt.

However, if you click on the package dropdown, below it will pop up a selection of files you might be able to download.
(Where it says source and the ppa name is)

Whether or not it will work on the newer versions of Ubuntu is unknown.

Buyer beware though.
Who knows how bad or messy the files are.

---

### Post by acodea on 2013-11-27
> **deadflowr said:**
> 
...if you click on the package dropdown, below it will pop up a selection of files you might be able to download.
(Where it says source and the ppa name is)

there was googlegadgets! It wouldn't install though, because of broken packages, though those weren't really broken unless trying to install from the hardy ppa.

> Buyer beware though.
Who knows how bad or messy the files are.

Indeed!

well researched, Deadflower

---

### Post by ian-weisser on 2013-11-27
Mixing packages from different Ubuntu releases is a great way to break your system.

Different releases of Ubuntu are compiled using different versions of vital libraries. The resulting binaries may be incompatible with the different-version libraries.

Don't do it...unless you have plenty of free time and want to learn a lot about troubleshooting and package management.

---

### Post by acodea on 2013-11-27
@ian-weisser:] > Different releases of Ubuntu are compiled using different versions of vital libraries. The resulting binaries may be incompatible with the different-version libraries. this was something I had to hear, as the other forum as a meta user I find this is a tongue in cheek question. Thanks for the heads up.

---

