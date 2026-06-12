---
title: "[Perl-base] update problems"
date: 2005-02-19
forum: Repositories &amp; Backports
---

### Post by Carla Winter on 2005-02-19
Hello world!

Recently i've made an upgrade of my warty and i got that:  

```

The following packages will be upgraded:
  perl-base
1 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
3 not fully installed or removed.
Need to get 0B/727kB of archives.
After unpacking 0B of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 151729 files and directories currently installed.)
Preparing to replace perl-base 5.8.4-2ubuntu0.2 (using .../perl-base_5.8.4-2ubuntu0.3_i386.deb) ...
Unpacking replacement perl-base ...
dpkg: error processing /var/cache/apt/archives/perl-base_5.8.4-2ubuntu0.3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/perl/5.8', which is also in package liblockfile-simple-perl
Errors were encountered while processing:
 /var/cache/apt/archives/perl-base_5.8.4-2ubuntu0.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
venus:/var/cache/apt/archives# apt-get install perl-b
perl-base   perl-byacc  
venus:/var/cache/apt/archives# apt-get install perl-base 
Reading Package Lists... Done
Building Dependency Tree... Done
The following packages will be upgraded:
  perl-base
1 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
3 not fully installed or removed.
Need to get 0B/727kB of archives.
After unpacking 0B of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 151729 files and directories currently installed.)
Preparing to replace perl-base 5.8.4-2ubuntu0.2 (using .../perl-base_5.8.4-2ubuntu0.3_i386.deb) ...
Unpacking replacement perl-base ...
dpkg: error processing /var/cache/apt/archives/perl-base_5.8.4-2ubuntu0.3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/perl/5.8', which is also in package liblockfile-simple-perl
Errors were encountered while processing:
 /var/cache/apt/archives/perl-base_5.8.4-2ubuntu0.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i've tried apt-get -f install, apt-get -f install perl-base but nothing worked.
Does somebody have problems like this one?

And does somebody know how to fix it, because i can no longer install new software.

Thanks in advance.


Config: 
Compaq Evo n600c (laptop)
P3m 1.2 w/ speedstep
512 mo 
HDD 30go
Ubuntu warty 4.10 only!

---

### Post by WW on 2005-02-19
It appears that the packages perl-base (version 5.8.4-2ubuntu0.3) and liblockfile-simple-perl (version 0.2.5-4) both install the file /usr/lib/perl/5.8.  I'm no debian expert, but I'm pretty sure This Should Not Happen (tm).  So I think this is a packaging bug.  It appears that this has been fixed in hoary, since I don't see /usr/lib/perl/5.8 in the list of files installed by version 0.2.5-4ubuntu1 of liblockfile-simple-perl.  Unfortunately, that doesn't help you if you are running warty.

I don't know the best way to get around the problem. Let's hope an expert or Ubuntu dev takes notice.

---

