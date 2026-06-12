---
title: "Apache and Perl"
date: 2006-07-15
forum: Programming Talk
---

### Post by hitime on 2006-07-15
I'm trying to write some simplitic perl scripts (CGI) on my Sun Ultra 5.  I just installed the latest version of Ubuntu, modified the virtualhost file so I can execute perl scripts, but yet all I get in the apache log is:

[Sat Jul 15 17:10:13 2006] [error] [client 71.241.177.91] Premature end of script headers: test1.cgi
[Sat Jul 15 17:11:50 2006] [error] [client 71.241.177.91] Premature end of script headers: test1.cgi
[Sat Jul 15 17:13:05 2006] [error] [client 71.241.177.91] Premature end of script headers: test1.cgi
[Sat Jul 15 17:13:16 2006] [error] [client 71.241.177.91] Premature end of script headers: test1.cgi


I have even tried just a basic script like:

hitime@ultra5:/var/www/test$ cat test1.cgi
#!/usr/bin/perl

print "<html><head></head><body>";
print "test";
print "</html></body>";
hitime@ultra5:/var/www/test$


and I still get:

[Sat Jul 15 17:13:16 2006] [error] [client 71.241.177.91] Premature end of script headers: test1.cgi

If someone can tell me if I'm missing a switch on the shebang line or maybe I have something miss configured I would greatly appreciate it...


hitime  ](*,)

---

### Post by sharperguy on 2006-07-15
Ok, I dont know anything about perl, so i shouldnt really be attempting this.
But to me it seems like one of two things:[LIST=1]
[*]You have forgotten some "end" statement requred by perl (unlikely imo)
[*]You need a linespace after the last line (try pressing return after the last line and saving)[/LIST]

---

### Post by ifokkema on 2006-07-16
The thing is, Apache expects a header from your script. It's not there, and Apache stops processing the file output.
You need something similar to:
```
print "Content-type: text/html; charset=ISO-8859-1\n\n";
```
or the like.
You could also do:
```
use CGI;
``` and after that, I believe (not quite sure here):
```
print CGI::header();
```
I'm just not sure about the second command, but maybe it's enough to get you on your way.

---

