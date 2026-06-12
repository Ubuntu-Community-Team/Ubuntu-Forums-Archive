---
title: "install new software"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by tbrownarcher on 2008-09-02
I'm trying to install software such as flashplayer and java.  I'm getting nowhere. for instance java is downloaded as jre-6u7-linux-i586.bin or the *rpm.bin file I cannot use either.  I think i downloaded Alien to convert rpm files to deb files but after getting it with synaptic I cannot find where it put it if it was successful.

I'm finding that i need to use a .deb file but I can't find one so what do i do?  

Thanks,
Nate

---

### Post by mikewhatever on 2008-09-02
Both java and flash are in the repositories, no need to download stuff. The easiest way to install them is with Add/Remove.

---

### Post by halitech on 2008-09-02
check here for an easier way to install java and flashplayer

[http://ubuntuforums.org/showthread.php?t=766683&highlight=java+install](http://ubuntuforums.org/showthread.php?t=766683&highlight=java+install)

---

### Post by brentoboy on 2008-09-02
if you install the package ubuntu-restricted-extras
you will get most of that stuff and other thigns you might not even realize you would like to have.

---

### Post by jemate18 on 2008-09-02
To install [java].bin

cd to that directory

type
```
chmod 750 [java].bin
```

and
```
sudo ./[java].bin
```

---

### Post by Miljet on 2008-09-02
I can certainly sympathize with you. The first time I installed Ubuntu, I spent a solid week trying to install java the way you are trying before I learned that almost everything you will ever need is in the repositories.

First go to system-> Administration-> Software Sources. Check the boxes for main, universe, restricted, and multiverse. You don't need source code, and while you are there, uncheck the CD ROM. Close that window and look under Applications-> Add/Remove. In the search box type "Ubuntu restricted extras". Wait a few seconds until search finds it. Put a check beside it and click on "apply changes." It will download and install what you need is just a couple of minutes.

You will still need to open Firefox and click Edit-> Properties and click the Content tab. Ensure that java is enabled. Close and restart Firefox and you should be in business.

Welcome to Ubuntu and happy computing.

---

### Post by Miljet on 2008-09-02
Sorry, I just noticed that you are running Kubuntu. The menus will probably be slightly different. I'm not familiar with KDE, but the basic steps will be the same.

1. Enable extra repositories 
2. Use Add/Remove to install
3. Enable java in your browser

---

