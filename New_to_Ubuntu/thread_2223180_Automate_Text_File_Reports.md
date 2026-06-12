---
title: "Automate Text File Reports"
date: 2014-05-09
forum: New to Ubuntu
---

### Post by Magnezone150 on 2014-05-09
I'd like some scripting or programming pointers. it's something I want to do for fun with Perl preferably since I'm just learning it on my Ubuntu Machine.

I'm looking for a way to automate a script to help create weekly notes with an interactive menu to choose what was done that day almost like a to do list.

For Example:

**Menu**

Press the numbers for monday

1 = cleaned bedroom
2 = took dog for walk

Press 1 and 2

Press Numbers for Tuesday ...

Etc..

**Output in text file**

Monday

took dog for walk
cleaned bedroom

Tuesday

cleaned bedroom

etc...

---

### Post by tgalati4 on 2014-05-09
Although PERL is used for text processing, it lacks a real case statement which makes programming this type of application somewhat cumbersome.

[http://perldoc.perl.org/5.8.8/Switch.html](http://perldoc.perl.org/5.8.8/Switch.html)

[http://perlmaven.com/switching-in-perl-5.10](http://perlmaven.com/switching-in-perl-5.10)

You also want to include:

3:  Other activity--type in the activity and it will be saved for future use.

---

