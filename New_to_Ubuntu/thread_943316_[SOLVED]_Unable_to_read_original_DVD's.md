---
title: "[SOLVED] Unable to read original DVD's"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by fr.theo on 2008-10-10
Hello,

I have install "quick star" and all the codex i could find in the "add remove" under the Applications menu.


however i still cannot view my DVD's especially original ones could any one help me please.


thank you.

---

### Post by SunnyRabbiera on 2008-10-10
are your disks finalized?
and did you install libdvdcss?

---

### Post by Liviu-Theodor on 2008-10-10
In [FONT="Courier New"]Synaptic Package Manager[/FONT], install the [FONT="Courier New"]libdvdcss2[/FONT] package.
Or use in a terminal:
```
sudo apt-get install libdvdcss2
```

---

### Post by hyper_ch on 2008-10-10
(1) add the medibuntu repos

(2) install the libdvdcss2 package.

---

### Post by fr.theo on 2008-10-10
thank you for your reply, but these are DVD's which i have bought not made, and i am not to sure about file you refer to but i installed all i could find, if you think this file will help please instruct me on how to install it or down load it.



Thank you once again.

---

### Post by Liviu-Theodor on 2008-10-10
> **hyper_ch said:**
> (1) add the medibuntu repos

(2) install the libdvdcss2 package.

The APT line for medibuntu is: [http://packages.medibuntu.org/](http://packages.medibuntu.org/) and must entered at [FONT="Courier New"]System->Administration->Software sources[/FONT].

---

### Post by lisati on 2008-10-10
Before we answer, are you just trying to play the DVDs? (We don't want to encourage situations where there could be legal hassles)

Type the following commands at the terminal, and you should be able to play DVDs:
```

sudo aptitude install libdvdnav4 libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh

```
If all goes well, you won't need to add extra repositries, and you should be able to play commercial DVDs.

---

### Post by WWSmith36 on 2008-10-10
Please check that you have all repositories enabled in System > Administration > Software sources.

Then run this command:

```
sudo apt-get install ubuntu-restricted-extras
```

Now you have the most of the codecs needed to play most of the multimedia you may own.

Also you should setup the Medibuntu repository

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

then

```
sudo apt-get update 
sudo apt-get install libdvdcss2

```

This will give you DVD support.

---

### Post by hyper_ch on 2008-10-10
google for "medibuntu", the first hit on the list is what you look for and they have install instructions... I'm sure you can work this out.

---

### Post by fr.theo on 2008-10-10
all i want to do is watch them not replicate them, no illegal stuff, it just frustrating when you cant watch your favorite DVD's.



but thanks for the Help.

---

### Post by SunnyRabbiera on 2008-10-10
> **fr.theo said:**
> all i want to do is watch them not replicate them, no illegal stuff, it just frustrating when you cant watch your favorite DVD's.



but thanks for the Help.

well if you install libdvdcss it should work for most DVD's

---

### Post by fr.theo on 2008-10-10
Thank you to all of you, and all the Ubuntu user and professionals it worked, Thanks again.

---

### Post by mlentink on 2008-10-10
Just out of curiosity: have you read [this]("https://help.ubuntu.com/8.04/musicvideophotos/C/video.html")?

---

### Post by fr.theo on 2008-10-10
no but thank you for bringing it to my attention.

---

### Post by mlentink on 2008-10-10
OK. In general, you'&#314;l find the documentation in [https://help.ubuntu.com/](https://help.ubuntu.com/) answers many questions. So do a number of other sites, e.g.:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)
but there are others.

---

