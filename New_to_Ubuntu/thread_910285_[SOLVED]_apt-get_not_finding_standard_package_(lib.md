---
title: "[SOLVED] apt-get not finding standard package (libopenssl-ruby)"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by biot023@gmail.com on 2008-09-04
Hi -- I'm having trouble installing libopenssl-ruby.
I use the following command:

 sudo apt-get install libopenssl-ruby

(This was recommended to me when I ran the command passenger-install-apache2-module & it didn't find the openssl package it needed.)

The response I get is:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libopenssl-ruby

Can anyone advise me on what I can do to fix this?
(Bearing in mind I'm a total beginner!)
Cheers,
   Doug.

---

### Post by ronnielsen1 on 2008-09-04
You have to enable the universe repository. Easiest way is in synaptic

---

### Post by Nepherte on 2008-09-04
libopenssl-ruby is in the universe repository. Be sure you have it enabled. There two versions of it: 1.8 and 1.9. Try this:
```
sudo apt-get install libopenssl-ruby1.9
```

---

### Post by ronnielsen1 on 2008-09-04
System > Administration > Synaptic

Once in synaptic go to Settings > Repositories

Click the Universe repository

---

### Post by biot023@gmail.com on 2008-09-04
Hi -- cheers for the responses, there.
I'm afraid the attempt to install 1.9 didn't work, and I've no idea about Synaptic, sorry!
I only have ssh access to the server -- is this still possible through that?
& thanks again,
   Doug.

---

### Post by mlentink on 2008-09-04
Yes.
You should be able to use nano (which is a nice text editor) to edit your etc/apt/sources.lst file.

Try:
```
sudo nano /etc/apt/sources.lst 
```
Try and find the lines with 'universe' in them. There are most likely hash-signs in front of them. Delete those.
Write the changes to disk and eXit the program.

then do:
```
sudo apt-get update
```

after this you should be able to use the command given earlier

---

### Post by biot023@gmail.com on 2008-09-04
Thanks for that -- I've opened it up, and there are no lines which mention universal.
Would you be able to post what yours says, & maybe I could copy that in?
(Would that even work?)
& cheers again for helping out.
   Doug.

---

### Post by oldos2er on 2008-09-04
> **biot023@gmail.com said:**
> Thanks for that -- I've opened it up, and there are no lines which mention universal.
Would you be able to post what yours says, & maybe I could copy that in?
(Would that even work?)
& cheers again for helping out.
   Doug.

 Might be easier to do it graphically: Go to System, Administration, Software Sources, and check off the box for the universe repository. Then reload.

---

### Post by biot023@gmail.com on 2008-09-04
Cheers -- sadly I only have ssh, as this is a virtual server I'm renting a slice of, so I haven't access to any graphical tools.

---

### Post by halitech on 2008-09-04
will it let you do this?
```
cat /etc/apt/sources.list
``` so you can post it here so we can see what might need to be done?

---

### Post by Nepherte on 2008-09-04
This is the list with universe, multiverse, security and backports repositories enabled. You can disable the last four entries if you like. They aren't really necessary.
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse

##deb http://archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse
##deb-src http://archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.)
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
```

---

### Post by biot023@gmail.com on 2008-09-04
Sure thing:

<sources.list>
#
#  /etc/apt/sources.list
#

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

</sources.list>

Cheers,
   Doug.

---

### Post by halitech on 2008-09-04
ok, use this from post 3
```
sudo nano /etc/apt/sources.lst
``` to add ```
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe
```
then do ```
sudo apt-get update
```
and then try to install the lib again

---

### Post by biot023@gmail.com on 2008-09-04
Bingo!
That's absolutely fantastic, thanks!
   Doug.

---

### Post by halitech on 2008-09-04
~sits back, pops a beer, lights a smoke and polishes my nails on my shirt~ all in a days work and glad we got you working.  Don't forget to mark the thread solved so others will know as well.

---

### Post by mlentink on 2008-09-04
Thanks dude!
Seeing as how you did all the work 'n all!

---

