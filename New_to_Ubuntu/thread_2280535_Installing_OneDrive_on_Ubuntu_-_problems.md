---
title: "Installing OneDrive on Ubuntu - problems"
date: 2015-05-31
forum: New to Ubuntu
---

### Post by james139 on 2015-05-31
Hi, I'm trying to install OneDrive on ubuntu 14.04 and have ran into problems almost straight away. I'm following [this how-to]("http://www.omgubuntu.co.uk/2014/06/one-drive-ubuntu-integration"):, and have got to the sudo ./ install part and it says 'sudo: ./install: command not found'. I can't see what I'm doing wrong!

---

### Post by tristan16 on 2015-05-31
It looks like the program has been updated since the article. Try this instead:
```
bash install.sh
```
It installs required packages and the Onedrive program.

---

### Post by PhilGil on 2015-05-31
Did you cd to the the onedrive-d-future directory? Your command prompt should look something like this:
```
user@computername:~/onedrive-d-future$
```

If you're in the right directory then try the suggestion from the previous post.

---

### Post by james139 on 2015-05-31
Thanks tristan16, worked first time. I tried installing the /sh file with sh ,.install.sh after reading a how-to - didn't work!

---

### Post by james139 on 2015-05-31
Actually I don't know what it's done. It installed and I followed the instructions  but I can't find the installed program...

---

