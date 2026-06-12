---
title: "Autotools AC_CONFIG_FILES Question"
date: 2010-11-03
forum: Packaging and Compiling Programs
---

### Post by interval1066 on 2010-11-03
I'm packaging a few bash scripts with my application, this is my first time doing this. I'm using autotools, of course. I'm trying to use the AC_CONFIG_FILES macro in my configure.ac file;

AC_CONFIG_FILES([src/script], [chmod +x src/script])

previous to this is a test to see if zenity is installed on the system and copy it to the application's bindir; otherwise the intent is to use the application in a command line only mode.

I'm missing what I need to complete this action, as I expected, there is an error after this in a dry run of the configure script;

config.status: error: cannot find input file: `src/script.in'

Sure, I get it, I need to complete the script.in file. My problem is I'm not sure what needs to be in this file.

Is this a shell script to perform the actual cp of the script from src/ to $bindir? If so should I be performing the chmod there? The docs are a little sparse regarding this particular scenario. If I were distributing a shared lib and building with libtool there's gobs of info, but a script with an app seems a little difficult for me to find.

---

