---
title: "Mocp: FATAL_ERROR: Can't send() string to the server"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by cheatos on 2013-06-16
Hi all,

I have somehow screwed up my mocp...
The only thing I did was editing /etc/rc0.d/S51delmocpid but after it did not work any longer I also reedited it to its initial state.
Somehow now I alsways receive an error like
```
FATAL_ERROR: Can't send() string to the server!
```

Is there some way you can fix that?

Thanks for your help!

btw. I have a lubuntu 12.10 running

---

### Post by cheatos on 2013-06-18
bump

---

### Post by matt_symes on 2013-06-18
Hi

For the simple solution, did you try purgng and reinstalling moc ?

Also why did you edit that file ?

I also use moc (xubuntu 13.04), however i do that have that file you edited...

```
matthew-S206:/home/matthew % dpkg -l moc
zsh: correct 'moc' to '.moc' [nyae]? n
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version            Architecture       Description
+++-===========================-==================-==================-============================================================
ii  moc                         1:2.5.0~alpha4+svn amd64              ncurses based console audio player
matthew-S206:/home/matthew % 
```
```

matthew-S206:/home/matthew % ls /etc/rc?.d/*moc*
zsh: no matches found: /etc/rc?.d/*moc*
matthew-S206:/home/matthew % 

```

How did you install it ? Where did you get it from ? Did you follow a guide ? If so, then please post it here.

Kind regards

---

### Post by cheatos on 2013-06-20
ok, so this is what dpkg says about my moc:
```

michael@Michael-2013:~$ dpkg -l moc
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  moc            1:2.5.0~alph amd64        ncurses based console audio playe

```

I already have purged the moc package with apt-get but maybe I can try rremoving it with dpkg, dont know where the difference is

Thank you for your help!

---

### Post by cheatos on 2013-06-22
ok, so removing the .moc directory in my home directory made it work again.
However purging with apt-get or dpkg didn't do anything.

Thank you for your help to matt_symes

---

