---
title: "CGI not producing html page"
date: 2009-11-10
forum: Programming Talk
---

### Post by chandubaba on 2009-11-10
#!/usr/bin/perl -wT
print "Content-type:text/html\n\n";
print "Hello world\n";


This should produce html page ... but how to do it?

Output in terminal:
chandan@chandan-desktop:~/Documents/learn$ ./ff.cgi
Content-type:text/html

Hello world

---

### Post by A_Fiachra on 2009-11-10
You configure your web server to understand that it can run cgi programs.


Usually tou do this but setting correct executable permissions for a /cgi-bin directory (in the apache worls, you set +ExecCGI for a directory under DocumentRoot.  You can set +ExecCGI for home directories (using suexec) or other locations, you mileage may vary.  But, consult you webserver docs for how to enable CGI and tail your error log!!!!!

---

### Post by MindSz on 2009-11-10
My knowledge in CGI and HTML is almost 0, but I did program a small interface between the two for one of my projects.

What I did (besides enabling CGI) was to call the cgi script from an html page executed from a web browser. Basically, I opened up firefox, went to my html page and hit a button which executed the cgi script.

That seemed to work for me.

---

