---
title: "Perl script to anonymize last byte of IPs in Apache Logfiles"
date: 2013-11-25
forum: Programming Talk
---

### Post by email2 on 2013-11-25
Hello,

hope someone can give me a hand by interating a perl script to anonymize the last byte of my Apache logfiles.
To do so, i got a script from [http://www.zendas.de/technik/sicherheit/apache/scripte.html#1691](http://www.zendas.de/technik/sicherheit/apache/scripte.html#1691)  which worked once, but now i got perl script errors...

Here´s the code:

```

#!/usr/bin/perl

use strict;
use warnings;

use IO::Handle;

if (@ARGV != 1) {
    exit 1;
}

my $LOG;
open $LOG, ">>$ARGV[0]";

$LOG->autoflush(1);

while (my $Line = ) {
    chomp $Line;

    if ($Line =~ /^\[.*/) {
        $Line =~ s/^(.*?\[client \d+\.\d+\.\d+)\.\d+(\].*)/$1.0]$2/;
    } else {
        $Line =~ s/^(\d+\.\d+\.\d+)\.\d+ (.*" (?:\d+|-) (?:\d+|-) "[^?]*).*/$1.0 $2\"/;
        $Line =~ s/""$/\"/;
    }

    print $LOG "$Line\n";
}


```

I saved the script to  /usr/local/bin/aplog-anon,

and added the following to my apache2.conf:

```
LogFormat "%a - - %t \"%r\" %>s %b \"%{Referer}i\"" combined


```

And this to my Apache virtual-host file:

```

ErrorLog "|/usr/local/bin/aplog-anon /var/log/apache/error.log"
CustomLog "|/usr/local/bin/aplog-anon /var/log/apache/ssl_accessAnon.log" combined

```


If i execute the script via /usr/local/bin/./aplog-anon , i get the following errors:

```

mty@bscw1:~$ sudo  /usr/local/bin/./aplog-anon
[sudo] password for mty:
syntax error at /usr/local/bin/./aplog-anon line 17, near "= ) "
syntax error at /usr/local/bin/./aplog-anon line 28, near "}"
Execution of /usr/local/bin/./aplog-anon aborted due to compilation errors.

```


Im my Apache error.log i find this:
```

Execution of /usr/local/bin/aplog-anon aborted due to compilation errors.
piped log program '/usr/local/bin/aplog-anon /var/log/apache2/ssl_accessAnon.log' failed unexpectedly
syntax error at /usr/local/bin/aplog-anon line 17, near "= ) "
syntax error at /usr/local/bin/aplog-anon line 28, near "}"
Execution of /usr/local/bin/aplog-anon aborted due to compilation errors.

```

Is there realy something wrong with the per script, or did i something wrong with piping or....?

Hope someone has a hint...

Thanks in advance,
Martin

---

### Post by Lars Noodén on 2013-11-25
It looks like you are missing a file handle in the code above.  So the *while* line probably ought to read like this, using the default one:

```

while (my $Line = **<>**) {

```

---

### Post by email2 on 2013-11-25
Hello Lars,

thanks for the hint :)

Ich added the ***<>*** in the while statement.

Now i get no errors if i execute the script via /usr/local/bin/./aplog-anon
So far so good.


But the Apache logfile still remains empty an i get the following line in apache error.log instead of the apache log file:

```
 
piped log program '/usr/local/bin/aplog-anon /var/log/apache2/ssl_accessAnon.log' failed unexpectedly

``` 

Im not quite shure what 
```
CustomLog "|/usr/local/bin/aplog-anon /var/log/apache/access.log" combined
```
in the virtual hostfile does...thought it pipes the logfile output directly to the script...am i right?

Thanks for your help!
Martin

---

### Post by Bucky Ball on 2013-11-25
*Thread moved to **Programming Talk**.*

---

### Post by email2 on 2013-11-25
here is the logfile i used for testing:

