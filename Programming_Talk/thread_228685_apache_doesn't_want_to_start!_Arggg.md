---
title: "apache doesn't want to start! Arggg"
date: 2006-08-03
forum: Programming Talk
---

### Post by careca on 2006-08-03
i do:
**sudo apache2ctl -k restart**

and says:
**httpd not running, trying to start**

but it really doesn't start. I check going to 'ubuntu' (my 'localhost').

Previously I edited apache2.cong but apache2ctl configtest said Syntax OK.

---

### Post by ifokkema on 2006-08-04
> **careca said:**
> i do:
**sudo apache2ctl -k restart**

and says:
**httpd not running, trying to start**

but it really doesn't start. I check going to 'ubuntu' (my 'localhost').

Previously I edited apache2.cong but apache2ctl configtest said Syntax OK.

Try the Debian/Ubuntu way:
```
sudo /etc/init.d/apache2 start
```
or
```
sudo /etc/init.d/apache2 restart
```

---

### Post by careca on 2006-08-04
```
root@ubuntu:~# sudo /etc/init.d/apache2 start
 * Starting apache 2.0 web server...                           [fail]
```

Mmm... i don't know what's wrong...

I can't know! There is no error log, nothing...

---

### Post by scxtt on 2006-08-04
you should have something like:

```
scxtt@madiera.kubuntu [/var/log/apache2]
:> ll
total 12K
-rw-r----- 1 root adm 6.1K 2006-07-28 21:14 access.log.1
-rw-r----- 1 root adm 3.6K 2006-07-28 21:16 error.log.1
-rw-r----- 1 root adm    0 2006-07-30 06:06 access.log
-rw-r----- 1 root adm    0 2006-07-30 06:06 error.log
```

---

### Post by careca on 2006-08-04
Mmmm... now says something:

```
[Fri Aug 04 11:54:52 2006] [error] Can't locate Apache/Registry.pm in @INC (@INC contains: /home/netreg/lib /usr/ng/lib/perl5 /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /etc/apache2) at /home/netreg/lib/startup.pl line 47.\nBEGIN failed--compilation aborted at /home/netreg/lib/startup.pl line 47.\nCompilation failed in require at (eval 2) line 1.\n
[Fri Aug 04 11:54:52 2006] [error] Can't load Perl file: /home/netreg/lib/startup.pl for server ubuntu.localdomain:0, exiting...

```

Now i remember, i put this in apache2.conf:
```

<Files ~ "\.pl">
 SetHandler perl-script
 PerlResponseHandler ModPerl::RegistryPrefork
 Options +ExecCGI
</Files>

```

but i know that ModPerl... is in the system:
```
cpan> install ModPerl::RegistryPrefork
ModPerl::RegistryPrefork is up to date (0.01).

cpan> install ModPerl::Registry
ModPerl::Registry is up to date (1.99).

```

---

### Post by slakkie on 2006-08-04
Check you apache config to see wheter you load mod_perl.

---

### Post by ifokkema on 2006-08-04
Strangely, I find that libapache-mod-perl provides usr/lib/perl5/Apache/Registry.pm, but the libapache2-mod-perl2 doesn't. But the description of libapache2-mod-perl2 says: 

```
 mod_perl allows the use of Perl for just about anything
 Apache-related, including <Perl> sections in the config
 files and the famous Apache::Registry module for caching
 compiled scripts.
```

Also, I would make sure it's this problem that's keeping Apache from starting by commenting the part in the config file, and trying again, just to be sure you're chasing the right thing...

---

### Post by careca on 2006-08-04
I've installed mod_perl2, because i've got apache2.

I found a document on internet that says Apache::Registry must be replaced with ModPerl::Registry in apache2+mod_perl2. That's why i changed the line.

(I'm sure start.pl exists. I'll try to change permissions but I don't thing is there the problem)

---

### Post by careca on 2006-08-04
> **slakkie said:**
> Check you apache config to see wheter you load mod_perl.

I'm sure mod_perl2 is loaded

---

### Post by ifokkema on 2006-08-04
> **careca said:**
> I've installed mod_perl2, because i've got apache2.
I know, but my point is, that libapache-mod-perl provides /usr/lib/perl5/Apache/Registry.pm and libapache2-mod-perl2 provides /usr/lib/perl5/ModPerl/Registry.pm.
That's strange, because the files differ in directory name, and although you seem to have changed the Apache config to look for the libapache2-mod-perl2 file, it searches for the libapache-mod-perl file...

I guess it's fixed after installing libapache-mod-perl although that seems like a strange hack...

---

### Post by careca on 2006-08-04
I found the problem, but...

startup.pl was asking for old Registry:
```
use strict;

use lib "/usr/ng/lib/perl5";
use lib "/home/netreg/lib";

$ENV{GATEWAY_INTERFACE} =~ /^CGI-Perl/ or die "GATEWAY_INTERFACE not perl!";
[B]
use Apache::Registry();[/B]

use CGI (); 
#CGI->compile(':all');
use CGI::Carp ();
use DBI;
use DBD::mysql;
use CMU::Netdb;
use CMU::WebInt;

1;
/CODE]

I have now another error message:
[CODE][Fri Aug 04 15:57:14 2006] [error] GATEWAY_INTERFACE not perl! at /home/netreg/lib/startup.pl line 45.\nCompilation failed in require at (eval 2) line 1.\n
[Fri Aug 04 15:57:14 2006] [error] Can't load Perl file: /home/netreg/lib/startup.pl for server ubuntu.localdomain:0, exiting...

```




it is safe to use Apache modules with Apache2?

---

### Post by ifokkema on 2006-08-04
> **careca said:**
> I found the problem, but...

startup.pl was asking for old Registry:
Where is that startup.pl from? I found these possible packages:
libapache-dbi-perl: usr/share/doc/libapache-dbi-perl/examples/startup.pl
scoop: usr/share/scoop/etc/startup.pl

My guess is it's libapache-dbi-perl, which seems to handle both Apache 1.3.X and Apache 2. Possibly, this problem you're having is a bug in one of these packages.

> **careca said:**
> it is safe to use Apache modules with Apache2?
Well, it can't get any worse, can it? :)

---

