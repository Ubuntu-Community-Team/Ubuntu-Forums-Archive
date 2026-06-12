---
title: "Help installing package"
date: 2015-07-23
forum: New to Ubuntu
---

### Post by NotionCommotion on 2015-07-23
Hi all!  Fairly new with ubuntu.  Know a little centos/redhat, but just enough to be dangerous.


My daughter wanted her own laptop, so took an old laptop and put utuntu on it.  Working great!  Until now....

She wants [https://krita.org/download/krita-desktop/](https://krita.org/download/krita-desktop/).  Did the following:

```
sudo add-apt-repository ppa:kubuntu-ppa/backports 
sudo apt-get update 
sudo apt-get install krita

```

but get the following error when launching the application:

> Essential application components could not be fount.
This might be an installation issue.
Try restarting, running kbuildsyoca4.exe or reinstalling.

exe file?  Tell me ubuntu doesn't use those!  Recommendations?

---

### Post by MGrowl on 2015-07-23
I'm not sure about this, I just read Krita's website to know what it is. Seems Krita uses KDE environment, Ubuntu uses Unity by default if I'm not mistaken

---

### Post by NotionCommotion on 2015-07-23
Thanks MGrowl,

Meaning I have to tell her Daddy can't help :(

Pretty sure I have a stock ubuntu install, and likely don't want to change.

---

### Post by Bucky Ball on 2015-07-23
Krita? Open Software Centre and install it. :)

Yes, it is KDE based and will drag in a million and one KDE related packages and dependencies with it.

_ALWAYS_ check the official repos (Software Centre) before dragging third-party .debs, PPAs and repos in. That can cause a fair degree of chaos if you are not sure what you are doing. Third-party software is untrusted and not officially tested on Ubuntu.

For a start I would get rid of the unrequired Krita PPA you've installed. Not needed and could cause problems when attempting to install the official version from the repos.

If you want an image manipulation app, install Gimp from Software Centre, if it is not already in Ubuntu as a default (I don't use the default Ubuntu desktop so unsure).

---

### Post by v3.xx on 2015-07-23
Good news and bad..

The good is no extra kde apps will be loaded.

The bad; krita is a 400M install.

[ATTACH=CONFIG]263332[/ATTACH]

---

### Post by MGrowl on 2015-07-23
@Ronald_hume. I suggest creating a new thread for the problems you're having so the community can pitch in and find you a solution.

---

### Post by Bucky Ball on 2015-07-23
> **v3.xx said:**
> 

The bad; krita is a 400M install.

[ATTACH=CONFIG]263332[/ATTACH]

Yep, the majority KDE dependencies. :)

---

### Post by stalkingwolf on 2015-07-23
perhaps  install kubuntu instead?  it uses kde.

---

### Post by mystics on 2015-07-23
> **MGrowl said:**
> I'm not sure about this, I just read Krita's website to know what it is. Seems Krita uses KDE environment, Ubuntu uses Unity by default if I'm not mistaken

This shouldn't be an issue. I've had Krita running on Xubuntu. However, as mentioned, Krita will drag in a lot of extra KDE-related stuff. When I later removed it, I couldn't believe how long the list of stuff I needed to autoremove was.

But, as already mentioned, if installing through the terminal isn't working, Krita is in the Ubuntu Software Center. If you just type Krita into the search bar, it should come up.

---

### Post by anakai on 2015-07-23
It is a kde app and it will use a couple of kde depends, but if you use the command

```
sudo apt install --no-install-recommends krita
```

Maybe it will cut down the list of deps. It can lack in functionally if you use it with this command, just so you now.

---

### Post by deadflowr on 2015-07-23
I'd recommend using ppa-purge to rid yourself of the ppa for kubuntu-backports.
Those packages tend to be less than stable, IMO.
```
sudo apt-get install ppa-purge
```
then
```
sudo ppa-purge ppa:kubuntu-ppa/backports
```
This should revert all of those ppa packages to those in the normal repositories.
Which are more stable and well tested.

I'll also second the comment on the package and DE(desktop environment) does not matter.
The packages are only bringing in bloat.
Ubuntu devs work hard to make all packages run in all environments.
Be it a kde package in unity, or gnome packages in kubuntu.
Or any of the other variations thereof.

My two and a half cents, anyway...

---

### Post by v3.xx on 2015-07-23
> **anakai said:**
> It is a kde app and it will use a couple of kde depends, but if you use the command

```
sudo apt install --no-install-recommends krita
```

Maybe it will cut down the list of deps. It can lack in functionally if you use it with this command, just so you now.
Good idea, but unfortunately krida has no recommends.

[http://packages.ubuntu.com/vivid/krita](http://packages.ubuntu.com/vivid/krita)

---

### Post by Bucky Ball on 2015-07-23
> **anakai said:**
> It is a kde app and it will use a couple of kde depends ...

... and a bucket load of other stuff. There are more than a couple. :-k ;)

---

### Post by NotionCommotion on 2015-07-23
Sorry, reply to wrong post! (never mind :) ).  Please just look at the next one!

---

### Post by NotionCommotion on 2015-07-23
[COLOR=#000000]Hi all. Sorry had to sleep and go to work.[/COLOR]

[COLOR=#000000]After running my pre-mentioned scripts, I then ran "sudo apt-get remove krita".[/COLOR]

[COLOR=#000000]I then went to Software Centre (who would have known such a thing exists [/COLOR]:smile:[COLOR=#000000] ), and installed krita.[/COLOR]

[COLOR=#000000]I get the same error [/COLOR]:sad:

---

### Post by deadflowr on 2015-07-24
pre-mentioned scripts?
I don't follow that, but...

Basically, unless you downgrade all the packages from the ppa versions to the repo versions (using ppa-purge), whether nor not you remove krita or disable the ppa won't matter, as there will still be a long list of ppa packages on the system.
Krita is dependent on those packages, which is probably where the breakage is coming from.
(That's probably/a-most-likely cause. But not fully definite)

If that makes sense.

---

