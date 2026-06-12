---
title: "What is Kubuntu??"
date: 2005-03-19
forum: Outdated Tutorials &amp; Tips
---

### Post by bigblop on 2005-03-19
What does this name stand for??

---

### Post by DJ_Max on 2005-03-19
It's Ubuntu Linux with the KDE Desktop Environment suite, insteal of Gnome.

---

### Post by bigblop on 2005-03-19
I have installed regular Ubuntu and have installed KDE version 3.2.3 I guess there is no difference between my Ubuntu and Kubuntu then?

When will it be possible to instal KDE 3.4 for Ubuntu?

---

### Post by DJ_Max on 2005-03-19
I'm not sure, but you might be able to use the Backports.
But I am sure that Hoary has it.

---

### Post by bigblop on 2005-03-19
I am a linux newbie. What does Backports and Hoary mean??

---

### Post by TheOtherShoe on 2005-03-19
Hoary is the latest version of Ubuntu; it is currently in testing. Backports are packages from Hoary that are made available for use in Warty, the currently stable version of Ubuntu.

Also, Hoary is short for Hoary Hedgehog and Warty is short for Warty Warthog. And the version you have installed is almost certainly Warty.

---

### Post by bigblop on 2005-03-19
Ok sp if I would like to install KDE 3.4 I need to use a backport right? But how do I use a backport on my warty Ubuntu??

---

### Post by GentleHatemonger on 2005-03-19
There is no backport for KDE to Warty nor will there be (to my best judgement).
Hoary is surprisingly stable already, so if you are willing to take the plunge, launch these commands:

```

sudo sed -i 's/warty/hoary/g' /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade

```

Then to install KDE:

```

sudo apt-get install kubuntu-desktop kubuntu-default-settings

```

Then just restart your comp to load up Hoary

---

### Post by jdong on 2005-03-19
Kubuntu: A fancy name for Ubuntu, with KDE installed from Universe.

Backports: [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)


As far as a KDE 3.4 backport, I tried a 3.3.x backport, and that failed miserably. The metapackages are a pain to build by hand, and there were too many dependencies that I couldn't satisfy.

---

