---
title: "Install LWP::CURL"
date: 2014-12-23
forum: New to Ubuntu
---

### Post by unreal2 on 2014-12-23
Hi,

I try install.

```
wget http://search.cpan.org/CPAN/authors/id/G/GA/GAAS/libwww-perl-6.05.tar.gz
tar xzf libwww-perl-6.05.tar.gz
cd libwww-perl-6.05/
perl Makefile.PL 
make
sudo make install
```
result OK
or

```
perl -MCPAN -e 'install Bundle::LWP'
```
result OK
or

```
perl -MCPAN -e 'install LWP::Curl'
(....................)
 =  0.30 CPU)
Result: FAIL
Failed 5/8 test programs. 1/4 subtests failed.
make: *** [test_dynamic] B&#322;&#261;d 2
  LORN/LWP-Curl-0.12.tar.gz
2 dependencies missing (WWW::Curl::Easy,Test::Exception); additionally test harness failed
  /usr/bin/make test -- NOT OK
//hint// to see the cpan-testers results for installing this module, try:
  reports LORN/LWP-Curl-0.12.tar.gz
Running make install
  make test had returned bad status, won't install without force
Could not read metadata file. Falling back to other methods to determine prerequisites
```

But still not work.

```
ad@pc:~/work/sk$ ./b.pl
Can't locate LWP/Curl.pm in @INC (you  may need to install the LWP::Curl module) (@INC contains: /etc/perl  /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5  /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18  /usr/local/lib/site_perl .) at ./b.pl line 6.
BEGIN failed--compilation aborted at ./b.pl line 6.

```


What is the Reason ??

---

### Post by schragge on 2014-12-23
*WWW::Curl* and *Test::Exception* are packaged for Ubuntu as [libwww-curl-perl]("http://packages.ubuntu.com/trusty/libwww-curl-perl") and [libtest-exception-perl]("http://packages.ubuntu.com/trusty/libtest-exception-perl"), respectively.

Just install them with
```
sudo apt-get install lib{www-curl,test-exception}-perl
```
BTW, this is the standard naming scheme for packages containing perl modules on Debian-based distributions: **WWW::Curl** > lib**www-curl**-perl, **Test::Exception** > lib**test-exception**-perl and so on.

---

### Post by unreal2 on 2014-12-23
Thanks, but i need install lwp::curl and   is probably not the same www::curl ? Yes?

---

### Post by schragge on 2014-12-23
Sure, it's not the same. But it **depends** on WWW::Curl and Test::Exception having been installed.

---

### Post by unreal2 on 2014-12-23
if I well understand.
I can't install lwp :: curl on ubuntu? 
instead it is www::curl available.

---

### Post by schragge on 2014-12-23
No. LWP::Curl is not available in Ubuntu repository, you should install it from CPAN. But to do so, you should first
```

sudo apt-get install lib{www-curl,test-exception}-perl

```
because these are **dependencies** of LWP::Curl. Please read [uhelp]community/InstallingSoftware#Package_Dependencies[/uhelp]

---

### Post by unreal2 on 2014-12-23
thanks for your  patience. now i understand

---

