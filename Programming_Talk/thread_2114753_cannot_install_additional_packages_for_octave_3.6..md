---
title: "cannot install additional packages for octave 3.6.3"
date: 2013-02-10
forum: Programming Talk
---

### Post by fr33c0untry on 2013-02-10
hi
i wanted to install a few packages ,integration ,symbolic and signal processing.i downloaded them from octave forge and tried to install by entering the command on octave but it showed some compiling errors.

so i searched for it on synaptic manager.it had all the packages that could be found in octave-forge but when i clicked to download is instructed me to delete the new version 3.6.3 and install the old 3.2.4 version.

i'm thinking of going back to the old one since i had it before and didn't find any difference with the new one.and because its easier to install the packages that way. but i hope if someone can help me install these packages on octave 3.6.3

i can provide the error message later if required.

thanks

---

### Post by fr33c0untry on 2013-02-11
here are the errors that i get :
for integration-1.0.7.tar.gz

```
 
couldn't create installation directory /usr/share/octave/packages/integration-1.0.7 : Permission denied
error: called from `pkg>copy_files' in file /usr/share/octave/3.6.3/m/pkg/pkg.m near line 1569, column 7
error: called from:
error:   /usr/share/octave/3.6.3/m/pkg/pkg.m at line 876, column 5
error:   /usr/share/octave/3.6.3/m/pkg/pkg.m at line 383, column 9

```

for symbolic-1.1.0.tar.gz

```

make: mkoctfile: Command not found
make: *** [symbols.o] Error 127
'make' returned the following error: make: Entering directory `/tmp/oct-hFUiQu/symbolic/src'
mkoctfile -v    -c symbols.cc
make: Leaving directory `/tmp/oct-hFUiQu/symbolic/src'
error: called from `pkg>configure_make' in file /usr/share/octave/3.6.3/m/pkg/pkg.m near line 1391, column 9
error: called from:
error:   /usr/share/octave/3.6.3/m/pkg/pkg.m at line 834, column 5
error:   /usr/share/octave/3.6.3/m/pkg/pkg.m at line 383, column 9

```

the other packages show one of the two errors as well.

---

