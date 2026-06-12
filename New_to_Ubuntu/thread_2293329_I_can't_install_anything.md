---
title: "I can't install anything"
date: 2015-09-04
forum: New to Ubuntu
---

### Post by Oinos on 2015-09-04
I always get errors for missing files or something and I can't fix that with the suggested commands. This time it was:

> E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

All not-founds;

```
Err http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main mysql-common all 5.5.37-0ubuntu0.13.10.1
  404  Not Found [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com/ubuntu/ saucy/main libdbi-perl i386 1.627-1
  404  Not Found [IP: 91.189.91.23 80]
Err http://security.ubuntu.com/ubuntu/ saucy-security/main mysql-common all 5.5.37-0ubuntu0.13.10.1
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ saucy/main libdbd-mysql-perl i386 4.023-1
  404  Not Found [IP: 91.189.91.23 80]
Err http://security.ubuntu.com/ubuntu/ saucy-security/main libmysqlclient18 i386 5.5.37-0ubuntu0.13.10.1
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main mysql-client-core-5.5 i386 5.5.37-0ubuntu0.13.10.1
  404  Not Found [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com/ubuntu/ saucy/main libterm-readkey-perl i386 2.30-4build4
  404  Not Found [IP: 91.189.91.23 80]
Err http://security.ubuntu.com/ubuntu/ saucy-security/main mysql-client-core-5.5 i386 5.5.37-0ubuntu0.13.10.1
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main mysql-client-5.5 i386 5.5.37-0ubuntu0.13.10.1
  404  Not Found [IP: 91.189.91.23 80]
Err http://security.ubuntu.com/ubuntu/ saucy-security/main mysql-client-5.5 i386 5.5.37-0ubuntu0.13.10.1
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ saucy-security/main mysql-server-core-5.5 i386 5.5.37-0ubuntu0.13.10.1
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ saucy-security/main mysql-server-5.5 i386 5.5.37-0ubuntu0.13.10.1
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ saucy-security/main php5-common i386 5.5.3+dfsg-1ubuntu2.6
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ saucy-security/main php5-mysql i386 5.5.3+dfsg-1ubuntu2.6
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ saucy-security/main php5-cli i386 5.5.3+dfsg-1ubuntu2.6
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ saucy/main libapr1 i386 1.4.8-1ubuntu1
  404  Not Found [IP: 91.189.91.23 80]
Err http://security.ubuntu.com/ubuntu/ saucy-security/main php5-readline i386 5.5.3+dfsg-1ubuntu2.6
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ saucy/main libaprutil1 i386 1.5.2-1
  404  Not Found [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com/ubuntu/ saucy/main libaprutil1-dbd-sqlite3 i386 1.5.2-1
  404  Not Found [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com/ubuntu/ saucy/main libaprutil1-ldap i386 1.5.2-1
  404  Not Found [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main apache2-bin i386 2.4.6-2ubuntu2.2
  404  Not Found [IP: 91.189.91.23 80]
Err http://security.ubuntu.com/ubuntu/ saucy-security/main apache2-bin i386 2.4.6-2ubuntu2.2
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ saucy-security/main apache2-data all 2.4.6-2ubuntu2.2
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ saucy-security/main apache2 i386 2.4.6-2ubuntu2.2
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main apache2-mpm-prefork i386 2.4.6-2ubuntu2.2
  404  Not Found [IP: 91.189.91.23 80]
Err http://security.ubuntu.com/ubuntu/ saucy-security/main apache2-mpm-prefork i386 2.4.6-2ubuntu2.2
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main libapache2-mod-php5 i386 5.5.3+dfsg-1ubuntu2.6
  404  Not Found [IP: 91.189.91.23 80]
Err http://security.ubuntu.com/ubuntu/ saucy-security/main libapache2-mod-php5 i386 5.5.3+dfsg-1ubuntu2.6
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ saucy/main libhtml-template-perl all 2.91-1
  404  Not Found [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main mysql-server all 5.5.37-0ubuntu0.13.10.1
  404  Not Found [IP: 91.189.91.23 80]
Err http://security.ubuntu.com/ubuntu/ saucy-security/main mysql-server all 5.5.37-0ubuntu0.13.10.1
  404  Not Found [IP: 91.189.91.13 80]
Fetched 6,578 B in 4s (1,597 B/s)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-common_5.5.37-0ubuntu0.13.10.1_all.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/libmysqlclient18_5.5.37-0ubuntu0.13.10.1_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdbi-perl/libdbi-perl_1.627-1_i386.deb  404  Not Found [IP: 91.189.91.23 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdbd-mysql-perl/libdbd-mysql-perl_4.023-1_i386.deb  404  Not Found [IP: 91.189.91.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-client-core-5.5_5.5.37-0ubuntu0.13.10.1_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libterm-readkey-perl/libterm-readkey-perl_2.30-4build4_i386.deb  404  Not Found [IP: 91.189.91.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-client-5.5_5.5.37-0ubuntu0.13.10.1_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-server-core-5.5_5.5.37-0ubuntu0.13.10.1_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-server-5.5_5.5.37-0ubuntu0.13.10.1_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.5.3+dfsg-1ubuntu2.6_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-mysql_5.5.3+dfsg-1ubuntu2.6_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.5.3+dfsg-1ubuntu2.6_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-readline_5.5.3+dfsg-1ubuntu2.6_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apr/libapr1_1.4.8-1ubuntu1_i386.deb  404  Not Found [IP: 91.189.91.23 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1_1.5.2-1_i386.deb  404  Not Found [IP: 91.189.91.23 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1-dbd-sqlite3_1.5.2-1_i386.deb  404  Not Found [IP: 91.189.91.23 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1-ldap_1.5.2-1_i386.deb  404  Not Found [IP: 91.189.91.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-bin_2.4.6-2ubuntu2.2_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-data_2.4.6-2ubuntu2.2_all.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2_2.4.6-2ubuntu2.2_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-prefork_2.4.6-2ubuntu2.2_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.5.3+dfsg-1ubuntu2.6_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libh/libhtml-template-perl/libhtml-template-perl_2.91-1_all.deb  404  Not Found [IP: 91.189.91.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-server_5.5.37-0ubuntu0.13.10.1_all.deb  404  Not Found [IP: 91.189.91.13 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

What should I do?

---

### Post by howefield on 2015-09-04
Installing a currently supported version would be the best bet.

Saucy went end of life on July 17th last year, so the repositories get moved to old-releases.

---

### Post by Oinos on 2015-09-04
> **howefield said:**
> Installing a currently supported version would be the best bet.

Saucy went end of life on July 17th last year, so the repositories get moved to old-releases.

Does this mean that if I want to be able to install programs I'll have to go through the trouble of reinstalling my OS twice a year? What are some alternative servers or ways of installing?

---

### Post by howefield on 2015-09-04
If you insist on installing a non LTS (Long Term Support) version, then you will have to upgrade every 9 months, if you want longer support then install an LTS version which gets 5 years of support. The current LTS is 14.04, the next will be 16.04.

You could point your repositories to old-releases and stay on Saucy, but given that it is end of life and will not receive any updates, security or otherwise, it probably wouldn't be a very wise choice.

---

### Post by pfeiffep on 2015-09-04
>>>Does this mean that if I want to be able to install programs I'll have  to go through the trouble of reinstalling my OS twice a year? What are  some alternative servers or ways of installing?

Absolutely not. I suggest installing 14.04 LTS and you'll be good until 2019.

---

### Post by cdh79 on 2015-09-04
as a beginner being in a similar situation (and hoping to not highjack this thread), what's the best way in this situation? 
making sure that "/etc/update-manager/release-upgrades" is set to "lts" and then "do-release-upgrade" ?

---

### Post by yancek on 2015-09-04
> making sure that "/etc/update-manager/release-upgrades" is set to "lts" and then "do-release-upgrade" ? 		

Probably the best but I'm sure it will vary for people.  The only reason for upgrading to a non-LTS that makes sense to me is if something isn't working or you want to try out some new software which isn't available in the current LTS.  Another option is to have your personal data on a separate partition or partitions and do a new install of an LTS to the / partition.

---

### Post by grahammechanical on 2015-09-04
@cdh79 and others who do not know

If we install a Long Term Support version (LTS) then our setttings in Software & Updates will automatically be set to notify us of the next LTS release and only that. If we install what we call an interim release that only has 9 months support then Software & Updates will be set up to automatically notify us of the next release of Ubuntu. We can change these settings. But,

1) if we are on an LTS version then it is best to stay on an LTS version unless we are willing to upgrade every six months.

2) If we are on a 9 months support version then it is best to upgrade to the next version during the 3 month period of overlap between a new release coming out and our version reaching end of life.

We do get notification of new releases based upon the setting in Software & Updates. Each version of Ubuntu has its own software repositories. When a version of Ubuntu reaches end of life its software repositories are closed. The software in those repositories are no longer updated. The repositories are relocated to an archive. That means that the URLs in the lists of software sources are no longer accurate. That is the situation that the Original Poster is in. We can change the URLs to point to the old-releases archive and then access the repositories and upgrade to the next release. Or, we can do a fresh install of a supported version. Some of us think that a fresh install is the better choice.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Regards

---

### Post by miniKOX on 2015-09-04
Hello Oinos. 
As it was told. you can always use old-releases repository, for older, unsupported versions of Ubuntu.

In terminal type:
```

