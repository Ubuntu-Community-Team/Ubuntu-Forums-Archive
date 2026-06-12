---
title: "file identifies Perl script as HTML"
date: 2014-08-05
forum: Programming Talk
---

### Post by Peter_DP on 2014-08-05
Hi;

I am a member of the Ohloh team at Black Duck Software and we are upgrading our production servers to Ubuntu 14.  Right now I am testing our open source line counting application, Ohcount ([https://github.com/blackducksw/ohcount](https://github.com/blackducksw/ohcount)) to run on Ubuntu 14 and have run into a problem.

In a nutshell, when we have a perl CGI script that starts with [FONT=courier new]#!/usr/bin/perl -w[/FONT], the magic database identifies it as "HTML" instead of Perl.  We can change the result by changing the code to [FONT=courier new]#!/usr/bin/env perl -w[/FONT]. While this will fix our tests, I don't know if this will satisfy the expectations of our user community. (Hi, Users ):P)

Here is some output:

**Unwanted Output **
```

vagrant-ubuntu-trusty-64: ~/src/ohcount (master)$ head test/src_dir/perl.cgi 
#!/usr/bin/perl -w


# ajaxCheckbox.pl - a script to test Ajax functionality

vagrant-ubuntu-trusty-64: ~/src/ohcount (master)$ file test/src_dir/perl.cgi 
test/src_dir/perl.cgi: HTML document, ASCII text

```

**&#8203;Desired Output** (other than our having to change the shebang line)
```

vagrant-ubuntu-trusty-64: ~/src/ohcount (master)$ vim test/src_dir/perl.cgi 

vagrant-ubuntu-trusty-64: ~/src/ohcount (master)$ head test/src_dir/perl.cgi 
#!/usr/bin/env perl -w


# ajaxCheckbox.pl - a script to test Ajax functionality

vagrant-ubuntu-trusty-64: ~/src/ohcount (master)$ file test/src_dir/perl.cgi 
test/src_dir/perl.cgi: Perl script, ASCII text executable

```

One can see that the Perl script identifier is in there, it's just that the library matches HTML first.
```

vagrant-ubuntu-trusty-64: ~/src/ohcount (master)$ file --keep-going test/src_dir/perl.cgi 
test/src_dir/perl.cgi: HTML document text\012- Perl script text executable\012- HTML document text\012- HTML document text\012- HTML document text\012- HTML document text\012- exported SGML document text\012- a /usr/bin/perl -w script text executable\012- exported SGML document, ASCII text

```

It **may **also be that this is the correct designation.  After all, the reference script ([https://github.com/blackducksw/ohcount/blob/master/test/src_dir/perl.cgi](https://github.com/blackducksw/ohcount/blob/master/test/src_dir/perl.cgi)) is a CGI that tests AJAX functionality and indeed generates HTML.   So, it may be that we have to change our test so show that this is HTML.

I'd appreciate your thoughts on the matter.  Thanks,  pdp

---

