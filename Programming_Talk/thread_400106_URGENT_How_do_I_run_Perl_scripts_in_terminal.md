---
title: "URGENT: How do I run Perl scripts in terminal???"
date: 2007-04-03
forum: Programming Talk
---

### Post by netsurfau on 2007-04-03
G'day All,

I'm trying to finish an assignment and have to test the scripts I've written, and don't 
want to go into Windoze to work on them.

Assignment is due tomorrow of course.  For some reason I though I could just run
them natively.

How do I get the Perl scripts to run in a terminal window?

Regz
Blade

---

### Post by souki on 2007-04-03
first solution
perl /path/to/the/script.pl

second solution, if you want to execute it like any other command
write this at first line in your script
#!/usr/bin/perl

then, change the executable bit
chmod +x script.pl

then you can execute it
/path/to/the/script.pl

---

