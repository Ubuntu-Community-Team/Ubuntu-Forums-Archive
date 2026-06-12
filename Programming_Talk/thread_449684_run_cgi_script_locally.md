---
title: "run cgi script locally"
date: 2007-05-20
forum: Programming Talk
---

### Post by evaristegalois on 2007-05-20
I can write html forms on the web and make perl process them, but I don't seem to be able to do it on my local computer. Here is test.htm:

> 

<html>

<form action="/home/path-to-file/test.cgi" method="POST">

<input name="test" type="text" size="15"><p>

<input type="submit" value="LOGIN">

</html>



Here is test.cgi:

> 

#!/usr/bin/perl

$data = <STDIN>;

print "Content-type: text/html\n\n";

print "<html>Form results: $data<p></html>";



If I put test.htm and test.cgi on the web server and run them, everything runs perfectly. If I run test.cgi from the command line everything works well, too. But if I open the local computer file test.htm in firefox, firefox doesn't get it that I want it to run test.cgi as a script using the data from the test.htm webform. I have perl installed. The permissions are set correctly. What's going on?

---

### Post by pmasiar on 2007-05-20
does web server run on your local computer? You can get simple web server in about 7 lines of Python, see wiki in my sig.

---

### Post by tr333 on 2007-05-21
The CGI program is executed by the web server, not the web browser.  This means that you can't run CGI programs from your local machine unless you are running them through a web server.  You should be able to run the CGI program from the commandline directly if you want to test it. eg. "perl ./test.cgi"

writing CGI programs is much easier in perl if you use the CGI module, available from CPAN and installed by default on most perl installs.  Any CGI done with perl should use the "taint mode" switch "-T".
the CGI module allows you to get the form data from each individual parameter using the"param()" method.
```
#!/usr/bin/perl -T

use strict;
use warnings;

use CGI qw(:all -debug);
use CGI::Carp qw(fatalsToBrowser warningsToBrowser);
use CGI::Pretty;

print header;
print start_html("TEST");
print h1("FORM DATA TEST");
print br;

if ( param() ) {
    print p("Printing FORM data:");
    foreach my $parameter (param()) {
        print p("$parameter = ".param($parameter));
    }
} else {
    print p("no form data exists");
}

print end_html;

```

see the following sites for more info:
[http://search.cpan.org/~lds/CGI.pm-3.29/CGI.pm](http://search.cpan.org/~lds/CGI.pm-3.29/CGI.pm)
[http://search.cpan.org/modlist/World_Wide_Web/CGI](http://search.cpan.org/modlist/World_Wide_Web/CGI)

---

### Post by evaristegalois on 2007-05-28
Thanks. That sounds helpful. I'll look into it. I didn't know I had to have my own web server on the local machine either.

--evaristegalois

---

