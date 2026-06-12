---
title: "Autotools with a multidirectory project"
date: 2007-12-20
forum: Programming Talk
---

### Post by Naddiseo on 2007-12-20
I've been trying to understand autotools for the past few days to get it to work with a mutli directory project. So far I can just write a simple make file that builds files in that directory. But, I don't want to be writing separate makefiles in each directory, then calling them all by hand, plus with files depending on other files in other directories I don't want to be writing out the huge paths each time.

So my question: is there a way/program that I can run on the top level directory that generates the makefiles in each (sub)directory and the current directory, and keeps track of the dependencies?

I ask this so as not to write one myself, but I'm sure other people have had exactly the same problem; so there must be a solution.


Thanks for any help.

---

### Post by engla on 2007-12-20
Yes, autotools facilitates this. With autotools, each directory should have a Makefile.am file, and the top dir should simply specify the rule:

SUBDIRS = src doc data

(for example if you have these three subdirectories)

Then the Makefile.am in each directory would do the job. I'm sure we can find examples for this on the net.

I hope you see the difference between GNU make and autotools; the former is a more lowlevel tool, for which you can write makefiles (named exactly "Makefile" almost all the time). Autotools are autoconf and automake and some associated tools to which you write configuration files like "configure.ac" and "Makefile.am". These are higher-level, since they in turn generate makefiles for gnu make, which make then later will run. Even though autotools are higher-level and the makefiles are wayy shorter to write, it can be tricky.

[Here is a tutorial/intro to autotool]("http://inti.sourceforge.net/tutorial/libinti/autotoolsproject.html")s which even uses SUBDIRS

---