sudo gedit /etc/apt/sources.list

```
and paste there:
```

http://old-releases.ubuntu.com/ubuntu saucy main restricted multiverse security

```

save it, and in terminal type:
```
 sudo apt-get update
```

---

### Post by Geoffrey_Arndt on 2015-09-04
By far the best solution (imho) in this case (as the original poster is using such an old version) is to:
>   Copy/paste your important files to a large SD/USB device or cloud service.   
>   Download latest version of LTS (14.04.3) & burn to DVD or USB Flash-stick.
>   Install 14.04.3 to your system

If you have a sane version of files to save off the device, this entire operation including install can take less than 1.5 hours.    Tweaking your system afterwards can also take another 30 to 60 minutes.

This way, you have a stable, reliable system until April 2019 (unless you want to upgrade to the 2016 LTS (good till 2021 then).
And next time, you'll know better.

---

### Post by Oinos on 2015-09-04
So do I have to format the hard drive, or there's a quicker way once I have Ubuntu?
Could somebody post an ELI5 FAQ on all this stuff about different versions and switching versions and support and differences between versions, et cetera?
And why do I have to change my OS anyway, since it's already fullfilling all my needs, save for these installation troubles?

---

### Post by howefield on 2015-09-04
> **Oinos said:**
> So do I have to format the hard drive, or there's a quicker way once I have Ubuntu?

On my machines I prefer the "nuke and pave" method with a freshly formatted disk/partition but you can easily upgrade from your current 13.10 to the current LTS (14.04) which would give you support till April 2019. From there you can keep it till then or upgrade to 16.04 (the next LTS) when it is released. 

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) explains how to upgrade from an end of life position.

> Could somebody post an ELI5 FAQ on all this stuff about different versions and switching versions and support and differences between versions, et cetera?

Wish I knew what an " ELI5 FAQ" was. 

> And why do I have to change my OS anyway, since it's already fullfilling all my needs, save for these installation troubles?

Well, you don't. You could easily carry on your merry way with an unsupported release, it's your machine and your choice.. You could die long before you get an issue but your first sentence in this thread suggests otherwise... 

> *I always get errors for missing files or something and I can't fix that with the suggested commands. This time it was:*

Your software stays at the current versions and it gets increasingly difficult to install new software and you become increasingly vulnerable to attack.

---

### Post by Yellow Pasque on 2015-09-04
[http://askubuntu.com/a/91821](http://askubuntu.com/a/91821)

---

### Post by cdh79 on 2015-09-05
thank you all very much for the explanation..
that really helped me get a better overall understanding of the release-structure Ubuntu uses :)

---

