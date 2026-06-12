---
title: "Need a Linux Suggestion"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by Five_Iron_OBrien on 2013-01-06
I'm wanting to watch Netflix Movies not sure if it's possible with my laptop. It's very old. Was wondering what would be a good linux to use on it. 

It has 1.50 GHz processor & one gig of Ram.

It's an acer TravelMate 2420 that runs on Windows XP

---

### Post by Terl on 2013-01-06
Unfortunately Netflix is not Linux friendly.  I know there are projects to try and get it working well in Linux but I am not aware of successful ones although I did find this [http://lifehacker.com/5963726/netflix-finally-comes-to-ubuntu-in-the-form-of-an-unofficial-desktop-app]("http://lifehacker.com/5963726/netflix-finally-comes-to-ubuntu-in-the-form-of-an-unofficial-desktop-app") after googling a little.  

With the specs on the PC you have you would want to try Lubuntu which uses the LXDE desktop rather than Ubuntu itself as the specs are a little light on your pc.

---

### Post by offgridguy on 2013-01-06
> **terl said:**
> unfortunately netflix is not linux friendly.  I know there are projects to try and get it working well in linux but i am not aware of successful ones although i did find this [http://lifehacker.com/5963726/netflix-finally-comes-to-ubuntu-in-the-form-of-an-unofficial-desktop-app]("http://lifehacker.com/5963726/netflix-finally-comes-to-ubuntu-in-the-form-of-an-unofficial-desktop-app") after googling a little.  

With the specs on the pc you have you would want to try lubuntu which uses the lxde desktop rather than ubuntu itself as the specs are a little light on your pc.+1

---

### Post by evilsoup on 2013-01-06
There is a netflix desktop application that utilises wine to use Silverlight 4. Unfortunately, it's pretty variable; it works for some people, but not for others, and it works for some programmes, but not for others. It's available in a PPA:

```

sudo add-apt-repository ppa:ehoover/compholio
sudo apt-get update
sudo apt-get install netflix-desktop

```

Whether it will work on your laptop... well, there's only one way to find out.

---

### Post by haqking on 2013-01-06
```
sudo apt-add-repository ppa:ehoover/compholio

``````
sudo apt-get update && sudo apt-get install netflix-desktop
```

edit: ninja'd above

---

### Post by mysteriousdarren on 2013-01-07
[http://www.webupd8.org/2012/11/how-to-use-netflix-in-ubuntu-through.html](http://www.webupd8.org/2012/11/how-to-use-netflix-in-ubuntu-through.html)

---

