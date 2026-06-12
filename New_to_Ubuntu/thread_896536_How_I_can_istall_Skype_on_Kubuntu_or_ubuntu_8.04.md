---
title: "How I can istall Skype on Kubuntu or ubuntu 8.04?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by Harmony_Of_Distortion on 2008-08-21
Hello I'm trying to install Skype 2.0.0.72-1.deb  on my Ubuntu!

How I can do this? I have already dowloaded Skype from Skype.org and I can't istall it.:(

---

### Post by OldGrey on 2008-08-21
You can first install the medibuntu repository See: 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

then install skype via synaptic plus other stuff like Google earth if you are interested.

---

### Post by billgoldberg on 2008-08-21
This command will do it.

Just copy/paste it into a terminal (konsole on kubuntu, terminal on ubuntu).

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y skype
```

That will install the latest skype version for you.

---

### Post by hector_roberts on 2009-04-20
thanks billgoldberg, really works!!!!!

---

### Post by hector_roberts on 2009-04-20
thanks!

---

### Post by edubidu on 2010-04-22
Hi,
I've found a newer version yet on my computer that works fine.
Downloadable here:
[http://diuf.unifr.ch/people/ducarroz/?Skype_for_Ubuntu_8.04_LTS](http://diuf.unifr.ch/people/ducarroz/?Skype_for_Ubuntu_8.04_LTS)

---

