---
title: "Perl CGI question"
date: 2008-01-04
forum: Programming Talk
---

### Post by bryanosaurus on 2008-01-04
I used to run an apache server on Windows, and I have this pretty simple script to keep track of hits on my website. I recently switched to Ubuntu and have my Apache2 server set up. 
I have perl working, pl and cgi scripts can be executed from my cgi-bin. I can't get my counter script to work though. 

```
#!/usr/bin/perl




$counter = "counter.txt";

open(FILE, "$counter") || &error('open->counter', $counter);

$count = <FILE>;

close(FILE);

$count++;

open(FILEA, ">$counter") || &error('open->counter', $counter);

print (FILEA "$count");

close(FILEA);

print "Content-type: text/html\n\n";

print "$count";
```

I'm pretty sure everything is correct, SSI's are set up through apache

<!--#exec cgi="../cgi-bin/counter.cgi" -->

returns

[an error occurred while processing this directive]

Any one know if I need to do this differently or maybe there's something I'm missing? Any help would be appreciated :)

---

### Post by evymetal on 2008-01-04
look in your apache log files, they should give you much more information.

They normally tell you where the problem is. Haven't ever used an executable SSI, but have you got the correct modules imported in httpd.conf?

---

### Post by bryanosaurus on 2008-01-05
I'm not sure what modules I need actually. Do you have any information on this?

As for error log I have this:

[Sat Jan 05 15:13:29 2008] [error] (2)No such file or directory: exec of '/usr/lib/cgi-bin/counter.cgi' failed
[Sat Jan 05 15:13:29 2008] [error] [client 24.45.44.211] Premature end of script headers: counter.cgi

I also can't run this in terminal, I get this error:

Undefined subroutine &main::error called at /usr/lib/cgi-bin/counter.cgi line 6.

line 6 is:

open(FILE, "$counter") || &error('open->counter', $counter);

---

