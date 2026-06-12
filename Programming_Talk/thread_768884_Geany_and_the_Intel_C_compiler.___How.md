---
title: "Geany and the Intel C compiler.   How?"
date: 2008-04-26
forum: Programming Talk
---

### Post by Nuverde on 2008-04-26
In the past, I have done my C programming using a terminal and bash.  I like using the Intel C compiler.  When using bash, I just source the iccvars.sh file inside my .bashrc to set up my environment.  Now,I am starting to play with Geany and would like to use the Intel C compiler. I am using a makefile to manage things.  How can I source this iccvars.sh file to make it available in Geany?  Is there an option inside Geany?  Do I need to configure something in Gnome?

Thanks!

---

### Post by sq377 on 2008-04-26
Under Build->Set Includes and Arguments, you can have it run anything you want.  I have mine set to run make.  You could probably have it run something like iccvars.sh && make if make doesn't just work.

---

