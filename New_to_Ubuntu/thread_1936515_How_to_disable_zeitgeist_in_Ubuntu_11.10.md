---
title: "How to disable zeitgeist in Ubuntu 11.10?"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by ngubk on 2012-03-06
I read somewhere that zeitgeist is among the main reasons unity is chosen. But as i upgraded to ubuntu 11.10( 10.10->11.04->11.10) last week, zeitgeist is using up over 50% of my CPU whenever it runs, especially when this service logs my music (my Banshee has around 1000 songs), or my files( i'm a programmer so i modify lots of files)
So can i disable it or at least reduce its running frequency?
Thanks for any reply!

---

### Post by stinkeye on 2012-03-06
Install activity-log-manager

```
sudo add-apt-repository ppa:zeitgeist/ppa
sudo apt-get update
sudo apt-get install activity-log-manager
```

---

### Post by Script Warlock on 2012-03-06
> **ngubk said:**
> I read somewhere that zeitgeist is among the main reasons unity is chosen. But as i upgraded to ubuntu 11.10( 10.10->11.04->11.10) last week, zeitgeist is using up over 50% of my CPU whenever it runs, especially when this service logs my music (my Banshee has around 1000 songs), or my files( i'm a programmer so i modify lots of files)
So can i disable it or at least reduce its running frequency?
Thanks for any reply! check [this]("http://askubuntu.com/questions/21417/temporarily-stopping-zeitgeist")

---

### Post by ngubk on 2012-03-06
Thanks! works like charm

---

### Post by rad_sci_guy on 2012-04-14
I tried this and I get an error

E: Unable to locate package activity-log-manager


> **stinkeye said:**
> Install activity-log-manager

```
sudo add-apt-repository ppa:zeitgeist/ppa
sudo apt-get update
sudo apt-get install activity-log-manager
```

---

### Post by stinkeye on 2012-04-14
Seems the package failed to build for 11.10
[**_[COLOR="DarkRed"]https://launchpad.net/~zeitgeist/+archive/ppa/+packages[/COLOR]_**]("https://launchpad.net/~zeitgeist/+archive/ppa/+packages")
In 12.04 it is included in the default install in system settings.

---

