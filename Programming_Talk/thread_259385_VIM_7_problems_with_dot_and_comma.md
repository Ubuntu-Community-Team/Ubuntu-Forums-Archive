---
title: "VIM 7 problems with dot and comma"
date: 2006-09-17
forum: Programming Talk
---

### Post by krypto_wizard on 2006-09-17
Hi,

I use Ubuntu Dapper and somedays back I upgraded to VIM 7 using some
.deb file which I got somewhere on the internet. I quite don't remember
where and how I got that.

Ever since I have upgraded to VIM 7 on my desktop I have a wierd
problem.

Whenever I am in insert mode and I type a .(dot) or a ,(comma), the
cursor doesn't move forward. Instead of the cursor being on the next
whitespace it blinks on the previous character which is a dot or comma.

So whenever I am writing text and I type dot or a comma I have to use
spacebar to move to the next whitespace, whic is very annoying.

The same problems doesn't exist on my laptop and I have exact same
configuration in terms of version of linux and VIM.

Every help is greatly appreciated.

Thanks

---

### Post by baldy1324 on 2006-09-17
i think that it is a problem with that non-offical vim package you got off the internet. since dapper has vim 7...
try to run ```
sudo apt-get remove --purge vim
```
```
sudo apt-get clean
```
then ```
sudo apt-get install vim
```
this should uninstall the old vim package, remove the .deb file off your computer so apt wont use that to shortcut the downloading part, then it installs the vim from the official ubuntu repositories in your sources.list:D

---

### Post by krypto_wizard on 2006-09-17
Thanks dude. That does solve my problem. I was wondering if I messed up some settings in VIM and that had resulted in malfunctioning of VIM.

Anyways, Thanks a lot.

---