```
mty@bscw1:~$ tail /var/log/apache2/ssl_access.log
194.94.81.253 - - [25/Nov/2013:16:36:53 +0100] "GET /awstats-icon/os/unknown.png HTTP/1.1" 404 259 "https://bscw1.fb2.fh-frankfurt.de/awstats/awstats.pl?config-bscw.fh-frankfurt.de&framename=mainright"
194.94.81.253 - - [25/Nov/2013:16:36:53 +0100] "GET /awstats-icon/browser/unknown.png HTTP/1.1" 404 262 "https://bscw1.fb2.fh-frankfurt.de/awstats/awstats.pl?config-bscw.fh-frankfurt.de&framename=mainright"
194.94.81.253 - - [25/Nov/2013:16:36:53 +0100] "GET /awstats-icon/other/button.gif HTTP/1.1" 404 260 "https://bscw1.fb2.fh-frankfurt.de/awstats/awstats.pl?config-bscw.fh-frankfurt.de&framename=mainright"
194.94.81.253 - - [25/Nov/2013:16:36:53 +0100] "GET /awstats-icon/mime/image.png HTTP/1.1" 404 259 "https://bscw1.fb2.fh-frankfurt.de/awstats/awstats.pl?config-bscw.fh-frankfurt.de&framename=mainright"
194.94.81.253 - - [25/Nov/2013:16:36:53 +0100] "GET /awstats-icon/other/hx.png HTTP/1.1" 404 257 "https://bscw1.fb2.fh-frankfurt.de/awstats/awstats.pl?config-bscw.fh-frankfurt.de&framename=mainright"
194.94.81.253 - - [25/Nov/2013:16:37:13 +0100] "GET /bscw/bscw.cgi/ HTTP/1.1" 401 6213 "-"
194.94.81.253 - - [25/Nov/2013:16:37:15 +0100] "POST /bscw/bscw.cgi/496631?op=_login HTTP/1.1" 303 2405 "https://bscw1.fb2.fh-frankfurt.de/bscw/bscw.cgi/"
194.94.81.253 - - [25/Nov/2013:16:37:16 +0100] "GET /bscw/bscw.cgi/ HTTP/1.1" 303 2558 "https://bscw1.fb2.fh-frankfurt.de/bscw/bscw.cgi/"
194.94.81.253 - - [25/Nov/2013:16:37:16 +0100] "GET /bscw/bscw.cgi/178 HTTP/1.1" 304 - "https://bscw1.fb2.fh-frankfurt.de/bscw/bscw.cgi/"
194.94.81.253 - - [25/Nov/2013:16:37:23 +0100] "GET /bscw/bscw.cgi/1937020 HTTP/1.1" 200 110879 "https://bscw1.fb2.fh-frankfurt.de/bscw/bscw.cgi/178"

```

Using the script produces no output:
```
mty@bscw1:~$ /usr/local/bin/aplog-anon < /var/log/apache2/ssl_access.log
mty@bscw1:~$

```

It seems the $Line is empty?

---

### Post by Lars Noodén on 2013-11-25
I'm not sure how to capture the errors from any perl scripts while they are being used by Apache in a log pipe.

I have, however, made a simpler test which does nothing except convert the log line to upper case.

```

#!/usr/bin/perl                                                                 

use strict;
use warnings;

if (@ARGV != 1) {
    print qq(one argument needed\n);
    exit 1;
}

print $ARGV[0], qq(=argv0\n);

open ( LOG, ">>$ARGV[0]") or die;
open ( IN, "<-") or die;

autoflush LOG;
autoflush IN;

while ( my $line = <IN> ) {
    chomp( $line ); 
    $line = uc $line;  # upper case
    print LOG $line, qq(\n);
}

close ( LOG );
close ( IN );

```

It's simpler style but it worked in my test on Apache.  If that works for you, then you can substitute in the regular expressions.  

About those sample lines, which part are you trying to remove or replace?

---

### Post by email2 on 2013-11-25
I copied your code to apache-anon2 and added 
#!/usr/bin/perl
in the first line (hope this was right?)

```


#!/usr/bin/perl
use strict;
use warnings;

if (@ARGV != 1) {
    print qq(one argument needed\n);
    exit 1;
}

print $ARGV[0], qq(=argv0\n);

open ( LOG, ">>$ARGV[0]") or die;
open ( IN, "<-") or die;

autoflush LOG;
autoflush IN;

while ( my $line = <IN> ) {
    chomp( $line );
    $line = uc $line;  # upper case
    print LOG $line, qq(\n);
}

close ( LOG );
close ( IN );


```

