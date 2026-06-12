---
title: "Trouble Installing Anjuta"
date: 2006-08-09
forum: Programming Talk
---

### Post by neil_707 on 2006-08-09
Hey I'm basically a newbie to Ubuntu Linux!

I have a problem installing Anjuta IDE. When I try to compile the source package it gives me the falling error(after running ./configure)

neil@neil-laptop:~/Desktop/anjuta-2.0.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

Help!?:-k 

Thanx

Neil

---

### Post by simonn on 2006-08-09
Install it using synaptic or apt-get.

---

### Post by agrimstad on 2007-04-06
I hit this same error about the missing perl module XML::Parser too in a completely different context. Since the question didn't receive a useful answer, I thought I might finish the thread with the answer that worked for me.

The clue is in the diagnostic:

checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

It turns out there is an ubuntu package called intltool (!). Install it, e.g.,

sudo apt-get install intltool

and the error should go away.

---

