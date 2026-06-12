---
title: "Failed to run a newly built program, except chmod, what could possibly be the cause?"
date: 2010-05-31
forum: Packaging and Compiling Programs
---

### Post by jjsafeware on 2010-05-31
Background info:
after a few fiddlings with the header files, I've managed build (compile and linked) a program that depends on a few libraries such as gfortran, xercesc, motif etc.
The end program is successfully built and file attribute is changed to rwx. However, when I run it, the system simply prompts "command not Found"

The starting lines are so simple that it only shoots out some texts as follows.
cinfo << endl
      << " Hello  " << endl;

I figured that there might be some missing dependent run-time libraries like dll in Windows. However, with the command not found error, it's impossible to find out what is missing.

My question is,
Is there a way to find out what libraries are missing?
Or, is there any other cause for "command not found" except the missing libraries?

Thanks in advance for a hint!

---

### Post by gmargo on 2010-05-31
You can find out what shared libraries a program expects with "ldd program".

---

### Post by jjsafeware on 2010-06-01
Thanks a lot pal! I'll try it out.

---

### Post by SevenMachines on 2010-06-01
just a quick check in case, apologies is this is an obvious thing :)
Remember that the current working directory isnt in your system path for running executables. ie, if you have a binary 'helloworld' in your current directory then

$ helloworld
helloworld: command not found

but if you include the path as part of the command, in this case the current directory './'
$ ./helloworld
hello!!!!!

---

### Post by jjsafeware on 2010-06-01
Yes you're right, it worked now. thanks a lot 7machines.
To look for shared libraries, getlibs works better.

---

