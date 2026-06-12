---
title: "Install instructions?"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by KenFF on 2012-03-18
Hi, 

I feel a bit stupid but I am trying to install on an Acer Netbook alongside Win XP. I started this some weeks ago and got sidetracked. I had partitioned my disc and thought I was good to go. 

Now when I try to install, it comes up with an error saying that it cannot install on this drive - maybe because there are too many primary partitions!!

Yes, the drive has a C: and also a "PQSERVICE" partition (also a "primary"), which is the windows checkpoint/restore partition. It also has a logical drive of 45GB Fat32 which is empty.

I was reading some documentation when I was doing this last but I can't seem to find it.

Can anyone just point me in the right direction? Like I say, I feel a bit stupid but I have been going round in circles all afternoon!

---

### Post by HeroOfCanton on 2012-03-18
The maximum number of partitions allowed on a drive is 4 due to the way the MBR is structured.

If you're trying to put on a 5th you will encounter errors. If that blank FAT32 one is not in use you can convert it to ext and install linux there.

---

### Post by KenFF on 2012-03-18
I was searching here for instructions! All I had to do was "Google it"!:confused:

I deleted the spare partition and set up a new one 10 GB smaller. That seems to have done the trick. Ubuntu seems to be installing somewhere?? and I am hoping that it is on the 10 GB free space!!):P

---

### Post by Rodney9 on 2012-03-18
Welcome.

Help Guide to Ubuntu Oneiric version 11.10

[http://ubuntuguide.org/wiki/Ubuntu_Oneiric](http://ubuntuguide.org/wiki/Ubuntu_Oneiric)

Linux is Not Windows

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Very good pictorial Install Guide

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

10 Things to after Installing Ubuntu

[http://www.omgubuntu.co.uk/2011/10/1...-ubuntu-11-10/](http://www.omgubuntu.co.uk/2011/10/1...-ubuntu-11-10/)


Rodney

---

### Post by KenFF on 2012-03-18
Wow, Thanks Man.

I've wanted to get off Windows for 20 years!! Just recently realized that I can convert my NetBook! My Desktop is a whole different kettle of fish! But it's next\\:D/

---

### Post by anewguy on 2012-03-18
And remember - it's not 4 total partitions, it's 4 PRIMARY partitions.  You can create extended (logical) paritions within those.

Dave

---

