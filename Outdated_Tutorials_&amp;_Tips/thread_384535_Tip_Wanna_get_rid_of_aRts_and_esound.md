---
title: "Tip: Wanna get rid of aRts and esound ?"
date: 2007-03-14
forum: Outdated Tutorials &amp; Tips
---

### Post by SuperDindon on 2007-03-14
**[COLOR="Sienna"]Why would I like to get rid of aRts ?[/COLOR]**

Maybe.. you want to get ahead of your time (KDE 4) ? Want sound in non-arts software or want to maximize the prominence of your ALSA configuration ( see below ) ? Or you just noticed that arts is totally useless and wonder why it is still eating your resources ? Let's blast it !

Read also : [http://ubuntuforums.org/showthread.php?t=344599](http://ubuntuforums.org/showthread.php?t=344599)

**[COLOR="Sienna"]Just do it![/COLOR]**

First install the package "sox", which is a lil' CLI program which has the ability we are looking for : play most types of sound files through ALSA.

Then we'll make a script we'll call kdeplay and place in /usr/local/bin :
```
sudo kwrite /usr/local/bin/kdeplay
```
Fill it :
```
#!/bin/sh
VOLUME=0.75
sox -q $1 -t alsa -v $VOLUME default

```
Save it, close kwrite and make the new script executable :
```
sudo chmod a+x /usr/local/bin/kdeplay
```

Now go in the KDE Configuration Center -> Sound & Multimedia -> System notifications -> Player configuration. Tick "Use an external player" and enter the path of our script above : /usr/local/bin/kdeplay. Job is done!
Now you can disable aRts in Sound & Multimedia -> Sound system and still enjoy KDE sounds ;)

**[COLOR="Sienna"]And what about esound ?[/COLOR]**

Sorry Gnomers, there's no way to escape from esound for now. You can however redirect esound to dmix so esound won't monopolize your hardware, change this line in /etc/esd/esd.conf :
```
spawn_options=-terminate -nobeeps -as 1
```
to :```
spawn_options=-terminate -nobeeps -as 1 -d default
```

---

### Post by Ateo on 2007-05-20
Why not just akodeplay for sounds? That's what I do. No real need to do all the above (for KDE) since akodeplay is installed by default and performs better than sox.

Just food for though.

---

### Post by SuperDindon on 2007-05-20
Hi,
That's interesting, but does akodeplay support volume ?

---

### Post by Chareos on 2007-05-26
in a multiple-soundcard scenario, would you suggest sox or akodeplay in order to send sound to a specific soundcard ?

I mean: do these programs let you choose the target sound device ?

---

### Post by anachreon_ on 2007-11-28
Anybody have any further thoughts on this?  I have a Dell Inspiron 9300 laptop into which I plug a PCMCIA Soundblaster Audigy 2 ZS Notebook.  Everything worked pretty well under Kubuntu Feisty, but under Gutsy I keep getting errors regarding aRts on startup, and basically don't get sound any more.  Not sure what the problem is, but this sounds like a possible solution.  Can anybody offer some help?

Thanks.

---

