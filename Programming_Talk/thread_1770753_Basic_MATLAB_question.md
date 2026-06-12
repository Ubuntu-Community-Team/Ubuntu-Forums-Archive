---
title: "Basic MATLAB question"
date: 2011-05-29
forum: Programming Talk
---

### Post by GammaPoint on 2011-05-29
I'm trying to modify some MATLAB code that someone else has written (I don't really know MATLAB, just Python and FORTRAN) and am getting confused as to why some of the changes I made aren't doing what they are supposed to do. It has to do with running UNIX commands with MATLAB. 

For example I run the command :
```

[nothing,tline] = unix(['echo ' ORG_STRUC.commandExecutable{POP_STRUC.POPULATION(Ind_No).Step} ' >> debugfile']);

```

and it writes the 'ORG_STRUC.command......" variable (which is just a short string) into my ASCII file called debugfile as expected. However, then I do the following:

```

[nothing, tline] = unix(['qsub ' ORG_STRUC.commandExecutable{POP_STRUC.POPULATION(Ind_No).Step} ]);
disp(tline);
disp(class(tline));

```

This submits a job to the supercomputer and returns a string into the variable tline, which is correctly printed by MATLAB when I type disp(tline) and it is of type CHAR as shown by disp(class(tline)). But, when I try to ECHO this variable out to a separate file as I did in the first section of code, like this

```

[nothing,rline] = unix(['echo ' tline ' >> debugfile']);

```

absolutely nothing is printed. How can this be? Am I missing something subtle? Thanks so much in advance for the help!

---

