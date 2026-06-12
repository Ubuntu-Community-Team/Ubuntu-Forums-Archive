---
title: "Problem Compiling LDD3 Example"
date: 2010-01-23
forum: Programming Talk
---

### Post by not_a_phd on 2010-01-23
I was working through the Linux Device Drivers 3rd Edition, and was compiling the "SCULL" example from Chapter 3. 

I ran across the following error in many places in the access.c source file:[INDENT]**error: dereferencing pointer to incomplete type**
[/INDENT]This occurred in several places, but it seems like all of them occurred where the 'current' macro is being used.

```

      (scull_u_owner != current->uid) &&   /*allow user */
       (scull_u_owner != current->euid) &&  /*allow whoever did su */

```I am using gcc 4.4.1 in Karmic.

It is clear to me that the current macro is recognized, but it is not completely defined in this source module. 

Is there a work around? Anyone?

---

### Post by Zoanie on 2010-02-08
Hi, I found your query as I was working on the same problem.  There are a large number of problems with the LDD3 source examples.  I found a great resource that should resolve all the problems.  A professor at FSU went though the problem to fix and document all of the changes required to get the examples to compile.  Check out the below links.  They really saved me a great deal of time an frustration.

[http://www.cs.fsu.edu/~baker/devices/diffs](http://www.cs.fsu.edu/~baker/devices/diffs)
[http://www.cs.fsu.edu/~baker/devices/lxr/source/2.6.25/ldd-examples/](http://www.cs.fsu.edu/~baker/devices/lxr/source/2.6.25/ldd-examples/)

---

### Post by Abhisheietk on 2010-03-07
For the linux kernal 2.6.31 there is a change in struct task_struct

so just change 
scull_u_owner != current->uid
scull_u_owner != current->euid

to
scull_u_owner != current->real_cred->uid
scull_u_owner != current->real_cred->euid

it worked for me !!

---

### Post by gramound on 2010-04-08
> **Zoanie said:**
> 
[http://www.cs.fsu.edu/~baker/devices/diffs](http://www.cs.fsu.edu/~baker/devices/diffs)
[http://www.cs.fsu.edu/~baker/devices/lxr/source/2.6.25/ldd-examples/](http://www.cs.fsu.edu/~baker/devices/lxr/source/2.6.25/ldd-examples/)


I was going crazy trying to use his "diff -r" file with the "patch" command. I gave up and used:
```

cd examples
for i in $(find .)
do
wget http://www.cs.fsu.edu/~baker/devices/lxr/source/2.6.25/ldd-examples/$i -O $i
done

```
:guitar:

---

### Post by kalad on 2010-04-14
Apart from changing (all):

scull_u_owner != current->uid
scull_u_owner != current->euid

to
scull_u_owner != current->real_cred->uid
scull_u_owner != current->real_cred->euid

I had to include:
#include <linux/sched.h>
in access.c (otherwise it was complaining about "dereferencing pointer to incomplete type").

BR

---

