---
title: "org.eclipse.core.jobs"
date: 2010-09-24
forum: Packaging and Compiling Programs
---

### Post by UlrihRekkenin on 2010-09-24
Hello!

When I have compiled my project I saw the message:

An internal error occurred during: "Building Workspace".
Could not find a file to match the module name: coordinate_transformations

In Error Log I saw 
```
An internal error occurred during: "Building Workspace"
```and the link to plug-in *org.eclipse.core.jobs*

If I understand exactly, the problem in the module-file "coordinate_transformations". But if I corrected it  code again and compiled project I have just one error

```
speed = sym1_to_cartesian(Sdot)
                                         1
Error: Rank mismatch in array reference at (1) (1/2)
```The primed model of my code there


```
PROGRAM trouble
double precision :: speed(3,4),  Sdot(6), sym1_to_cartesian(3,4)
...
   speed = sym1_to_cartesian(Sdot)
...
END PROGRAM trouble

```

---

