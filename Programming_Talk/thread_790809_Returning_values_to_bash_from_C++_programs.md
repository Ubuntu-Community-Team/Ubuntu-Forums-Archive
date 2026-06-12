---
title: "Returning values to bash from C++ programs"
date: 2008-05-11
forum: Programming Talk
---

### Post by rohitsb on 2008-05-11
Hello,

Since I've started experimenting with Linux/Ubuntu, I've developed a C++ program for date arithmetic. I plan to run the program in a bash shell script to accept a base date and number of days to add/subtract as command line arguments. 

I would like the program to return the resultant date back to the shell. Any ideas on how to do this ?

FYI, I've already tried setenv() and putenv(). setenv() works within the scope of the program, but the change to the environment variable is not reflected after the program terminates.

Thanks
RSB

---

### Post by dtmilano on 2008-05-11
Use stdout, i.e.:
> cout << results << endl;

---

### Post by Replicon on 2008-05-11
Yup, if you output to stdout, and in your script, call it with backticks (e.g. FOO=`mydatethingger`), it'll do what you want (might have to put that through a regex or something, but that's easy).

---

### Post by rohitsb on 2008-05-11
Thanks dtmilano!! It worked...

---

