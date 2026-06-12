---
title: "Perl Net::SMTP::TLS (using downloaded modules)"
date: 2007-07-28
forum: Programming Talk
---

### Post by SadaraX on 2007-07-28
I am trying to write a perl script to send email using SMTP authentication. I am still new to Perl so I do not know how to do everything yet. I am using Debian Stable and Ubunutu 7.04.

When I just use Net::SMTP, the script works sometimes, but not all the time. I would like to use this TLS module to do real authentication with a smtp-server/port/login/password:

[http://search.cpan.org/author/AWESTH...et/SMTP/TLS.pm](http://search.cpan.org/author/AWESTH...et/SMTP/TLS.pm)

In my script, if I try to use:

```
use Net::SMTP::TLS;
```


It complains that the TLS module is not available. I would like to know how to download the source for the TLS module and how to either install it, or use it locally with my script. Direct link to TLS module here: [http://search.cpan.org/src/AWESTHOLM...et/SMTP/TLS.pm](http://search.cpan.org/src/AWESTHOLM...et/SMTP/TLS.pm)

Thanks for any help in advance.

---

### Post by Mr. C. on 2007-07-29
Perl finds modules using the @INC array of search paths.

Examine your install's search path:

```
perl -e 'print "@INC"'
```

You can add to the search path if necessary.  See :

[http://perldoc.perl.org/lib.html](http://perldoc.perl.org/lib.html)

MrC

---

### Post by tr333 on 2007-07-31
Have you tried installing this using cpan?

Start the cpan shell by typing "cpan" at the bash prompt, then install the module by typing "install Module::Name" at the cpan prompt.

---

### Post by SadaraX on 2007-07-31
> **tr333 said:**
> Have you tried installing this using cpan?

Start the cpan shell by typing "cpan" at the bash prompt, then install the module by typing "install Module::Name" at the cpan prompt.

Yeah, I ended up using CPAN to install the module. It took a bit of juggling some dependencies with Apt but I got it to work. The problem has been SOLVED.

---