now i get the following output:
```

mty@bscw1:~$ sudo /usr/local/bin/./aplog-anon2  /var/log/apache2/ssl_access.log
/var/log/apache2/ssl_access.log=argv0

```

the script stucks...do i miss something?

---

### Post by Lars Noodén on 2013-11-25
The piped log scripts take a file name as a command line argument and then that file is appended to.  The data appended is read from stdin.  

```

sudo /usr/local/bin/aplog-anon2 /tmp/output.log < /var/log/apache2/ssl_access.log

```

---

### Post by email2 on 2013-11-25
Goal of the script is to set the last byte of the IP adress to 0 and cut the refferer after the first?

from:
194.94.81.**253** - - [25/Nov/2013:16:36:53 +0100] "GET /awstats-icon/browser/unknown.png HTTP/1.1" 404 262 "https://bscw1.fb2.fh-frankfurt.de/awstats/awstats.pl?**config-bscw.fh-frankfurt.de&framename=mainright**"

to:
194.94.81.**0** - - [25/Nov/2013:16:36:53 +0100] "GET /awstats-icon/browser/unknown.png HTTP/1.1" 404 262 "https://bscw1.fb2.fh-frankfurt.de/awstats/awstats.pl?"

---

### Post by Lars Noodén on 2013-11-25
Ok, here's one with some substitutions.

```

#!/usr/bin/perl                                                                 

# apache piped logs, requires logfile name as arg                               

use strict;
use warnings;

if (@ARGV != 1) {
    exit 1;
}

open ( LOG, ">>$ARGV[0]") or die;
open ( IN, "<-") or die;

autoflush LOG;
autoflush IN;

while ( my $line = <IN> ) {
    $line =~ s/^(\d+)\.(\d+)\.(\d+)\.(\d+)/$1.$2.$3.0/;
    $line =~ s/(\]\s+".*)\?\S+\s/$1/;
    print LOG $line;
}

close ( LOG );
close ( IN );

exit ( 0 );

```

In the pattern \d is a digit, \s is a whitespace, \S is not a white space.  If you have the package perl-doc, you have the full documentation in the man pages.  The man page perlre has the explanation of patterns.

---

### Post by email2 on 2013-11-25
now i got it right:

```
mty@bscw1:~$ sudo /usr/local/bin/./aplog-anon2 /var/log/apache2/test.tmp < /var/log/apache2/ssl_access.log
/var/log/apache2/test.tmp=argv0
mty@bscw1:~$ tail /var/log/apache2/test.tmp
194.94.81.253 - - [25/NOV/2013:16:36:53 +0100] "GET /AWSTATS-ICON/BROWSER/UNKNOWN.PNG HTTP/1.1" 404 262 "HTTPS://BSCW1.FB2.FH-FRANKFURT.DE/AWSTATS/AWSTATS.PL?CONFIG-BSCW.FH-FRANKFURT.DE&FRAMENAME=MAINRIGHT"
194.94.81.253 - - [25/NOV/2013:16:36:53 +0100] "GET /AWSTATS-ICON/OTHER/BUTTON.GIF HTTP/1.1" 404 260 "HTTPS://BSCW1.FB2.FH-FRANKFURT.DE/AWSTATS/AWSTATS.PL?CONFIG-BSCW.FH-FRANKFURT.DE&FRAMENAME=MAINRIGHT"
194.94.81.253 - - [25/NOV/2013:16:36:53 +0100] "GET /AWSTATS-ICON/MIME/IMAGE.PNG HTTP/1.1" 404 259 "HTTPS://BSCW1.FB2.FH-FRANKFURT.DE/AWSTATS/AWSTATS.PL?CONFIG-BSCW.FH-FRANKFURT.DE&FRAMENAME=MAINRIGHT"
194.94.81.253 - - [25/NOV/2013:16:36:53 +0100] "GET /AWSTATS-ICON/OTHER/HX.PNG HTTP/1.1" 404 257 "HTTPS://BSCW1.FB2.FH-FRANKFURT.DE/AWSTATS/AWSTATS.PL?CONFIG-BSCW.FH-FRANKFURT.DE&FRAMENAME=MAINRIGHT"
194.94.81.253 - - [25/NOV/2013:16:37:13 +0100] "GET /BSCW/BSCW.CGI/ HTTP/1.1" 401 6213 "-"
194.94.81.253 - - [25/NOV/2013:16:37:15 +0100] "POST /BSCW/BSCW.CGI/496631?OP=_LOGIN HTTP/1.1" 303 2405 "HTTPS://BSCW1.FB2.FH-FRANKFURT.DE/BSCW/BSCW.CGI/"
194.94.81.253 - - [25/NOV/2013:16:37:16 +0100] "GET /BSCW/BSCW.CGI/ HTTP/1.1" 303 2558 "HTTPS://BSCW1.FB2.FH-FRANKFURT.DE/BSCW/BSCW.CGI/"
194.94.81.253 - - [25/NOV/2013:16:37:16 +0100] "GET /BSCW/BSCW.CGI/178 HTTP/1.1" 304 - "HTTPS://BSCW1.FB2.FH-FRANKFURT.DE/BSCW/BSCW.CGI/"
194.94.81.253 - - [25/NOV/2013:16:37:23 +0100] "GET /BSCW/BSCW.CGI/1937020 HTTP/1.1" 200 110879 "HTTPS://BSCW1.FB2.FH-FRANKFURT.DE/BSCW/BSCW.CGI/178"


```

