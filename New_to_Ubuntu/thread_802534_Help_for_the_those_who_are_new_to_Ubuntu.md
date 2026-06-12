---
title: "Help for the those who are new to Ubuntu"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by anotherdisciple on 2008-05-21
I have noticed that A LOT of new users do things the hard way when it comes to installing codecs and such. You don't need to install all of them individually!!! Ubuntu has a package that does most of the work for you, so if you need any meda help try this first:

Go to the terminal... Applications > Accessories > Terminal ... and type this:

**Ubuntu:**
sudo aptitude install ubuntu-restricted-extras

**Kubuntu:**
sudo aptitude install kubuntu-restricted-extras
[B]
Xubuntu:[/B]
sudo aptitude install xubuntu-restricted-extras


This package could have saved me a lot of time had I known about it when I first started! I hope this helps someone and isn't just old news.

---

### Post by kellemes on 2008-05-21
> **anotherdisciple said:**
> I have noticed that A LOT of new users do things the hard way when it comes to installing codecs and such. You don't need to install all of them individually!!! Ubuntu has a package that does most of the work for you, so if you need any meda help try this first:

Go to the terminal... Applications > Accessories > Terminal ... and type this:

**Ubuntu:**
sudo aptitude install ubuntu-restricted-extras

**Kubuntu:**
sudo aptitude install kubuntu-restricted-extras
[B]
Xubuntu:[/B]
sudo aptitude install xubuntu-restricted-extras


This package could have saved me a lot of time had I known about it when I first started! I hope this helps someone and isn't just old news.

Great tip..
Still I think the best thing new users should do is read the standard documentation because it's all explained in there..
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

Thanks for sharing..

---

### Post by anotherdisciple on 2008-05-21
Why does the documentation always suggest add/remove or apt-get... shouldn't we tell the newer people to use aptitude?

---

### Post by civillian on 2008-05-21
probably, but this way they dont have to hunt down the exact package theyre looking for, its just a case of ctrl+c ctrl+v! Less work overall, and some learning about the CLI gets done, so everybody wins!

---

### Post by smartboyathome on 2008-05-21
Aptitude is actually not "newer", in fact, apt-get now has all the functions aptitude has, so there is no point really in using aptitude.

---

### Post by anotherdisciple on 2008-05-22
Actually I said newer PEOPLE

---

### Post by kellemes on 2008-05-22
> **anotherdisciple said:**
> Why does the documentation always suggest add/remove or apt-get... shouldn't we tell the newer people to use aptitude?

It doesn't really matter as long as you use one of both, not both.
This since aptitude handles dependencies a little different as apt-get..
Personally I like aptitude a lot, much better and efficient then apt-get, but it's a matter of taste I guess..

---

### Post by theumang on 2008-05-22
I needed some help with syncing photos to my 30g ipod video.
am using the Hardy heron on amd64..

I tried hunting before I wanted to post this..
learnt about a few like the songbirdnet, am very impressed with the looks, don't want to try if it does not help in managing photos..

learnt about Amarok & gtkpod, tested them..

they do not recognize my ipod..
but when I plug it in, it launches the rhythmic thing n allows me to play songs..

also trying to do the wine way, is it recommended for a nooob?

---

