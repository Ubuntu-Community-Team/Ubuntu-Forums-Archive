---
title: "How to use &quot;dpkg --configure -a&quot;"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by milan_cortana on 2008-07-26
Hi all,
J break up some upgrades during the installation(my pc restart)
and since then j am getting this notification when try to run 
update or synaptic package manager:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So J run with sudo offcourse:
sudo dpkg --configure -a
and it was ok.System was fixing something or what else it was doing.
But when it came to:
Setting up language-pack-en-base (1:7.10+20080205) ...
Generating locales...
  en_AU.UTF-8... 

it just stuck like this for hours.
J let it work for 5 to 6 hours but it wasnt moving.
J tried again with sudo dpkg --configure -a,
but same process was on again.

Help me please
and make it simple because J am nooby.
Thanks

---

### Post by spiderbatdad on 2008-07-26
perhaps try opening synaptic package manager and choose: Edit>>Fix Broken Packages.

---

### Post by Steve413z on 2008-07-26
I had the same exact problem today!!

reboot and go into recovery mode, goto the command line and login as root
try:
```
apt-get purge locales
```or
```
dpkg --purge locales
```then after thats done
```
apt-get install locales
```
```
dpkg --configure -a
```
note: you may need to play around with it a little bit, I sat and tried to get this to work for like an hour before it finally worked

but basically you need to manage to clear out all the settings from the "locale" package and then reinstall it

weird problem

---

### Post by phidia on 2008-07-26
There are a few [hits]("http://www.google.com/search?q=Setting+up+language-pack-en-base+(1%3A7.10%2B20080205)+...+Generating+locales...+en_AU.UTF-8...&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a") from googling > Setting up language-pack-en-base (1:7.10+20080205) ...
Generating locales...
en_AU.UTF-8...  but I don't if they're that helpful.

you might try "updatedb" or "sudo apt-get --fix-missing" and reboot then run the dpkg command again.

---

### Post by milan_cortana on 2008-07-26
@phidia
Thanks a lot for help.

J did what Steve413z suggested,and it worked(thanks again Steve).

---

