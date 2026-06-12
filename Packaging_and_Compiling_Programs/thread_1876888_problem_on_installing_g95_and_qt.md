---
title: "problem on installing g95 and qt"
date: 2011-11-07
forum: Packaging and Compiling Programs
---

### Post by rinosalman on 2011-11-07
hi..
i hope this is the right forum to place my problem.
i install g95 on ubuntu 10.10, i try followed this "ln -s $PWD/g95-install/bin/*g95* /bin/g95" to create symbolic link..appear this one "ln: creating symbolic link `/bin/g95': File exists"
but, when tested it by write "g95", appear this one " 
No command 'g95' found, did you mean:
 Command 'gt5' from package 'gt5' (universe)
 Command 'f95' from package 'gfortran' (main)
g95: command not found
need help please...

---

### Post by SevenMachines on 2011-11-07
It looks like you're trying to symlink many files into one, best way in this case i'd say is instead just to add the executable path to you're ~/.bashrc file.
```
 export PATH=/path/to/g95/binaries/:$PATH
```Or add the g95 repository supplied by the author and install from there,see
[http://www.gfd-dennou.org/library/cc-env/g95/index.htm.en#label-3](http://www.gfd-dennou.org/library/cc-env/g95/index.htm.en#label-3)

Or, stick with the well supported and already available fortran tools in the ubuntu repository.
```
$ sudo apt-get install gfortran
$ f95
```

---

### Post by rinosalman on 2011-11-07
it's solved, thanks for SevenMachines

---

