---
title: "Perl in Ubuntu. Running my first webpage"
date: 2010-03-14
forum: Programming Talk
---

### Post by ade234uk on 2010-03-14
OK I am intrigued by perl. I have created my first hello world programme.
I have apache running and have uploaded my hello_world.pl to public_html
I also have perl installed on my Ubuntu server.

When I goto to run hello_world.pl it attempts to download it, instead of displaying it.

Can someone point me in the right direction here?

---

### Post by gmargo on 2010-03-14
You have to tell **apache** that your .pl file should be run as a cgi script.  Do this by creating a file called **.htaccess** in the same directory as your .pl file.  The contents of **.htaccess** should be:
```

Options +ExecCGI
AddHandler cgi-script cgi pl

```This tells apache that any files in this directory (and below) that end in ".cgi" or ".pl" are cgi scripts to be executed.  You also need execute permissions set on those files.

For your entertainment, and also to give you some known working code, here's my own "Hello.pl" cgi script:
```

#!/usr/bin/perl -w

use strict;
use warnings;

use CGI qw(-debug escapeHTML -oldstyle_urls);
use POSIX ();

my $q = CGI->new();

main();
exit 0;

sub main
{
    print $q->header('text/html');
    print qq(<!DOCTYPE html\n)
         .qq(    PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"\n)
         .qq(    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">\n);

    my $title = "Howdy";
    print "<html>\n";
    print "<head>\n";
    print "<title>".escapeHTML($title)."</title>\n";
    print qq(<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />\n);
    print "</head>\n";
    print "<body>\n";

    print "<p>\n";
    print "Hello, World\n";
    print "</p>\n";

    print "<p>\n";
    print " getuid=".(POSIX::getuid());
    print " geteuid=".(POSIX::geteuid());
    print " cwd=".escapeHTML(POSIX::getcwd());
    print "</p>\n";

    print "<p>\n";
    print "Environment variables:\n";
    print "<br/>\n";
    foreach (sort keys %ENV)
    {
        print escapeHTML($_)." => ".escapeHTML($ENV{$_})."\n";
        print "<br/>\n";
    }
    print "</p>\n";

    print "</body>\n";
    print "</html>\n";
}

```

---

### Post by ade234uk on 2010-03-15
Excellent. Thank you very much. Will check this out when I get home. Will let you know how I get on.

---

