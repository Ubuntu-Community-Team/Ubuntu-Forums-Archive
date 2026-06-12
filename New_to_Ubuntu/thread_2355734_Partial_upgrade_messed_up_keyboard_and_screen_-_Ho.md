---
title: "Partial upgrade messed up keyboard and screen - How can it be revoked?"
date: 2017-03-16
forum: New to Ubuntu
---

### Post by Maria_Jensen on 2017-03-16
I was trying to install git-all and I had some difficulties. While working on it the upgrade manger came on, suggesting that I did a partial upgrade. I (stupidly) accepted, but after it was done and I had restarted the system, the screen is distorted and there is no contact to the keyboard (while the mouse still works). Thanks to onscreen keyboard I was able to log in, but the problem persists. 

After googling partial upgrade (on my other computer :-) ) I realize that it is not recommended. So now I just want to undo it and I would greatly appreciate some instructions on how to safely go about it. 

The system is (was) Ubuntu 16.04 32-bit. 

Best regards
Maria

Please, anyone? 

I tried 
  
```
  sudo apt-get update && sudo apt-get dist-upgrade
```

and got 

```
  sudo: unable to resolve host gl: Connection refused
  [sudo] password for maria:
  Err:1 http//archive.canonical.com/ubuntu xenial InRelease
    Temporary failure resolving 'archive.canonical.com'
```
etc. etc. a long list of errors relating to the fact that there is no network connection.

I am not able to get Grub opened, since ubuntu is the only system on the disk and pressing down the shift key doesn't work as the keybord has no effect.

---

### Post by marchello_lippi2 on 2017-03-17
Hi, can you **ping** any other famous hosts like google.com etc?
What does **ifconfig** say?

---

