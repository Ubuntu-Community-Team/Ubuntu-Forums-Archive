---
title: "[SOLVED] Add directory to linux command search"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by katsu_ishii on 2008-07-29
When I type 'ls' in the command line, Linux searches through a list of directories to find the executable named 'ls'. How can I add directories to the list?

---

### Post by ktrnka on 2008-07-29
I think what you want is to add the directory of the executable in /etc/environment

---

### Post by fatality_uk on 2008-07-29
The **ls** is used to list directory contents. It will show, all files and directories. For instance it will show directories, by default I think as blue entries. Executables are green. 
In a terminal type **man ls** for a copy of the manual relating to the ls command.

---

### Post by ilrudie on 2008-07-29
> **katsu_ishii said:**
> When I type 'ls' in the command line, Linux searches through a list of directories to find the executable named 'ls'. How can I add directories to the list?

Actually linux does not do that.  Your shell does that.  You want to add a directory to the path variable in your shell.  Alternatively you can edit /etc/environment to make the change for all users.  

To make the change just for you add ```
export PATH=$PATH:<your_new_path>
``` to ~/.bashrc (if you use bash) or ~/.profile (if you use ksh or sh)

---

