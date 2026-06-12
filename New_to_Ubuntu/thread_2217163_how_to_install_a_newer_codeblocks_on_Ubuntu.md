---
title: "how to install a newer codeblocks on Ubuntu"
date: 2014-04-15
forum: New to Ubuntu
---

### Post by tj107us on 2014-04-15
Hey guys, I have downloaded the newest codeblocks for linux, now I just dont know how to get it to install on Ubuntu. How do I go about installing it?

thanks,
tj

---

### Post by grier-devon on 2014-04-15
```
sudo add-apt-repository ppa:pasgui/ppa
sudo apt-get update
sudo apt-get install codeblocks
```

---

### Post by protoss96 on 2014-04-16
> **tj107us said:**
> Hey guys, I have downloaded the newest codeblocks for linux, now I just dont know how to get it to install on Ubuntu. How do I go about installing it?

thanks,
tj

Go here:
```
 http://www.codeblocks.org/downloads/26 
```

Then select debian version but be sure you are selected the correct architecture, then extraxt files and type this command in terminal to install all .deb packages:
```
sudo dpkg -i *.deb && sudo apt-get -f install
```

That should install and correct all dependecies codeblocks requires.

---

### Post by tj107us on 2014-04-16
> **grier-devon said:**
> ```
sudo add-apt-repository ppa:pasgui/ppa
sudo apt-get update
sudo apt-get install codeblocks
```



Hey thanks for the help!! I got it to work.

---

