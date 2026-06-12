---
title: "Programming for the Sys Admin"
date: 2007-04-29
forum: Programming Talk
---

### Post by fritz_monroe on 2007-04-29
I've always been a Windows system administrator.  About a year ago I managed to switch over to a large Linux based system that also has several Solaris servers, but no Windows servers.  I'm coming along and have done lots of junior UNIX/Linux SA functions.  In day to day troubleshooting, I have to edit a lot of config files and parse the log files.  But these functions are very labor intensive and should be automated or scripted.

This is where I'm looking for some advice.  I've done some coding in Java and C, but don't know much about scripting languages.  So from an SA's point of view, what languages should I look into to perform these scripting tasks?  I know that Perl, AWK and SED are good ones to learn, but are there any others that I should look into for working with these text files?

Thanks in advance.

---

### Post by pmasiar on 2007-04-29
Python can do work of all three, and is much more readable

---

### Post by cwaldbieser on 2007-04-29
> **fritz_monroe said:**
> I've always been a Windows system administrator.  About a year ago I managed to switch over to a large Linux based system that also has several Solaris servers, but no Windows servers.  I'm coming along and have done lots of junior UNIX/Linux SA functions.  In day to day troubleshooting, I have to edit a lot of config files and parse the log files.  But these functions are very labor intensive and should be automated or scripted.

This is where I'm looking for some advice.  I've done some coding in Java and C, but don't know much about scripting languages.  So from an SA's point of view, what languages should I look into to perform these scripting tasks?  I know that Perl, AWK and SED are good ones to learn, but are there any others that I should look into for working with these text files?

Thanks in advance.

Some basic shell scripting can do wonders.  The bourne shell is pretty universal, and bash is popular on Linux.  Python is also good for doing the same kinds of tasks.

---

### Post by fritz_monroe on 2007-04-29
Thanks for the quick replies.  I didn't think about Python.  I know there are a couple good online books on learning BASH scripting.  Maybe that's the way to go?

Any other suggestions?

---

### Post by ghostdog74 on 2007-04-29
I suggest you learn shell scripting first, since you are system administrator. get to know the tools available for you eg sed/awk/bash. Parsing text files is only one of the functions an SA does. also if you want to write rc or startup scripts, learn the shell.

---

