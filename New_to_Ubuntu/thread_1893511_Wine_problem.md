---
title: "Wine problem?"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by kingrat89 on 2011-12-10
Hello there,

I think my question is for Absolute Beginner Talk and it consists in:

I am running Ubuntu 10.04 Lucid and I installed Wine software, I just want to see how good the wine is working because I had a ubuntu hardy 2 years ago. The problem is that when I installed wine I tried to play 2 games: Red Alert 2 and Championship Manager 01-02 which I think are very light, but the wine is running to slow even for this games. I can't play the Red Alert and the CM is very slow. Do you have some reasonable explanation about this problem and can you tell me some configurations of the wine to work better?

Thanks a lot

---

### Post by BC59 on 2011-12-10
First I recommend you to install the latest Wine version, from the Wine PPA.

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3
```


For Red Alert 2 look here:
[http://thelinuxexperiment.com/guinea-pigs/tyler-b/how-to-play-red-alert-2-on-linux/](http://thelinuxexperiment.com/guinea-pigs/tyler-b/how-to-play-red-alert-2-on-linux/)

For Championship Manager I think the last version of Wine can play it without problem.

---

### Post by kingrat89 on 2011-12-10
> **BC59 said:**
> First I recommend you to install the latest Wine version, from the Wine PPA.

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3
```


For Red Alert 2 look here:
[http://thelinuxexperiment.com/guinea-pigs/tyler-b/how-to-play-red-alert-2-on-linux/](http://thelinuxexperiment.com/guinea-pigs/tyler-b/how-to-play-red-alert-2-on-linux/)

For Championship Manager I think the last version of Wine can play it without problem.

Damn it I read the article yesterday and I saw that the installation is very easy, but I didn't see the speed fix :(

Thanks a lot again...

---

