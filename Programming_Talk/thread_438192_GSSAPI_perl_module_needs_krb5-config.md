---
title: "GSSAPI perl module needs krb5-config"
date: 2007-05-09
forum: Programming Talk
---

### Post by simba00 on 2007-05-09
Hello, I'm trying to compile the GSSAPI perl module using cpan

It doesn't compile. [The docs say to make sure krb5-config is present]("http://www.cpan.org/modules/by-module/LWP/AGROLMS/GSSAPI-0.23.readme") - but what does that actually mean?

I've done ```
 apt-get install krb5-user
``` but it still wants more from me - here's the output from sudo perl -MCPAN -e shell

```
cpan> make GSSAPI         
Running make for module GSSAPI
Running make for A/AG/AGROLMS/GSSAPI-0.24.tar.gz
  Is already unwrapped into directory /home/simba/.cpan/build/GSSAPI-0.24

  CPAN.pm: Going to build A/AG/AGROLMS/GSSAPI-0.24.tar.gz

 Welcome to GSSAPI.pm setup! 

 run "perl Makefile.PL --help" to see further installation options
----------------------------------------------------------
 Searching krb5-config command... not found! at Makefile.PL line 94.
``` It's driving me crazy because I'm clearly missing something obvious - but what?

Thanks for looking,

S.

---

### Post by pointone on 2007-05-09
```
sudo apt-get install krb5-config
```

---

### Post by simba00 on 2007-05-10
Hello, thanks for replying. 

When I run that apt-get tho, my terminal says the 'krb-config is already the latest version'

Is there some way I need to associate it with the Makefile.PL or perl's make.conf? It's obviously not happening automatically. Or else, perl can't see that I already have krb5-config for some reason.

A real puzzle.

---

### Post by eternalsword on 2008-03-18
For those that come across this like me looking for an answer, the solution is installing libkrb5-dev as that is the package that contains /usr/bin/krb5-config the krb5-config package only contains the configuration files.

---

### Post by Draiodoir on 2009-06-10
Just came up against this today when trying to install LDAPCONTRIB for twiki and this fixed it for me. It's great when people take the time to post the solution on their own posts when they find them. Thanks

---

