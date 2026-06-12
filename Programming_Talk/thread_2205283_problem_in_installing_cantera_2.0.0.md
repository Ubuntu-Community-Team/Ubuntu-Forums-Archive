---
title: "problem in installing cantera 2.0.0"
date: 2014-02-13
forum: Programming Talk
---

### Post by babakflame on 2014-02-13
Dear Buddiesme 

I am trying ot install cantera 2.0.0 . I have downloaded the code and put it in $HOME/flameletFOAM address.
Then I came into src folder of cantera. there is a SConscript and Makefile.am files in this folder.
I have already downloaded scons g++ libboost-all-dev libsundials-serial-dev subversion libblas-dev liblapack-dev

In the src folder of cantera I ran:

```
scons build [COLOR=#0000ff]optimize=[/COLOR]n [COLOR=#0000ff]blas_lapack_libs=[/COLOR]blas,lapack [COLOR=#0000ff]prefix=[/COLOR]/opt/cantera [COLOR=#0000ff]python_package=[/COLOR]none
```


I got this error:

```
babak@babak-VPCEA26FG:~/flameletFOAM/cantera-2.0.0/src$ scons build optimize=n blas_lapack_libs=blas,lapack prefix=/opt/cantera python_package=none

scons: *** No SConstruct file found.
File "/usr/lib/scons/SCons/Script/Main.py", line 834, in _main


```

Would some body help me what is the problem?

   Regards
      Bobi

---

### Post by spjackson on 2014-02-13
```

$ man scons

       By  default, scons searches for a file named SConstruct, Sconstruct, or
       sconstruct (in that order) in the current directory and reads its  con&#8208;
       figuration  from  the  first file found.  An alternate file name may be
       specified via the -f option.

```
So, find where that file is and run your command in that directory.
```

$ find ~/flameletFOAM/cantera-2.0.0 -iname sconstruct

```
Where are you getting your instructions from about how to build and install this?

---

### Post by babakflame on 2014-02-27
Dear spjackson

Many thanks. I found the location of Sconstruct file.

---