I tried your script with directly piping from Apache vhost file (like you intended i guess)
this works fine too :)

**Seems i should by u a beer so far** :smile:


With the regex from the initially script it works right i intended:

```

#!/usr/bin/perl
use strict;
use warnings;

if (@ARGV != 1) {
    print qq(one argument needed\n);
    exit 1;
}

print $ARGV[0], qq(=argv0\n);

open ( LOG, ">>$ARGV[0]") or die;
open ( IN, "<-") or die;

autoflush LOG;
autoflush IN;

while ( my $line = <IN> ) {
    chomp( $line );

    if ($line =~ /^\[.*/) {
        $line =~ s/^(.*?\[client \d+\.\d+\.\d+)\.\d+(\].*)/$1.0]$2/;
    } else {
        $line =~ s/^(\d+\.\d+\.\d+)\.\d+ (.*" (?:\d+|-) (?:\d+|-) "[^?]*).*/$1.0 $2\"/;
        $line =~ s/""$/\"/;
    }


#    $line = uc $line;  # upper case


    print LOG $line, qq(\n);
}

close ( LOG );
close ( IN );


```

Output:

```

mty@bscw1:~$ tail /var/log/apache2/ssl_accessAnon.log
194.94.81.0 - - [25/Nov/2013:18:52:44 +0100] "GET /bscw/bscw.cgi/2800431?op=presence.getpresence HTTP/1.1" 200 1565 "https://bscw1.fb2.fh-frankfurt.de/bscw/bscw.cgi/2800431"
194.94.81.0 - - [25/Nov/2013:18:52:45 +0100] "GET /bscw/bscw.cgi/2800383 HTTP/1.1" 200 125391 "https://bscw1.fb2.fh-frankfurt.de/bscw/bscw.cgi/2800431"
194.94.81.0 - - [25/Nov/2013:18:52:47 +0100] "GET /bscw/bscw.cgi/2800383?op=presence.getpresence HTTP/1.1" 200 1565 "https://bscw1.fb2.fh-frankfurt.de/bscw/bscw.cgi/2800383"
194.94.81.0 - - [25/Nov/2013:18:52:48 +0100] "GET /bscw/bscw.cgi/178 HTTP/1.1" 200 1323420 "https://bscw1.fb2.fh-frankfurt.de/bscw/bscw.cgi/2800383"


```


Many thanks Lars!

---

### Post by email2 on 2013-11-25
> **Lars Noodén said:**
> Ok, here's one with some substitutions.

In the pattern \d is a digit, \s is a whitespace, \S is not a white space.  If you have the package perl-doc, you have the full documentation in the man pages.  The man page perlre has the explanation of patterns.

i´ll have a look at the perl man pages...

---

### Post by Lars Noodén on 2013-11-25
The manual page is the authoritative source and ok for lookup but you can get a short overview here, too:

[http://www.cs.tut.fi/~jkorpela/perl/regexp.html](http://www.cs.tut.fi/~jkorpela/perl/regexp.html)

The $1 and $2 refer to the first and second groupings () in the first part of the substitution.

---

