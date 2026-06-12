---
title: "Repo connection refused"
date: 2006-04-24
forum: Repositories &amp; Backports
---

### Post by LeTon on 2006-04-24
Fresh install yesterday....connection refused:confused: 
Anyyone???Can not even update-this is what I get:
[B]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.5.2-0ubuntu8_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.5.2-0ubuntu8_all.deb)
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2a_3.5.2-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2a_3.5.2-0ubuntu8_i386.deb)
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-bin_3.5.2-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-bin_3.5.2-0ubuntu8_i386.deb)
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/p/privoxy/privoxy_3.0.3-5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/p/privoxy/privoxy_3.0.3-5_i386.deb)
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)


[/B]
Sorces list is as follows:
# 
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060329.1)]/ dapper main restricted


# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060329.1)]/ dapper main restricted

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) dapper main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) dapper main

Tnx

---

### Post by SgtDude on 2006-04-28
Wow, that one's wierd...

The "localhost:8080" is your machine.  I'm not sure why it's trying to connect to that...

What's your network situation?  i.e. are you at home running through a cable/dsl modem?  At work running through a corporate network?  Give us some more details and we might be able to come up with a solution.

---

### Post by CheshireMac on 2008-09-15
Same problem, different computer, different situation, methinks.
I'm living on residence at university. The network here is a shared network and has some pretty harsh restrictions. Not sure if that would have any bearing on Aptitude though.
I'm running on a fresh install of Hardy, installed yesterday (again), and all I want to do is set up my dual monitor. 
I can't seem to do any work regarding the repos, and it's the same sad story all over again. Every time I do a fresh install, I get these errors and I never seem to know why. 
I desperately need this computer now more than ever . . . education and all that jazz.
Any help would be greatly appreciated. Thanks. :)

---

