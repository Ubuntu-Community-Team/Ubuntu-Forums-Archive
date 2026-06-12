---
title: "Warty upgrade fails with error message"
date: 2005-01-22
forum: Repositories &amp; Backports
---

### Post by Lachlan on 2005-01-22
Hi, Initially I had some trouble with my /etc/apt/sources.list,so I copied a list from a previous posting.
Ran apt-get update from root terminal,ok.Ran apt-get upgrade,ok.As I am on dial up and the download was going to take 6 – 7 hours I cancelled the download after about 5 minutes,planning to run it again very early on the following morning.Performed another apt-get update,then ran apt-get upgrade and it just hung on me.Closed down the root terminal and fired up Synaptic ending up with the same result.Cancelled upgrade and this error message appeared.

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/shadow/login_4.0.3-28.5ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/shadow/login_4.0.3-28.5ubuntu6.1_i386.deb)
  

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.8.4-2ubuntu0.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.8.4-2ubuntu0.2_all.deb)
  

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.3.2.ds1-13ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.3.2.ds1-13ubuntu2.2_i386.deb)
  

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/glibc/locales_2.3.2.ds1-13ubuntu2.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glibc/locales_2.3.2.ds1-13ubuntu2.2_all.deb)
  

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.3.2.ds1-13ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.3.2.ds1-13ubuntu2.2_i386.deb)
  

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.3.2.ds1-13ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.3.2.ds1-13ubuntu2.2_i386.deb)
  

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.4-2ubuntu0.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.4-2ubuntu0.2_i386.deb)
  

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.4-2ubuntu0.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.4-2ubuntu0.2_i386.deb)
  

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-base_5.8.4-2ubuntu0.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-base_5.8.4-2ubuntu0.2_i386.deb)
  

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xfree86/libice6_4.3.0.dfsg.1-6ubuntu25.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xfree86/libice6_4.3.0.dfsg.1-6ubuntu25.1_i386.deb)
  

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cdrtools/cdrecord_2.0+a30.pre1-1ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cdrtools/cdrecord_2.0+a30.pre1-1ubuntu3_i386.deb)
  

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.0.2-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.0.2-0ubuntu3_i386.deb)
  

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cdrtools/mkisofs_2.0+a30.pre1-1ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cdrtools/mkisofs_2.0+a30.pre1-1ubuntu3_i386.deb)
  
Could not download all package files

The version of the package that you want to install might be no longer available in the repository. Or there might be problems with the source of the package. Refresh the package list and check the source of the package (e.g. CD or network connection).

Cheers

Lachlan

---

### Post by mendicant on 2005-01-23
This just sounds like a connection error during the update process.

---

### Post by Lachlan on 2005-01-23
Thanks for the reply,it looks as though you are right.I tried the upgrade process 5 minutes ago and it worked just fine.

Lachlan

---

