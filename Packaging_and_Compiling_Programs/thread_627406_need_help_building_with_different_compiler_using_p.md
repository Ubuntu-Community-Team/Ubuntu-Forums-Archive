---
title: "need help building with different compiler using pdebuild on Ubuntu 7+"
date: 2007-11-30
forum: Packaging and Compiling Programs
---

### Post by milind_iitg on 2007-11-30
Hello,
 I want to use another compiler(Intel icc) for pdebuilding the packages. icc I have not downloaded & built using pdebuild, but with ./configure && run. So, its not in the list of package database, eg. dpkg -l icc does not show anything. How I can assure its present there. Actually, I want to use icc to build other packages, but by using pdebuild. But pdebuild takes gcc, and gcc is recognized by the pbuilder tool, while icc does not. Is there a method or configuration in which I can use with Intel compiler.
Regards

---

### Post by milind_iitg on 2007-12-03
Hello,
 I want to use another compiler(Intel icc) for pdebuilding the packages. icc I have not downloaded & built using 

pdebuild, but with ./configure && run. So, its not in the list of package database, eg. dpkg -l icc does not show 

anything. How I can assure its present there. Actually, I want to use icc to build other packages, but by using 

pdebuild. But pdebuild takes gcc, and gcc is recognized by the pbuilder tool, while icc does not. Is there a method 

or configuration in which I can use with Intel compiler. I tried installing pentium-builder, and then changing the 

perl script it produces, to change the gcc used to icc. Example,

@target = ("icc", @ARGV);
exec @target or die "Unable to exec @target[0]: $!\n";

I gave the full path to icc, and then tried running:--
gcc -V, gcc -help , it all runs giving intel compiler version & its help.
But when I execute compilation command like:--
gcc -c <demo.cpp>,
the exec command used in the script hangs indefinitely. The exec is not working as expected with icc.
Do I need to change anything more for the configuration to succeed properly for pentium-build.
Can pentium-build be used for compilers other than gcc. I could not find any good materials on the net regarding this. In a gist, pentium-builder is not working for me when I want to invoke other compiler.
  I can use alias also. It will show output that gcc command executes, but instead icc is executing,
but I am not sure if alias will work as expected with pdebuild, and I am not sure if the pbuilder environment will identify the alias, and I have no way to prove that gcc is aliased to icc. 
  Also, is there any other way?
Regards
Milind

---

