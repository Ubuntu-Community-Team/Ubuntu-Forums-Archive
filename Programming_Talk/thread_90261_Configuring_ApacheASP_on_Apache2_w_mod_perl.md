---
title: "Configuring Apache::ASP on Apache2 w/ mod_perl"
date: 2005-11-14
forum: Programming Talk
---

### Post by pokeroo on 2005-11-14
I installed apache2 (2.0.54-5ubuntu2) and mod_perl 2.0.1-3 under Kubuntu (Breezy Badger). These were done using the packages from [http://packages.ubuntu.com](http://packages.ubuntu.com).

I copied the following settings from [http://www.apache-asp.org/config.html](http://www.apache-asp.org/config.html)  into /etc/apache2/apache2.conf and restarted Apache:

PerlModule  Apache::ASP
 <Files ~ (\.asp)>    
   SetHandler  perl-script
   PerlHandler Apache::ASP
   PerlSetVar  Global .
   PerlSetVar  StateDir /tmp/asp
 </Files>

I have setup User directories under public_html and public_html/cgi-bin is setup for CGI.

Now when I put index.asp into public_html I get the following in /var/log/apache2/error.log:

[Mon Nov 14 14:12:41 2005] [error] [client 64.7.136.67] Can't locate object method "get" via package
 "APR::Table" at /usr/share/perl5/Apache/ASP.pm line 2013.\n at /usr/share/perl5/Apache/ASP.pm line
2013\n\tApache::ASP::get_dir_config('APR::Table=HASH(0x86d7ef0)', 'Global') called at /usr/share/per
l5/Apache/ASP.pm line 273\n\tApache::ASP::new('Apache::ASP', 'Apache2::RequestRec=SCALAR(0x86d7ecc)'
, '/home/ahmad/public_html/index.asp') called at /usr/share/perl5/Apache/ASP.pm line 181\n\tApache::
ASP::handler('Apache2::RequestRec=SCALAR(0x86d7ecc)') called at -e line 0\n\teval {...} called at -e
 line 0\n

If anyone has run across this can you please respond. I would greatly appreciate it.

---

### Post by pokeroo on 2005-11-15
No one has come across this?

---

