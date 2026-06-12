---
title: "Any easy way to turn my Ubuntu PC into a dev platform?"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by naragam on 2013-01-15
Hi all,

There has to be an easier way to turn my Ubuntu PC into a dev platform w/o going through so many unresolved problems with the building of foundation libs. Right? I have been trying to get three libs - GSL, EMBOSS, and Biopython. So far, something or the other (mostly trying to get some include file or lib reference resolved) fails and the web-based docs are either old or outdated and as usual, I can't seem to find a working build script that just builds on my machine. 

Can somebody out there please point me to something reliable so that I can get a working dev platform built for some advanced bioinformatics work?

Thanks much in advance,

Nash

---

### Post by Cheesemill on 2013-01-15
There should be no need to compile anything, all of those packages are in the standard Ubuntu repositories.

```
sudo apt-get install gsl-bin emboss python-biopython
```

---

### Post by Toz on 2013-01-15
Here is a spin of Ubuntu specifically for bioinformatics: [http://nebc.nox.ac.uk/tools/bio-linux]("http://nebc.nox.ac.uk/tools/bio-linux").

There is a link at that website with information on how to install all of the bio-linux software onto an existing ubuntu system: [http://nebc.nerc.ac.uk/tools/bio-linux/other-bl-docs/package-repository]("http://nebc.nerc.ac.uk/tools/bio-linux/other-bl-docs/package-repository").

---

### Post by naragam on 2013-01-16
Thanks much cheesemill! Hope that will work good...:)

---

### Post by naragam on 2013-01-16
Dumb question to cheesemill....

I think I got get-apt working, but I have no idea where all it installed the packages, for, I can't "find" them or look at the *.h files .... apparently to have gone into /usr/include/gsl area...? Can you point me to how I can check my installations?

TiA, Nash

---

### Post by oldos2er on 2013-01-16
You can see where each file in a package is installed with ```
dpkg -L <package name>
```

---

### Post by naragam on 2013-01-16
Thanks Ann... I should have reframed my question... Actually what I need are the include files from the GSL library (e.g., gsl_rng.h). I assumed that the package gsl-bin would have everything, but I guess I'm still too old fashioned unix guy and can't seem to muster all the new changes in Linux as far as these plethora of distributions go...lol

Can you or somebody else know how I can get all the include files that might be required for gsl/emboss/biopython based newer research software? Seems like it has become completely non-standard as to where people nowadays are putting the source files in any public release of free s/w?

Any help is highly appreciated.

Nash

---

