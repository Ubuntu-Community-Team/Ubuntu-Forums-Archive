---
title: "Cannot install LibreOffice on Ubuntu 10.04 Lucid"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by markless on 2012-11-10
Hello everyone,

I'm running into a bit of trouble, and i can't seem to figure out the problem. I have tried adding the key for LibreOffice and was successful in doing so. however, after updating and trying to install Libre, it is producing the following error.

"libreoffice:
 Depends: libreoffice-core but it is not going to be installed
 Depends: libreoffice-writer but it is not going to be installed
 Depends: libreoffice-calc but it is not going to be installed
 Depends: libreoffice-impress but it is not going to be installed
 Depends: libreoffice-draw but it is not going to be installed
 Depends: libreoffice-math but it is not going to be installed
 Depends: libreoffice-base but it is not going to be installed
 Depends: libreoffice-filter-mobiledev but it is not going to be installed
 Depends: libreoffice-java-common but it is not going to be installed
 Recommends: libreoffice-gnome but it is not going to be installed or
 	libreoffice-kde but it is not going to be installed"

I haven't a clue as to why  this continues to come up. It's quite vague. 
Attached is the screenshot of the error.

Can anyone help me out?

Thank you,

---

### Post by newb85 on 2012-11-10
> **markless said:**
> I have tried adding the key for LibreOffice and was successful in doing so. 

What do you mean by this?  Are you referring to the GPG key?  Or perhaps you meant that you added the LibreOffice PPA?

---

### Post by Zill on 2012-11-10
markless:  Can I ask *why* you wish to do this?

The default office suite in Lucid is OpenOffice, rather than LibreOffice, and so this should already be installed.

Leaving "politics" aside, OpenOffice and LibreOffice are basically the same application with effectively identical functionality.

Is there anything you consider can be done with LibreOffice that you currently cannot do with OpenOffice?

---

### Post by monkeybrain2012 on 2012-11-10
10.04 comes with OpenOffice.org which is in conflict with LibreOffice, you have to remove it first. To get rid of everything in the terminal type

sudo apt-get autoremove openoffice*

See if you can install LibreOffice afterwards.

---

### Post by monkeybrain2012 on 2012-11-10
> **Zill said:**
> markless:  Can I ask *why* you wish to do this?

The default office suite in Lucid is OpenOffice, rather than LibreOffice, and so this should already be installed.

Leaving "politics" aside, OpenOffice and LibreOffice are basically the same application with effectively identical functionality.

Is there anything you consider can be done with LibreOffice that you currently cannot do with OpenOffice?

Yes, Lucid comes with a really old version of OpenOffice, I don't know about the new apache OpenOffice (never use it) but Libreoffice is definitely a lot faster than the Lucid version, among other things.

@OP why are you still using Lucid? I remember what it was like, it is like ancient history now. :)

---

### Post by newb85 on 2012-11-10
> **Zill said:**
> Leaving "politics" aside, OpenOffice and LibreOffice are basically the same application with effectively identical functionality

Leaving politics aside would obscure a minor point of contention with your general comparison.  If a large contingent of developers left OpenOffice for LibreOffice because OpenOffice's new owners were hampering development, it stands to reason there would be differences between the programs.

---

### Post by Zill on 2012-11-10
> **monkeybrain2012 said:**
> ...Libreoffice is definitely a lot faster than the Lucid version, among other things...
As they both started out with the same code-base I would be surprised if LO is *much* faster than OOo.  Any difference in speed is probably due to different versions of the programs and, as you say, the Lucid version is quite old now.
> **monkeybrain2012 said:**
> ...@OP why are you still using Lucid? I remember what it was like, it is like ancient history now. :)
Lucid is a LTS release and so remains supported until April 2013.  Some of us prefer stability to the latest "bells & whistles" so stick to LTS releases.  It works for me. :-)

---

### Post by newb85 on 2012-11-10
> **Zill said:**
> As they both started out with the same code-base I would be surprised if LO is *much* faster than OOo.  Any difference in speed is probably due to different versions of the programs and, as you say, the Lucid version is quite old now.


With the initial release of LibreOffice, the developers reduced memory requirements, reduced reliance on Java, and switched to using Cairo for font rendering.  I would imagine these also contribute to the speed.

---

### Post by markless on 2012-11-10
Hello all,

I have tried removing all of OpenOffice in the beginning before I installed Libre. I knew that it had to be removed, so I did just as -monkeybrain2012- had mentioned, "sudo apt-get autoremove openoffice"

It has removed "OO", however I am unable to install Libre, or even re-install OO as well. 
I continue to get the same error message each time, just a bit different wording, obviously.

Thank you,

---

### Post by monkeybrain2012 on 2012-11-10
This is going to be painful. When that happens try to use synaptic to install those packages that it says won't be install and look at the error messages (say libreoffice-core) and repeat the process, usually after a few trials you will be nail down the conflict, chances are you might have added some ppas so some dependencies several steps down the road may be screwed up.

