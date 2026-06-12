---
title: "perl script and class.pm file location"
date: 2008-04-18
forum: Programming Talk
---

### Post by GoliathWest on 2008-04-18
I am trying to run a perl script from the command line but received the following error:

Can't locate Path/Class.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at fasta2match.pl line 15.

Do I need to copy the class.pm file or class directory into my file system instead of the location it is in after the software was extracted to its current location?

Thanks!

---

### Post by siouzi on 2008-04-18
The script needs the Path::Class module and it is not installed in the default locations in your system. You could install the module using cpan, but in this case I think it may be better to use Ubuntu's package management:
```
sudo apt-get install libpath-class-perl
```

---

### Post by GoliathWest on 2008-04-18
Siouzi,

Fantastic, that installed in an instant and the perl script ran.

---

