---
title: "Asking for sudo when a program starts (visually)"
date: 2005-11-08
forum: Programming Talk
---

### Post by mitchy_g on 2005-11-08
Hi,
I am wondering how I can ask the user of a program to input the password for 'sudo' when it is needed at startup or whenever. Much like when Synaptic is started from the top menu bar, it brings up a small dialog asking for the password.

Thanks
Mitch :)

---

### Post by 23meg on 2005-11-08
Use "gksudo".

---

### Post by mitchy_g on 2005-11-09
23meg,
Thanks for you reply, do you have any idea how to use gksudo from another program in C, im using gtk to create the application.

Thanks Again
Mitch

---

### Post by darth_vector on 2005-11-09
use the

execvp(char* full_path_of_command,char** argument_list)

---

