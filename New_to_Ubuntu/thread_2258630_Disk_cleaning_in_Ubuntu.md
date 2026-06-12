---
title: "Disk cleaning in Ubuntu?"
date: 2014-12-29
forum: New to Ubuntu
---

### Post by poorguy on 2014-12-29
being new to ubuntu i am wondering if you have to disk clean as i had to do in windows. in windows i used ccleaner is there such a utility as for linux.
thanks.
poorguy

---

### Post by Bucky Ball on 2014-12-29
Welcome. All depends on what you mean by disk clean. Do you mean to fragment the drive or delete unwanted programs? I haven't used Win for some time so a little unfamiliar. Which software did you use in Win?

There are things to help you clean up in Ubuntu like [Bleachbit]("http://bleachbit.sourceforge.net/"), but that should be used with caution, as it can seriously screw things up if you don't know your way around it. Here are a few basic commands you can use in a terminal to clean things up and a description of what they do, from [HERE]("http://stchman.com/cleanup.html"). They are pretty much all I've ever used (autoremove is pretty much all I use, really, the others rarely):

 > First command is the package autoclean.  What autoclean does is remove partial packages from the system. To use autoclean type the following command in a terminal:

```
sudo apt-get autoclean
```

Then enact the package clean command.  What this commnad does is to clean remove .deb packages that apt caches when you install/update programs.  To use the clean command type the following in a terminal window:

```
sudo apt-get clean
```

You can then use the autoremove command.  What the autoremove command does is to remove packages installed as dependencies after the original package is removed from the system.  To use autoremove tye the following in a terminal window:

```
sudo apt-get autoremove
```



For Firefox, you can go to the History and 'Clear Recent History ...' There are options there for what you would like to clear.

Hope that helps. ;)

---

### Post by sammiev on 2014-12-29
Much the same as above. I use this about once a month.

> echo "Cleaning Up" && sudo apt-get -f install && sudo apt-get autoremove && sudo apt-get -y autoclean && sudo apt-get -y clean

---

### Post by poorguy on 2014-12-29
hi Bucky Ball, what i used in windows was ccleaner. i will investigate bleachbit before using it. from what ihave read is that linux doesn't get stuffed up with extra garbage is  that true. just wanted to be prepared in case. i do clear browser history. thanks for the help.
poorguy

---

### Post by poorguy on 2014-12-29
hi sammiev, thanks fotr the info.
poorguy

---

### Post by Holger_Gehrke on 2014-12-29
A few more things to clean up:

A lot of programs write temporary data to ~/.cache. After removing an application it could be worthwhile to see whether something got left there. I wouldn't just delete these for programs you still have installed, though.

Thumbnails in ~/.thumbnail/fail, ~/.thumbnail/large and ~/.thumbnail/normal. If you often work with images, you will find 10,000 to 20,000 thumbnail-images in there after a month or two. These you can just delete, they will get recreated as needed.

---

### Post by Jonathan Precise on 2014-12-29
Also, if you want a graphical tool, you can use ubuntu tweak:

```
pkexec sudo -i
add-apt-repository ppa:ubuntu-tweak-testing/ppa
apt-get update && apt-get install ubuntu-tweak && exit
ubuntu-tweak
```

It hasn't been mantained in a while, but it still is a somewhat good program for tweaking. (WARNING: Please, please, please, don't use it's app store, as you can add (potentially malicious/dangerous) PPAs. Apart from that, you can use anything you want, like the Janitor.) Apart from the tweaks you can add to your system, there is the Janitor section, which you can use to clean up unneeded packages, unneeded cache, older/unused kernels, etc.

Just be careful to not clean the Firefox cache if you have Firefox open, as it can log you out of your sites temporarily, and it can be a pain to log in again.

---

### Post by poorguy on 2014-12-29
hey all, cool thanks for all the input. i am just hunting for info now am not going to clean or clear anything until i am sure f\of what i need to remove only when needed. still needing to learn more which is why i am here. thanks for the space. 
poorguy

---

### Post by monkeybrain20122 on 2014-12-29
Install bleachbit in software centre which works like ccleaner. It has two parts. The one for administrator clean the system (APT etc) and the one for ordinary user clean the /home (browser cache etc) Be careful about the settings, some features are experimental and should not be checked. See my screenshots (first one for administrator, second one for ordinary user)

---

### Post by poorguy on 2014-12-29
> **monkeybrain20122 said:**
> Install bleachbit in software centre which works like ccleaner. It has two parts. The one for administrator clean the system (APT etc) and the one for ordinary user clean the /home (browser cache etc) Be careful about the settings, some features are experimental and should not be checked. See my screenshots (first one for administrator, second one for ordinary user)

thanks for the info.
poorguy

---

