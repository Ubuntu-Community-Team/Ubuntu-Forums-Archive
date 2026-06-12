---
title: "Scripting and the Shell"
date: 2007-03-04
forum: Programming Talk
---

### Post by JELO on 2007-03-04
Hello all,
I recently began studying bash scripting.  What i'm trying to do is write a script that will basically take a function given by the user and solve it.
What I'm having trouble with is converting a string into an actual function to be evaluated.  What I've done so far probably isn't the best way.   Any other more sound method?

 #!/bin/bash
 echo Please, enter a function
 declare -i NAME x=2 result
 read NAME
 result=$NAME
 echo $result

I'm also wondering how I could go about using the declare statement to declare floats instead of integers as I've done so far, I haven't been able t find anything about it.  Is there a way to include cos, sin, tan in bash?  Maybe you guys know of a great tutorial.
Thanks

---

### Post by Mr. C. on 2007-03-04
The shell knows nothing about floats.  Integer only.

$ man eval
$ man bc

MrC

---

