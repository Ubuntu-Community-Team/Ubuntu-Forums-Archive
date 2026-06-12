---
title: "Install Java JRE from CLI"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by blx_286 on 2008-04-25
I am in need of some help. I would like to setup and test a product called SysAid. I have a server install of Dapper running on an old Dell PowerEdge 2650.

The SysAid instructions say I need to download and install Java JRE 1.5 or above and Tomcat. Could someone please tell me how to download and install Java from the CLI? I did a search in Aptitude and found Tomcat, but I didn't see a Java package that looked like a JRE 1.x.

Thanks,
Tim

---

### Post by kpkeerthi on 2008-04-25
The package name is sun-java5-jre

---

### Post by SOULRiDER on 2008-04-25
That means what you need to do is type:
```
sudo aptitude update
sudo aptitude install sun-java5-jre
```

---

### Post by blx_286 on 2008-04-25
Thanks for the quick reply guys. This is what I am getting from Aptitude:

```
sudo aptitude install sun-java5-jre
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "sun-java5-jre"
The following packages have been kept back:
  apache2 apache2-common apache2-mpm-prefork apache2-utils bind9-host bzip2 
  dnsutils libapr0 libbind9-0 libbz2-1.0 libdns21 libisc11 libisccc0 
  libisccfg1 libkrb53 liblwres9 libmysqlclient15off libpcre3 libxml2 
  linux-backports-modules-2.6.15-51-server linux-image-2.6.15-51-server 
  locales mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 
  python2.4 python2.4-minimal 
0 packages upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

---

### Post by kpkeerthi on 2008-04-25
This package is in multiverse repository. There is a how-to here
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by zvacet on 2008-04-25
Do you have all repos open? If not add this line to your source list 

```
sudo nano /etc/apt/sources.list
```

and add 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse

Crtl+o>enter>ctrl+x

```
sudo apt-get update
```

and then 

```
sudo aptitude install sun-java5-bin, sun-java5-jre
```

---

### Post by blx_286 on 2008-04-25
There was no multiverse entry in the sources.list, got it now.

Thanks guys.

---

### Post by stchman on 2008-04-25
> **blx_286 said:**
> I am in need of some help. I would like to setup and test a product called SysAid. I have a server install of Dapper running on an old Dell PowerEdge 2650.

The SysAid instructions say I need to download and install Java JRE 1.5 or above and Tomcat. Could someone please tell me how to download and install Java from the CLI? I did a search in Aptitude and found Tomcat, but I didn't see a Java package that looked like a JRE 1.x.

Thanks,
Tim

This will give you the complete Java package.

```

sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin
```

This will include the borwser plugin as well.  If you prefer Java 1.6 over 1.5 then sub 6 for 5 in the above statement.

---

### Post by quixote on 2009-02-05
I run 64-bit Intrepid and supposedly have java, jvm, jre, whatever, installed.  (I used the excellent instructions here: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) on how to get all the multimedia stuff working.)  At least synaptic says both sun-java6-bin and sun-java6-jre are installed.  I don't have sun-java6-plugin.   so I tried the following:```
sudo apt-get -y -f install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
``` figuring that would fix anything that might be broken and get the plugin part I was missing.

But I get this error message:  Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

So what's the deal?  What is it with Sun, never having an install that just works?  They probably do more, singlehandedly, to put people off Linux than anybody.  Grrr.  grump, grump, grump.

Anyway, any help will be much appreciated!

---

### Post by quixote on 2009-02-05
Oops.  I just noticed that this thread is from April of last year!  I'll try to find a more recent one for my grump.

---

