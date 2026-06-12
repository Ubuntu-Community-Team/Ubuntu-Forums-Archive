---
title: "What to install to compile cpp program"
date: 2005-08-17
forum: Programming Talk
---

### Post by grj on 2005-08-17
I need to install a small command line app called diatheke. What do I need to install to accomplish this? Any other suggestions would be greatly appreciated.

---

### Post by Juergen on 2005-08-18
But 'diatheke' is in the repositories...

If you want to compile anyway:

The package 'build-essential' installs the C/C++ compilers.

Then you probably have to install some 'lib*-dev'-packages.
This depends on the app you are compiling - so you have to find out yourself.
Look at the output of './configure' - it should complain about missing libs
(most of the time the libs are installed, just the corresponding *-dev packages are not).

---

### Post by grj on 2005-08-18
I could be wrong, but it appears the diatheke package is for the web version. It installs apache, etc which I do not want. Do you know if the package includes the cli version also. If it does, I will install it and just tell apache not to start up.

---

### Post by Juergen on 2005-08-18
I can't do much more than you can - look at the description in Synaptic (well I could install it but... :-))

It says it's a cli utility and a cgi-script.

---

