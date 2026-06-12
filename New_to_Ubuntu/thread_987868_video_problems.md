---
title: "video problems"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by gettinoriginal on 2008-11-20
I frequently use CNN.com for news.  When I go to local sites from links in cnn, I have problems viewing video at the local stations. I do have the latests "flash" installed.  Can anyone tell me how to make video work on these local sites ??

---

### Post by Crafty Kisses on 2008-11-20
Do you have this package installed?
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by gettinoriginal on 2008-11-20
Yes, I do, and I also ran an update, but everything is up to date.

---

### Post by gettinoriginal on 2008-12-05
bump

---

### Post by linux_tech on 2008-12-05
I have 8.1 Ubuntu, I ran this command and now I have complete access to all video web and havn't found any web video that will not work.  Give it a try.
You need to use tab and enter keys to get through the java part. 

Install dvd support, audio and video codecs, flash and java

In terminal enter this command:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

---

### Post by gettinoriginal on 2008-12-05
ok, did that, but still no luck, ie:

[http://www.clickondetroit.com/video/18198190/index.html](http://www.clickondetroit.com/video/18198190/index.html)

It loads, but will not play

---

### Post by binbash on 2008-12-05
> **gettinoriginal said:**
> ok, did that, but still no luck, ie:

[http://www.clickondetroit.com/video/18198190/index.html](http://www.clickondetroit.com/video/18198190/index.html)

It loads, but will not play

works fine with firefox3.1b2 flash 10

---

### Post by gettinoriginal on 2008-12-05
hmmmmmmmmm, I have firefox 3.0.4 flash 10. Do you have any plugins installed on firefox that may help with this ??

---

