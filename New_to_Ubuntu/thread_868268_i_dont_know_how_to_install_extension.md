---
title: "i dont know how to install extension"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by erik.tamsen on 2008-07-23
hi
im totally new to ubuntu. after the installation from xubuntu i wanted to go to youtube but i need a extension for firefox. i downloaded the file and somehow managed to extract to tar.gz thing. now im lost and i dont know what to do with those two files.  
flashplayer-installer
libflashplayer.iso
it would be nice if someone could tell me how to install that extention

---

### Post by northern lights on 2008-07-23
Forget what you've downloaded, might as well delete those.

From the xfce-terminal run ```
sudo apt-get install flashplugin-nonfree
```

Restart your browser.

---

### Post by Tim Sharitt on 2008-07-23
ignore
Too slow, and wrong environment.

---

### Post by jimmy the saint on 2008-07-23
Another option, to save you similar issues in the future, is to install xubuntu-restricted-extras.  This package includes flash, but also some other things that you may want, like MS fonts and some other goodies.
```
sudo apt-get install xubuntu-restricted-extras
```

---

### Post by mali2297 on 2008-07-23
You might need to enable the *multiverse* repository. In the package manager Synaptic, go to Settings -> Repositories to check that the repo is enabled. Then search for **flashplugin-nonfree** and install it.

---

### Post by erik.tamsen on 2008-07-23
it worked thank you :)
it is amazing you can look around with google and try a lot of things but one post in this forum and you have solved the problem within minutes :)

---

### Post by stevoo on 2008-07-23
yes but you could have installed the downloaded one from Adobe by going into the command prompt where the file is. 
And type  : 
sudo sh flashplayer-installer

If i remember correctly that would begin the installation :)

---

### Post by Joeb454 on 2008-07-23
It would indeed :)

---

