---
title: "install flash player?"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by Matrix01 on 2011-12-15
how do u install flash player?
i clicked 'install' in software cneter,
that did not work.

---

### Post by crave-n on 2011-12-15
> **Matrix01 said:**
> how do u install flash player?
i clicked 'install' in software cneter,
that did not work.
go to youtube and try to play anyy video the firefox asks you wether to install missing plugins just say yes and install it... :)

---

### Post by Matrix01 on 2011-12-15
which one:
ubuntu (apt)
            (rpm) 32 bit.  
            (tar.gz)
            (yum)?

---

### Post by crave-n on 2011-12-15
bdont go into the adobe website.....
when you try to play a video a toolbar lyk thingy whill appear below the address bar it will hav a button called install the missing plugins click that one....
:D

---

### Post by Matrix01 on 2011-12-15
apt did not get downloaded on Opera.

which one is it on firefox;
rpm,
tar.gz,
yum?

> **crave-n said:**
> bdont go into the adobe website.....
when you try to play a video a toolbar lyk thingy whill appear below the address bar it will hav a button called install the missing plugins click that one....
:D

---

### Post by crave-n on 2011-12-15
just search for flash player in ubuntu software center... and install it

---

### Post by Ctrl-Alt-F1 on 2011-12-15
I've always had success with > sudo apt-get insall flashplugin-installer

It will install and update flash for you when important.  Also installs 32bit compatibility libraries if you're using a 64bit machine, which can come in handy for other things (games).

---

### Post by nothingspecial on 2011-12-15
Moved to Absolute Beginner Talk.

---

### Post by JRV on 2011-12-15
I would just install ubuntu-restricted extras.

It is a large package that includes:
[list]
[*] Video Audio Codecs.
[*] Java
[*] Flash
[*] MS core fonts
[*] UNRAR
[/list]

---

### Post by Matrix01 on 2011-12-15
mentioned earlier,
clicked 'install' in software center , that did not work.
 
> **crave-n said:**
> just search for flash player in ubuntu software center... and install it

---

### Post by TBABill on 2011-12-15
```
sudo apt-get update
```
Then ```
sudo apt-get install flashplugin-installer
```
You can copy/paste those into a terminal and let them run. If you need more codecs you can also do as suggested above and install Ubuntu restricted extras package, also found in Ubuntu Software Center, assuming it will install for you. If not, just ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Matrix01 on 2011-12-16
[ATTACH]209179[/ATTACH]

thank you!
i can watch youtube now :-)

> **TBABill said:**
> ```
sudo apt-get update
```Then ```
sudo apt-get install flashplugin-installer
```You can copy/paste those into a terminal and let them run. If you need more codecs you can also do as suggested above and install Ubuntu restricted extras package, also found in Ubuntu Software Center, assuming it will install for you. If not, just ```
sudo apt-get install ubuntu-restricted-extras
```

---

