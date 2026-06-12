---
title: "Streaming Video from internet"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by martinoheat on 2008-07-18
Hello guys,

I have added the MPlayer Plugin for Mozilla, but am still unable to watch any streamed video content online. Would really appreciate some assistance.

Cheers,

Martino

---

### Post by wolfen69 on 2008-07-18
go to synaptic and completely remove totem-mozilla. it is probably a conflict.

---

### Post by martinoheat on 2008-07-18
Hello Wolfen69,

Totem-mozilla is currently not installed. Any other ideas?

Martino

---

### Post by martinoheat on 2008-07-18
Anybody?

---

### Post by tuxxy on 2008-07-18
Did you install restricted-extras or just mplayer plugin? You need flash plugins for your browser and others such as java.

Try and search for restricted-extras in the repos this should get your videos running atleast.

---

### Post by Vivaldi Gloria on 2008-07-18
> **martinoheat said:**
> Hello guys,

I have added the MPlayer Plugin for Mozilla, but am still unable to watch any streamed video content online. Would really appreciate some assistance.



First add medibiuntu repos. Then in terminal:

```
sudo apt-get remove --purge totem-mozilla
sudo apt-get install mozilla-mplayer
```

---

### Post by martinoheat on 2008-07-18
Hello Vivaldi,

I am a newbie on Ubuntu. What is medibiuntu repos?

Martino

---

### Post by martinoheat on 2008-07-18
> **tuxxy said:**
> Did you install restricted-extras or just mplayer plugin? You need flash plugins for your browser and others such as java.

Try and search for restricted-extras in the repos this should get your videos running atleast.
I have installed pretty much every flash plug in and media player on the add/remove menu, but to no avail :(

---

### Post by Alldan on 2008-07-18
Medibuntu (Multimedia, Entertainment & Distractions In Ubuntu) is a repository of packages that cannot be included into the Ubuntu distribution for legal reasons (copyright, license, patent, etc)

i have no medibuntu package installed and i can can see any streamed video

after ubuntu installation i entered youtube and tried to watch a video. then mozilla asked me to install flashplayer-plugin. I did so and everything was ok.
do you have flashplayer-plugin installed? if yes remove it completely and then reinstall it
if this did not solve your problem install opera and try it. if it works then it's something with your mozilla

---

### Post by Vivaldi Gloria on 2008-07-18
> **martinoheat said:**
> Hello Vivaldi,

I am a newbie on Ubuntu. What is medibiuntu repos?

Martino

Medibuntu is explained here:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

And how to add it is written here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

The following commands in a terminal (Applications > Acc. > Term.) add it in ubuntu 8.04:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Then remove totem-mozilla completely by giving the command:

```
 sudo apt-get remove --purge totem-mozilla 
```

Then start synaptic (system > admin > synaptic). Go into repo sttings. Enable also restricted & multiverse repos from there and click refresh.

Now in synaptic search and install the following:

```
ubuntu-restricted-extras
w32codecs
mozilla-mplayer
```

---

