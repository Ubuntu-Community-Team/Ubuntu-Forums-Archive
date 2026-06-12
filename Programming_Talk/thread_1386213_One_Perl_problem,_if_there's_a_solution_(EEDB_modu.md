---
title: "One Perl problem, if there's a solution (EEDB module)"
date: 2010-01-20
forum: Programming Talk
---

### Post by gjatute on 2010-01-20
Hello!

I need to use for work a Perl module called EEDB. The doc is really poor and I had hard time making it work properly, but in the end I managed. I still have one problem and I was wondering whether there's a solution that does not imply to set up everything again.

All the scripts (.pl, .cgi, .fcgi) that come along with the module have the 
```
#!/usr/local/bin/perl -w
```first line. Unfortunately the location of my Perl distribution is /usr/bin/perl.

This would not be a big problem if the module was not working as it does: every time you create a new EEDB instance, a new webservice is created and the directory containing the .cgi/.fcgi scripts is copied in the directory browsed by apache (if the terminology is wrong I'm sorry, it's the first time I happen to work with servers). 

SO: should I reinstall completely the module and change the #!/usr/local/bin/perl -w before the installation (and consequent population of several directories) or is there another way to tell the system where to look for Perl?

Many thanks in advance for your help!

Margherita

---

