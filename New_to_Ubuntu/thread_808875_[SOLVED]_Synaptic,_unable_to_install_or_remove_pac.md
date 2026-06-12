---
title: "[SOLVED] Synaptic, unable to install or remove packages"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by rabidninjawombat on 2008-05-26
Ok this started yesterday.. i installed the kubuntu-desktop package because i wanted to try KDE,  decided i didnt like it and wanted to stick with Gnome. 

I uninstalled the packages and they all seemed to go away smoothly enough, except for one which appears to be causing the trouble. 

kio-umountwrapper

Anytime i attempt to install anything via Synaptic or Apt i get the error:

```
E: kio-umountwrapper: subprocess post-removal script returned error exit status 2
```

Full error if it helps any 

```
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

There doesnt appear to be a way to be able to have apt or synaptic ignore this package so i can isntall something else. It always attempts to remove this one first. 

Thanks for any help :)

---

### Post by rampageoberon on 2008-05-26
I've gotten that error once when I killed an installation of a package.

try the following (may need to do it a few times)

```
sudo aptitude -f install kio-umountwrapper
```

Hope that works

Edit: If you want to remove it after its fixed the thing use

```
sudo aptitude purge kio-umountwrapper
```

---

### Post by rabidninjawombat on 2008-05-26
thanks for the input.... the only thing is if i use 

```
sudo aptitude -f install kio-umountwrapper
```

it wants to install a bunch of dependencies i dont need... 

will the purge command remove those as well?

---

### Post by rabidninjawombat on 2008-05-27
ok update.  i follow the directions above  and i recieved the same error upon attempting 

```
sudo aptitude purge kio-umountwrapper
```  

:(

---

### Post by Paqman on 2008-05-27
> **rabidninjawombat said:**
> 
will the purge command remove those as well?

Yep, because you're using "aptitude" it'll remember the dependencies and remove them if they're not needed. That's the main advantage of aptitude over apt-get.

---

### Post by rabidninjawombat on 2008-05-27
> **Paqman said:**
> Yep, because you're using "aptitude" it'll remember the dependencies and remove them if they're not needed. That's the main advantage of aptitude over apt-get.


Thanks.. it did indeed remember the dependencies... but i am still unable to remove the package. :(  same error as posted above. 

```
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

---

### Post by rabidninjawombat on 2008-05-27
any feedback would be much appreciated.

---

### Post by rabidninjawombat on 2008-05-27
Hrrrm i found that by restarting it will clear synaptic. so i can install and remove packages again, but the kio-umountwrapper is still there. and still giving me the same error as above if i try to purge it. 

So the problem is partially fixed.. would still like to remove this package if it is unneeded.

---

### Post by Paqman on 2008-05-27
Hmm, try:
```

sudo aptitude remove -f kio-umountwrapper

```

---

### Post by rabidninjawombat on 2008-05-27
> **Paqman said:**
> Hmm, try:
```

sudo aptitude remove -f kio-umountwrapper

```


That removed all off the dependencies, but still get that error when it get to the package in question. 

```

erron@erron-desktop:~$ sudo aptitude remove -f kio-umountwrapper
[sudo] password for erron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  kdelibs-data kdelibs4c2a libakode2 libarts1-akode libarts1c2a libartsc0 
  libavahi-qt3-1 liblua50 liblualib50 libqt3-mt 
The following packages will be REMOVED:
  kio-umountwrapper 
0 packages upgraded, 0 newly installed, 11 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 72.3MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 134516 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Removing kdelibs4c2a ...
Removing kdelibs-data ...
Removing libarts1-akode ...
Removing libakode2 ...
Removing libarts1c2a ...
Removing libartsc0 ...
Removing libavahi-qt3-1 ...
Removing liblualib50 ...
Removing liblua50 ...
Removing libqt3-mt ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

I imagine i can just restart now and leave the package installed, then i should be able to install and remove via synaptic just fine.. as long as leaving that package around wont affect anything.

---

### Post by Paqman on 2008-05-27
> **rabidninjawombat said:**
> as long as leaving that package around wont affect anything.

Can't see why it would. If you're never using it the only issue is that it's taking up real estate on your hard drive. But hey, storage is cheap.

---

### Post by rabidninjawombat on 2008-05-28
> **Paqman said:**
> Can't see why it would. If you're never using it the only issue is that it's taking up real estate on your hard drive. But hey, storage is cheap.

Sorry to bump my own thread,  but it looks like this is still causing problems after all. I am still unable to uninstall that package and it is causing Update Manage 

Saying i can only do a partial upgrade do to the package no uninstalling correctly, :(

---

### Post by bboyhobbit on 2008-06-25
hey!

after a a bit of trouble (and a hell of a lot of googling) i finally found a fix to this problem.  Do the following from a terminal:

bboyhobbit@ubuntu:~$ sudo mkdir -p /usr/share/apps/d3lphin/servicemenus
bboyhobbit@ubuntu:~$ sudo touch /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop
bboyhobbit@ubuntu:~$ sudo apt-get remove kio-umountwrapper

worked for me!! hope it works for everyone else.  Credit goes [to this page]("https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729") for the fix

---

### Post by winfree on 2008-06-28
> **bboyhobbit said:**
> hey!

after a a bit of trouble (and a hell of a lot of googling) i finally found a fix to this problem.  Do the following from a terminal:

bboyhobbit@ubuntu:~$ sudo mkdir -p /usr/share/apps/d3lphin/servicemenus
bboyhobbit@ubuntu:~$ sudo touch /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop
bboyhobbit@ubuntu:~$ sudo apt-get remove kio-umountwrapper

worked for me!! hope it works for everyone else.  Credit goes [to this page]("https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729") for the fix
Hi bboyhobbit, Thanks for posting your findings!
I followed your last suggestion and it worked for me too, however, I had to change from  '.../d3lphin/...' to '.../dolphin/...'

---

### Post by dougmorin on 2008-07-18
Awesome, thanks so much for finding the problem.  This error has been plaguing me as well for a little bit now.  

I love having a community to rely on, this rocks.

:guitar:

---

### Post by xithilinx on 2008-08-01
> **bboyhobbit said:**
> hey!

after a a bit of trouble (and a hell of a lot of googling) i finally found a fix to this problem.  Do the following from a terminal:

bboyhobbit@ubuntu:~$ sudo mkdir -p /usr/share/apps/d3lphin/servicemenus
bboyhobbit@ubuntu:~$ sudo touch /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop
bboyhobbit@ubuntu:~$ sudo apt-get remove kio-umountwrapper

worked for me!! hope it works for everyone else.  Credit goes [to this page]("https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729") for the fix

You are the best!!! Agh I just searched everywhere for this problem... and finally found this post. Wow that sucked, :lolflag:

---

