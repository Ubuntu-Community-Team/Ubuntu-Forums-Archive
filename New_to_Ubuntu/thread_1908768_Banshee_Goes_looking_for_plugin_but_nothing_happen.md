---
title: "Banshee Goes looking for plugin but nothing happens"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-01-14
Hi there all

Ive just installed Linux 11.04. I thought I would import my music library, which are all mp3's. Banshee says its missing a plugin, and wants to search to find one. 
I click on search, the box dissapears....and nothing happens.
Most times I click on the play button and just nothing at all happens.

I know the sound is working, even now I am playing an audio CD, so banshee recognises them, but not my mp3's.

My question is whats happening? Shouldn't Banshee import the plugin? Maybe its something deeper because I cant get Ubuntu Software Center to do anything, it just searches and searches and returns nothing. And yes, I'm connected to the internet.

Please help.

---

### Post by nothingspecial on 2012-01-14
Press Ctrl-Alt-T to open a terminal.

Copy and paste this

```
sudo apt-get install ubuntu-restricted-extras
```

You will need to type your password, which you won't see, just type it and press enter.

This will install a whole bunch of goodies including flash and mp3 support.

I t will also install some fonts which come with an EULA, to except it you will need to press your Tab key to select ok.

---

### Post by Rodney9 on 2012-01-14
Ubuntu Desktop Computing Made Easy - 
[http://ubuntuforums.org/showthread.php?t=1884105&highlight=lmms](http://ubuntuforums.org/showthread.php?t=1884105&highlight=lmms)

Rodney

---

