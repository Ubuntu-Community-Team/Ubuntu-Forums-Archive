---
title: "[SOLVED] Ok whats up with Flash now - works on some but not this site."
date: 2008-07-11
forum: New to Ubuntu
---

### Post by philinux on 2008-07-11
[http://news.bbc.co.uk/1/hi/world/americas/7499067.stm](http://news.bbc.co.uk/1/hi/world/americas/7499067.stm)

I want to see the cow burp captured.

Flash got updated today so hmmm. It says i got the wrong plugin.

---

### Post by aktiwers on 2008-07-11
What version do you have installed?

---

### Post by philinux on 2008-07-11
10.0.1.218 from the repo.

Works here ok and the adobe website.

Plugins reports it as Shockwave Flash 10.0.0 d525

---

### Post by aktiwers on 2008-07-11
Yeah thats strange.. I have Flash 9 here on my sisters computer and it works perfect! I see the cow and everything.
So I guess its a Flash 10 Beta thing

---

### Post by fatality_uk on 2008-07-11
10 is only beta! I am running 9,0,124,0 and works well.
Anyway to downgrade? No sound to the cow piece by the way!

---

### Post by philinux on 2008-07-11
> **aktiwers said:**
> Yeah thats strange.. I have Flash 9 here on my sisters computer and it works perfect! I see the cow and everything.
So I guess its a Flash 10 Beta thing

The bbc apparently check the version and disable it if you not got the right one. Mines future so might have to get the old one out.

This new one does full screen flash really well.

---

### Post by aktiwers on 2008-07-11
I have sound? But only when the cow clip begins..

---

### Post by aktiwers on 2008-07-11
> **philinux said:**
> The bbc apparently check the version and disable it if you not got the right one. Mines future so might have to get the old one out.

This new one does full screen flash really well.

yeah I only read good things about it. This is the first downer I read about flash 10 beta.
But I am not with my own computer now (on vacation visiting family :D)  so I dont want to install beta software on this computer.

Have no idea how to downgrade though.. Wouldnt running the flash 9 installer from adobes website do the trick?

---

### Post by forger on 2008-07-11
Works here too:```
$ apt-cache policy flashplugin-nonfree 
flashplugin-nonfree:
  Installed: 9.0.124.0ubuntu2
  Candidate: 9.0.124.0ubuntu2
  Version table:
 *** 9.0.124.0ubuntu2 0
        500 http://archive.ubuntu.com hardy/multiverse Packages
        100 /var/lib/dpkg/status
```

Try close all firefox windows and restart it.

If it's not working:
- If you're using hardy, **disable hardy-backports** from system > administration > software sources > updates, then Close and Reload

Now close firefox, open a terminal and do:
```
sudo apt-get update
sudo dpkg -P --force-depends flashplugin-nonfree
sudo rm /var/cache/apt/archives/flashplugin*.deb
sudo apt-get -f install
```

- If you're not using hardy, I don't know where the heck you got that version, unless you're using intrepid, the **unstable** version, where you're supposed to file a bug report about it :)

---

### Post by philinux on 2008-07-11
It came through as a backports update today. 

Nothing wrong with backports.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

The weird thing is I thougt Ihad adobe's version installed from their tar file. version r128

---

### Post by philinux on 2008-07-11
Used synaptic to force previous version 9.

BBC back to normal.

Can see the cow now. :lolflag:

---

### Post by forger on 2008-07-11
So.. backports are good eh :p backports will always be backports, software "not tested enough"

---

### Post by fatality_uk on 2008-07-11
> **philinux said:**
> Used synaptic to force previous version 9.

BBC back to normal.

Can see the cow now. :lolflag:

Yay!!! You got sound on that story philinux? All I heard was an odd noise at the start then nothing!!!

---

### Post by aktiwers on 2008-07-11
> **fatality_uk said:**
> Yay!!! You got sound on that story philinux? All I heard was an odd noise at the start then nothing!!!

hah! I have no sound in the beginning and then sound when the cow shows up

---