---

### Post by ercherramon on 2012-11-12
hello. I also I have ubuntu lucid. and also had the same problem. the problem itself is with repositories of libreoffice only packages are available for versions 11.10, 12.04 and 12.10. you just need to remove the repository of libreoffice and add this new repository if it works:

```
sudo add-apt-repository ppa:ricotz/ppa
``````
sudo aptitude update
``````
sudo apt-get install libreoffice libreoffice-gnome
```This repository will install version 3.5.7.2. but at least this version works great.

NOTE: These are official repositories. packages are made &#8203;&#8203;by the same who run the repository libreoffice: Rico Tzschichholz. Just in case you can check the repository Launchpad page you suggest and official page LibreOffice repository.

[https://launchpad.net/~ricotz/+archive/ppa]("https://launchpad.net/~libreoffice/+archive/ppa")

[https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

---

### Post by newb85 on 2012-11-12
There are two official PPAs for LibreOffice.

For test builds and backports:
```
sudo add-apt-repository ppa:libreoffice/ppa
```

For a more stable experience:
```
sudo add-apt-repository ppa:libreoffice/libreoffice-3-5
```

Both should work on Lucid:
[https://launchpad.net/~libreoffice/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~libreoffice/+archive/ppa?field.series_filter=lucid)
[https://launchpad.net/~libreoffice/+archive/libreoffice-3-5?field.series_filter=lucid](https://launchpad.net/~libreoffice/+archive/libreoffice-3-5?field.series_filter=lucid)

---

### Post by ercherramon on 2012-11-12
> **newb85 said:**
> There are two official PPAs for LibreOffice.

For test builds and backports:
```
sudo add-apt-repository ppa:libreoffice/ppa
```For a more stable experience:
```
sudo add-apt-repository ppa:libreoffice/libreoffice-3-5
```Both should work on Lucid:
[https://launchpad.net/~libreoffice/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~libreoffice/+archive/ppa?field.series_filter=lucid)
[https://launchpad.net/~libreoffice/+archive/libreoffice-3-5?field.series_filter=lucid](https://launchpad.net/~libreoffice/+archive/libreoffice-3-5?field.series_filter=lucid)

thanks for pointing out the case of the repositories, but I would also say that the repository I mentioned above is also official and has nothing unusual as it was also done by the same officers up libreoffice packages. the matter is that unfortunately libreoffice has not updated great packages for Ubuntu Lucid and therefore gives errors with the upgrade package libreoffice-core

---

### Post by klein de usa on 2012-11-13
hi 
someone that knows how should probably fix this page
[https://wiki.ubuntu.com/LibreOffice#fnref-effd974a6b922e1cfd1dc9aa5e3de3dfb5639851]("https://wiki.ubuntu.com/LibreOffice#fnref-effd974a6b922e1cfd1dc9aa5e3de3dfb5639851")

to reflect monkeybrain2012 solution to this problem also about the difference in the  PPAs

---

### Post by wolferl on 2012-11-21
> **ercherramon said:**
> hello. I also I have ubuntu lucid. and also had the same problem. the problem itself is with repositories of libreoffice only packages are available for versions 11.10, 12.04 and 12.10. you just need to remove the repository of libreoffice and add this new repository if it works:

```
sudo add-apt-repository ppa:ricotz/ppa
``````
sudo aptitude update
``````
sudo apt-get install libreoffice libreoffice-gnome
```This repository will install version 3.5.7.2. but at least this version works great.

NOTE: These are official repositories. packages are made &#8203;&#8203;by the same who run the repository libreoffice: Rico Tzschichholz. Just in case you can check the repository Launchpad page you suggest and official page LibreOffice repository.

[https://launchpad.net/~ricotz/+archive/ppa]("https://launchpad.net/~libreoffice/+archive/ppa")

[https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

Thank you very much! Definitely this works. I was getting crazy all the time trying to install OOo and/or LibreOffice from the other repositories. With your help now it works great.

---

### Post by Hagar Delest on 2012-11-23
Or instead of messing up with repositories, better use the official .debs provided on their websites, they allow to install and run AOO and LibO in parallel.

See [[Ubuntu] Installing OOo on Debian and Co.](http://forum.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by rootyourbrain on 2013-04-15
> **newb85 said:**
> 

For a more stable experience:
```
sudo add-apt-repository ppa:libreoffice/libreoffice-3-5
```


I can confirm, this works perfectly for Ubuntu 10.04.4.

So,
```
sudo apt-get purge openoffice*
```
... removed Openoffice
I added this repo line in Terminal, then:
```
sudo apt-get update && sudo apt-get install libreoffice
```

This installed a fully functional Libreoffice.

THANK YOU!

---

