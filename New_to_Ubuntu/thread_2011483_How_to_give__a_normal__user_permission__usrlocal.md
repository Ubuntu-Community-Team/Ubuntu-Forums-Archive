---
title: "How to give  a normal  user permission  /usr/local"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by ravipuram on 2012-06-27
How to give  a normal  user permission  /usr/local 

What is the pros and cons 

What is the best practice 

Creating a user group and adding to them

---

### Post by SeijiSensei on 2012-06-27
Permission to do what exactly?  Ordinary users can run programs in /usr/local/bin with libraries in /usr/local/lib and configurations in /usr/local/etc?  Do you want to let ordinary users write into /usr/local?  I'd say that's generally a bad idea for the same reasons we don't let ordinary users write into /usr. 

Why kind of access to /usr/local are you talking about, writing files?  I'd do that sparingly and only into selected directories.  If you want to let users compile in /usr/local/src, for instance, you could create a compiler group, put those users in that group, and change the ownership of /usr/local/src to root:compiler with permissions 775.  If they had permission to write into all of /usr/local, they could also run "make install", not something I'd allow ordinary users to do.  After the compilation in /usr/local/src was finished and tested, I'd require someone with root privileges to review the result and, if approved, run "make install".

---

### Post by ravipuram on 2012-06-27
I want to give permission to a user on Permission on /usr/local to compile

---

### Post by Gone fishing on 2012-06-27
sorry more detail - I would have thought you could use sudo -i  to open a root terminal then navigate to the directory cd /home/user/compile_directory and then compile.

---

### Post by coffeecat on 2012-06-27
Threads merged.

One thread per issue, please.

---

### Post by ravipuram on 2012-06-27
Thanks Seijisensei

the user is a standard user, i want to give privilege to compile source code  in the  usr/local/ directory 

Adding  "usr1  ALL= /usr/local " this line in sudoers  will help 

if i add the above line in the  sudoers  , i am afraid the user will be over privileged . Actually i want to set least privilege


[COLOR="Black"]Seijisensi[/COLOR]

**If they had permission to write into all of /usr/local, they could also run "make install", **

No the user is a just a standard user 


[B]" you could create a compiler group, put those users in that group, and change the ownership of /usr/local/src to root:compiler with permissions 775."
[/B]
Please provide some examples

---

### Post by Cheesemill on 2012-06-27
> **ravipuram said:**
> Adding  "usr1  ALL= /usr/local " this line in sudoers  will help 

if i add the above line in the  sudoers  , i am afraid the user will be over privileged . Actually i want to set least privilege

That's not even a valid sudoers entry.

Entry's in the sudoers file have to point to a specific application, /usr/local is a directory.

---

### Post by ravipuram on 2012-06-27
Sow how to give  permission for a user  to write into all of /usr/local,

---

### Post by Gone fishing on 2012-06-28
I'm not sure about the security of this you don't trust the user to be in sudoers but you want them to be able to compile a run programs that will effect the whole system, will that not in effect give them the root privileges necessary to trash the box?

Why not run virtualbox in their account and give them their own Ubuntu inside the virtualbox and then make them administrator?

---

