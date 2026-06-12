---
title: "mod perl: Page outputs source code"
date: 2008-10-05
forum: Programming Talk
---

### Post by zigx on 2008-10-05
Hi All,

I have searched around the forums and on a few other sites but cannot find an answer to my mod_perl troubles.

Basically i finally got mod_perl working where it will interpret the script BUT when i view the script on this server via a browser i get a complete dump of the page's HTML source code.

All perl code is interpreted correctly, but it's like the page's header is not being sent over correctly?

On a different server that has mod_perl working correctly, i can access the exact same script/source code and the page renders correctly.

Any pointers on where i can look?

This is an ubuntu/apache2 setup.

Thank you!

PS: Here is the start of the script im running if it helps?
```

#!/usr/bin/perl

print "Content-type: text/html\n\n";

###Find where we are
  open(PWD,'pwd¦');
  $pwd = join('',<PWD>);
  $pwd =~ s/\n//gi;
  close PWD;

### Find the system date
 open(DT, 'date "+DATE: %Y-%m-%d%n<br>TIME: %H:%M:%S"¦');
 $dt = join('', <DT>);
 $dt =~ s/\n//gi;
 close DT;

print "<HEAD><TITLE>Advanced Whereami.cgi</TITLE></HEAD>\n";
print "<body bgcolor='#CC3399' text='#000000'>\n";


```.....etc

---

