---
title: "Unable to locate package macbuntu-os-ithemes-v9"
date: 2019-02-18
forum: New to Ubuntu
---

### Post by rayman07 on 2019-02-18
Hi everyone, new to Ubuntu 

I tried putting in  sudo apt-get install macbuntu-os-ithemes-v9 into the terminal I got an error saying  Unable to locate package macbuntu-os-ithemes-v9. 

I'm currently trying to install the dock, I've managed to get everything else but for some reason I'm having issues with this single piece. 

Otherwise this is basically what it looks like 

$ sudo apt-get install macbuntu-os-ithemes-v9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package macbuntu-os-ithemes-v9

Source is from [https://www.ubuntupit.com/ubuntu-mac-theme-tutorial-make-ubuntu-look-like-mac-os/](https://www.ubuntupit.com/ubuntu-mac-theme-tutorial-make-ubuntu-look-like-mac-os/) 
Everything worked just fine for me but for some reason  $ sudo apt-get install macbuntu-os-ithemes-v9 is the only line of code getting me an error

---

### Post by deadflowr on 2019-02-18
Which Ubuntu release?
For Ubuntu 18.04 the ithemes package is called
```
macbuntu-os-ithemes-v1804
```

---

### Post by monkeybrain20122 on 2019-02-20
Just to add that you should install synaptic (sudo apt install synaptic) It is a gui package manager and it is very convenient if you don't know the package's exact name. e.g people look up apt-get install commands from old tutorials but the name or version of the package has changed, or the package is no longer available (either synaptic, or use apt-cache search packagename)

---

