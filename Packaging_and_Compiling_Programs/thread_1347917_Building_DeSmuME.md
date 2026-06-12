---
title: "Building DeSmuME"
date: 2009-12-06
forum: Packaging and Compiling Programs
---

### Post by Azatos on 2009-12-06
I just switched over to ubuntu fully recently and I'm trying to get the hang of compiling things on ubuntu 9.10.  
Well I followed the instructions on the wikipage [http://wiki.desmume.org/index.php?title=Installing_DeSmuME_from_source_on_Linux](http://wiki.desmume.org/index.php?title=Installing_DeSmuME_from_source_on_Linux) 
 When I go type the autogen command it says the file was missing, i tried re updating the svn and tried again and same error.  I then looked in the folder and I see the file right there.

exact error: ./autogen.sh: 14: autoreconf: not found

---

### Post by SevenMachines on 2009-12-07
have you got autoconf installed? (it supplies autoreconf)
$ sudo apt-get install autoconf
$./autogen.sh

---

