---
title: "can't play mp3"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by tubularBell on 2008-04-22
Seems like I somehow run into a new problem everytime I find a solution for a previous one..

As it is now, I can't play mp3s.

I've installed the gstreamer0.10-fluendo-mp3, but it still isn't working. Tried various audioplayers.

Since the ingenious check-these-topics-before-posting-function is removed, I really can't find any similar threads.


Very thankful for help!

---

### Post by bijeeshvs on 2008-04-22
if you have not tried please try XMMS with MP3 Support (Use synptic to install)

---

### Post by Hallvor on 2008-04-22
```
sudo apt-get install ubuntu-restricted-extras
``` should solve all your multimedia needs.

edit: Yes, xmms is a decent player. It has its own codecs, so you don`t have to install anything else than the application itself.

```
sudo apt-get install xmms
```

---

### Post by bijeeshvs on 2008-04-22
Also install VLC media player it can play almost anything (even windows vista cd as a movie ha ha  ahhahha........) supports every videocodec, use synaptic to install


you can get more info here 

[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)
(use synaptic to install becoz its better than downloading)

---

### Post by tubularBell on 2008-04-22
Currently blacklisting/de-blacklisting sound modules(?). Figured I could play mp3 through my sucky internal sound card, but not the external one.

Anyway, thanks a lot for your help !!

I'll be back with updates..


..While I'm at it, any recommendations beside xmms and amarok? In Windows, I'm something of a foobar-person :P

---

### Post by ace007 on 2008-04-22
+1 for amarok, give it a chance...  the only real package you need to install to make multimedia things work is the restricted extras package

---

### Post by tubularBell on 2008-04-22
Amarok seems like a great software. It was the default skin that kind of made me back off. But ok, I'll give it another chance :)

---

### Post by spec-chum on 2008-04-22
Amarok's great.  I personally prefer Exaile though, but they're both excellent.

Why not try them both?  They're free. :)

---

### Post by tubularBell on 2008-04-22
Alright, now I have Rythmbox and Exaile(!) working fine with my external sound card, so it can't possibly be the hardware.

Amarok keeps giving me 'MP3 support is now installed, you will need to restart Amarok.' every single time I start it and try to play an mp3-file. Any suggestions? >_<

Haven't looked up output plugins for xmms yet. Will get back to it once I get Amarok to work!

---

### Post by Ideastone on 2008-04-22
Once you get your mp3's working you should really check out Banshee. It's great like Amarok, but it's native to Gnome so that you don't have to install the KDE libraries.

---

