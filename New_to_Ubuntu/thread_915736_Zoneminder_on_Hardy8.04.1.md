---
title: "Zoneminder on Hardy8.04.1"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by yayo78 on 2008-09-10
Good morning people...I have just installed Zoneminder1.22.3 on my Ubuntu8.04.1. (apt-get install zoneminder)
All ok during installation, but, after added a new monitor, all that i see is not video from my ip-cam, but a broken image link.
Someone have same problem?:confused:
bye
:KS

---

### Post by lapichiflati on 2008-10-21
After spending some time to get this to work on 8.04.1 I can say this is the best way from a fresh install to get everything working:

make sure your /usr directory is on the largest partition, this is where your captured video will live.  You could conceivably make /usr/share on another partition or disk for increased performance.  I don't recommend using your home directory for video storage, as permission problems and apache config is tough.

update
install LAMP
install zoneminder from package manager
follow the instructions for debian on the wiki to the letter:
[http://www.zoneminder.com/wiki/index.php/Main_Documentation#Installation_from_a_.deb]("http://www.zoneminder.com/wiki/index.php/Main_Documentation#Installation_from_a_.deb")
You should be good to go, all permissions will be good.

---

