---
title: "autoconf, automake, .texi headache"
date: 2009-01-06
forum: Packaging and Compiling Programs
---

### Post by shouldersmagru on 2009-01-06
Hello,

this seems like the best place for this problem, apologies if its not. I'm stuck in a loop that i thought i'd seen the last of in my red hat dependency hell days.

Initially, i was trying to use buildroot to build a file system and tools for cross compilation on an embedded board. I kept getting errors about a .texi file, which i cannot remember exactly what the errors were. 

Anyway, that led to me messing around with trying to install earlier versions of texinfo or automake as one possible solution. I think thats just made things worse.

So fast forward to now. Originally, i was using the synaptic package manager to install these programs, and i had a go at completely removing the autoconf and automake packages in order to try and start afresh. Automake install was crying about autoconf, so i tried installing that first, but that was throwing an error 'install -info: No dir file specified'.

I decided to try and install it myself, so downloaded the source for autoconf, did a configure which went fine, (oh, i made sure that perl and m4 was installed which are prerequisites, and texinfo shows as being installed according to the synaptic package manager.)

Then i tried a 'make all' which stops with the error 'No rule to make target fdl.texi needed by autoconf.info'.

Autoconf, automake and .texi / .info files seem to be so intertwined im not sure where to go from here. It all seems to be related to whatever deals with these .texi or .info files.

Any ideas anybody?:confused:

---

