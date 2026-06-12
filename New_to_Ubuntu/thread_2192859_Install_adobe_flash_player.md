---
title: "Install adobe flash player"
date: 2013-12-10
forum: New to Ubuntu
---

### Post by Mark de J on 2013-12-10
Hello,

How can I install Adobe Flash Player (last version) on Ubuntu? I need it in Chromium.

Mark

---

### Post by BlinkinCat on 2013-12-10
Hi,

I don't know if this will help -

[https://help.ubuntu.com/community/FlashPlayerStandalone](https://help.ubuntu.com/community/FlashPlayerStandalone)


Cheers - :P

---

### Post by sandyd on 2013-12-10
> **sir.mark1994 said:**
> Hello,

How can I install Adobe Flash Player (last version) on Ubuntu? I need it in Chromium.

Mark

Chromium supports pepper flash, you can get it by using the instructions at [http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html](http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html)

---

### Post by Mark de J on 2013-12-10
I don't get it working... :(

---

### Post by Nr90 on 2013-12-10
You could also just install Chrome.
It comes with pepper so should work out of the box.

---

### Post by deadflowr on 2013-12-10
You could either try the pepperflash method or
install the adobe-flashplugin
```
sudo apt-get install adobe-flashplugin
```
or what I do
```
sudo apt-get install flashplugin-installer
```
which then install a program that fetches the adobe-flashplugin directly from adobe.
I don't know what the difference is, but it works.
and of course you could install the restricted-extras package
```
sudo apt-get install ubuntu-restricted-extras
```
sidenote, if you're running xubuntu,kubuntu,lubuntu change the package name for it.
Also if you do this method, use the tab,spacebar, and arrow keys to navigate the EULA that will come up.

When you do get it installed, open chromium and look to make sure the plugin is enabled.

---

### Post by Mark de J on 2013-12-10
I got it, installed Google Chrome and websites where I need flash player are working, thanks!

---

