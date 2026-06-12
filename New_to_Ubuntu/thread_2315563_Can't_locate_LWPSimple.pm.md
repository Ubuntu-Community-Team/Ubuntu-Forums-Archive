---
title: "Can't locate LWP/Simple.pm"
date: 2016-02-29
forum: New to Ubuntu
---

### Post by Dimmizer on 2016-02-29
Hello Ubuntu Community,

I'm currently running a Ubuntu 14.04 VPS which is running a TeamSpeak 3 server. I've come into a bit of trouble trying to run a perl mod called rbmod located here [http://addons.teamspeak.com/directory/addon/miscellaneous-tools/rbMod-Perl-Modification.html](http://addons.teamspeak.com/directory/addon/miscellaneous-tools/rbMod-Perl-Modification.html)

I've configured/followed the instructions in the readme but when I try to start the script I receive an error as shown below.

[ATTACH=CONFIG]267582[/ATTACH]

I've Google the error and saw I could update perl or use cpan but none of those worked. I've come here to see if I could have any better luck. Thanks for your time in reading this and I look forward to feedback :D.

---

### Post by jim_deadlock on 2016-02-29
```
sudo apt-get install cpan
sudo cpan LWP::Simple
```

Try that and if you get any errors during installation post them here.

---

### Post by Dimmizer on 2016-02-29
> **jim_deadlock said:**
> ```
sudo apt-get install cpan
sudo cpan LWP::Simple
```

Try that and if you get any errors during installation post them here.

root@localhost:~# sudo apt-get install cpan
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package cpan
root@localhost:~#

---

### Post by jim_deadlock on 2016-02-29
Actually cpan should already be installed as part of perl, so just try:

```
sudo cpan LWP::Simple
```

---

### Post by Dimmizer on 2016-02-29
> **jim_deadlock said:**
> Actually cpan should already be installed as part of perl, so just try:

```
sudo cpan LWP::Simple
```

root@localhost:~# sudo apt-get install cpan
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package cpan
root@localhost:~# ^C
root@localhost:~# sudo cpan LWP::Simple
Going to read '/root/.cpan/Metadata'
  Database was generated on Fri, 26 Feb 2016 02:41:02 GMT
Running install for module 'LWP::Simple'
Running make for E/ET/ETHER/libwww-perl-6.15.tar.gz
Fetching with HTTP::Tiny:
[http://mirror.uoregon.edu/CPAN/authors/id/E/ET/ETHER/libwww-perl-6.15.tar.gz](http://mirror.uoregon.edu/CPAN/authors/id/E/ET/ETHER/libwww-perl-6.15.tar.gz)
Checksum for /root/.cpan/sources/authors/id/E/ET/ETHER/libwww-perl-6.15.tar.gz o                                                  k
Uncompressed /root/.cpan/sources/authors/id/E/ET/ETHER/libwww-perl-6.15.tar.gz s                                                  uccessfully
Using Tar:/bin/tar xf "libwww-perl-6.15.tar":
Couldn't untar libwww-perl-6.15.tar
Package seems to come without Makefile.PL.
  (The test -f "/root/.cpan/build/ETHER-PtTWbt/Makefile.PL" returned false.)
  Writing one on our own (setting NAME to LWPSimple)
  Had problems unarchiving. Please build manually
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
root@localhost:~#

---

### Post by jim_deadlock on 2016-02-29
In these situations I usually copy/paste the error line into google. In this case I found the following possible solution:

"What solved it for me was simply **rebooting the system"**

---

### Post by Dimmizer on 2016-02-29
> **jim_deadlock said:**
> In these situations I usually copy/paste the error line into google. In this case I found the following possible solution:

"What solved it for me was simply **rebooting the system"**

I shall try :D lol

---

### Post by Dimmizer on 2016-02-29
I rebooted and still the same problems =/


root@localhost:~# sudo cpan LWP::Simple
Going to read '/root/.cpan/Metadata'
  Database was generated on Fri, 26 Feb 2016 02:41:02 GMT
Running install for module 'LWP::Simple'
Running make for E/ET/ETHER/libwww-perl-6.15.tar.gz
Checksum for /root/.cpan/sources/authors/id/E/ET/ETHER/libwww-perl-6.15.tar.gz o                                      k
Uncompressed /root/.cpan/sources/authors/id/E/ET/ETHER/libwww-perl-6.15.tar.gz s                                      uccessfully
Using Tar:/bin/tar xf "libwww-perl-6.15.tar":
Couldn't untar libwww-perl-6.15.tar
Package seems to come without Makefile.PL.
  (The test -f "/root/.cpan/build/ETHER-TQ6jBx/Makefile.PL" returned false.)
  Writing one on our own (setting NAME to LWPSimple)
  Had problems unarchiving. Please build manually
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install

---

### Post by jim_deadlock on 2016-02-29
From what I've seen on google it seems that this kind of thing is associated with lack of RAM, hence the rebooting solution. You could try installing Archive::Tar to give it an alternative to the system tar but apart from that I'm out of ideas. I have Ubuntu Server 15.10 running in a VM with 2G of allocated RAM, I just ran sudo cpan LWP::Simple and it installed no problem.

```
sudo cpan Archive::Tar
```

---

### Post by Dimmizer on 2016-02-29
=/ kay I only have 256mb on the VM cause it's just a small hosting to run a teamspeak server.. It was $5 lol.

---

### Post by Dimmizer on 2016-03-01
Hours later and I still have nothing =/

Been at this all day trying to figure it out :( is anyone else out there who might have ideas?


I updated to a fresh install of 14.04 instead of 12.04 and still no advil I'm going crazy because this thing won't work.


Basically if I'm right.. I'm missing the LWP::Simple module and maybe even the Bundle::LWP but anytime I try to cpan install Bundle::LWP or Simple it can't seem to make the installs and fails.

---

### Post by Dimmizer on 2016-03-01
Was missing

[COLOR=#000000]apt[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000088]get[/COLOR][COLOR=#000000] install libwww[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]perl

lololol, thanks for all who helped.[/COLOR]

---

