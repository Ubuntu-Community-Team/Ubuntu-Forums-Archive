---
title: "VMWare Server problems"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Jim_in_Germany on 2008-04-26
Hi,

I updated from Gutsy to Hardy and tried to reinstall VMWares server (ran great under Gutsy).

I tried to install it by following the instractions here:
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

In Gutsy it was available in the repositries.

Anyway in Hardy, the instalation process terminates with:


Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

Can anyone help.
Why isn't it working?

Cheers muchly.

---

### Post by Jim_in_Germany on 2008-04-26
I solved my own problem.
I used a different method to install the VMware server.
Here is the full post:
[http://ubuntuforums.org/showthread.php?p=4700821&posted=1#post4700821](http://ubuntuforums.org/showthread.php?p=4700821&posted=1#post4700821)

Here is the summary of what worked for me:

step 1 ) sudo bash ( note sudo su always exits for some reason )
step 2 ) apt-get install build-essential
step 3 ) download vmware-server 1.0.5.tar.gz
step 4 ) extract it to the desktop
step 5 ) go to [http://groups.google.com/group/vmker...es/files?hl=en](http://groups.google.com/group/vmker...es/files?hl=en) and download patch 116 ( i did not get the wireless bridge one but it should work also )

step 6 ) extract the patch to desktop
step 7 ) cd Desktop/vmware-server-distrib
step 8 ) ./vmware-install.pl Keep all the defaults and do everything until it asks if you want to compile the kernel then say no ( if you say yes it is not that big of a deal it will just fail )

step 9 ) cd ../vmware-any-any-update116/
step 10 ) ./runme.pl make sure to say yes to compile kernel and follow defaults

*** This is the step i had trouble finding ***
step 11 )
cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/
cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/

---

### Post by handband2 on 2008-04-26
If you are still having problems installing vmware-server, Martti Kuparinen has a great howto:

**VMware Server Installation - hardy heron - 8.04**
[http://users.piuha.net/martti/comp/u...en/server.html](http://users.piuha.net/martti/comp/u...en/server.html)

---

