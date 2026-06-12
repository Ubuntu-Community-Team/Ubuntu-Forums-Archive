---
title: "How to run command that need root  privileges?"
date: 2011-06-20
forum: Programming Talk
---

### Post by leon.vitanos on 2011-06-20
Hi! I run a simple command at c++ like this:

 ```
if(system("COMMAND HERE`"))
     cerr << "Error while trying to use command 'COMMAND' into the specified folder! Check folder's permissions etc.\n";
```But how to run a command that needs root privileges?
Probably i should show an Authentication Dialog like this:

```
pkexec echo
```I don't know.. :???:

---

### Post by leon.vitanos on 2011-06-20
Ok i found it.. It is gksudo! :D

---

### Post by Petrolea on 2011-06-20
> **Bong.Da.City said:**
> Ok i found it.. It is gksudo! :D

If you want it to execute the program as root all by itself, without a password prompt you could echo the password and use a pipe to transfer it to your program.

---

### Post by lavinog on 2011-06-21
> **Petrolea said:**
> If you want it to execute the program as root all by itself, without a password prompt you could echo the password and use a pipe to transfer it to your program.

That is generally a bad idea.
Even if the program gets compiled, you can usually extract strings.

Also, root passwords should be changed every now and then, which would mean that you would have to keep your application up to date...to do that you need to keep the source code available...in plain text :eek:

---

