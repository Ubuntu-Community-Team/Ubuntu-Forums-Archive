---
title: "Installing PyScripter"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by thschiavo on 2008-06-27
I'm using Emacs to write my python scripts, but I tried that PyScripter ([http://mmm-experts.com/Products.aspx?ProductID=4](http://mmm-experts.com/Products.aspx?ProductID=4)) in windows and I would like to use it in Ubuntu. I saw some people in this Forum talking about PyScripter, but some of them are using it in Windows.

Is there anyway to install PyScripter in Ubuntu without using wine? :!:

PS - I wasn't able to find this software in synaptic.

---

### Post by deadgobby on 2008-06-27
[http://bytes.com/forum/thread732080.html](http://bytes.com/forum/thread732080.html)

---

### Post by thschiavo on 2008-06-27
Couldn't find any way to install PyScripter in this link, but I'll try that Eric editor... This one sounds like PyScripter.

Anyway, Thanks! It solves my problem! : )

---

### Post by tamoneya on 2008-06-27
if you are really attached to a certain windows program you could install it through wine.  Wine allows you to run windows programs on linux.  Wine is found in synaptic and then you just download the exe file for pyscripter and when you double click it wine will be called and it will install it for you.

---

### Post by thschiavo on 2008-06-29
> **tamoneya said:**
> if you are really attached to a certain windows program you could install it through wine.  Wine allows you to run windows programs on linux.  Wine is found in synaptic and then you just download the exe file for pyscripter and when you double click it wine will be called and it will install it for you.

I thank you for reply, but I was talking about not using wine. 

> **thschiavo said:**
> (...) Is there anyway to install PyScripter in Ubuntu without using wine? :!: (...)

But at the end of my search I think I'm going to keep with Emacs in Ubuntu, hehehehe

---

### Post by icis4 on 2009-11-29
If somebody is curious how to install PyScripter in Ubuntu, but in Wine follow these simple steps:
1. Download windows python installer into wine drive c: 
2. Install Python for Windows:
```
~$wineconsole cmd
z:\home\user>c:
c:>msiexec /i python-2.6.4.msi

```[FONT=Lucida Console]3. Download Pyscripter exe installer
4. Right click over the exe and choose Open with Wine program loader
5. ... thats all, enjoy :popcorn:
[/FONT]

---

### Post by pattonjm on 2011-08-24
> **icis4 said:**
> If somebody is curious how to install PyScripter in Ubuntu, but in Wine follow these simple steps:
1. Download windows python installer into wine drive c: 
2. Install Python for Windows:
```
~$wineconsole cmd
z:\home\user>c:
c:>msiexec /i python-2.6.4.msi

```[FONT=Lucida Console]3. Download Pyscripter exe installer
4. Right click over the exe and choose Open with Wine program loader
5. ... thats all, enjoy :popcorn:
[/FONT]

That helped me, thanks!

---

