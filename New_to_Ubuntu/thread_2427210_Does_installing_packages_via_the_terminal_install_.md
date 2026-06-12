---
title: "Does installing packages via the terminal install globally?"
date: 2019-09-19
forum: New to Ubuntu
---

### Post by tianbuntu on 2019-09-19
When I install some programs via the terminal, such as gfortran or python. Or when I am installing python packages using pip.

Do the programs and packages install globally for all users?

If so, how do I ensure that I am installing the packages only for my own user?

---

### Post by TheFu on 2019-09-19
All APT package management installs for everyone by default. It doesn't matter if it is CLI or GUI interface.
To limit which users can run any program, use normal Unix file/directory permissions.

I know very little about pip, but there are tools like pyenv, which would install for 1 user only and require that useid to control which version of python and which python modules are available to the user.

---

### Post by tianbuntu on 2019-09-19
You mean to say that the /usr/ directory is shared by everyone?

---

### Post by TheFu on 2019-09-20
> **tianbuntu said:**
> You mean to say that the /usr/ directory is shared by everyone?

That isn't what I meant to say, but it is true and all user accounts have at least read-only access to those files.

If you are interested in the *file system hierarchy*, there is a standards document which explains which files go where and why.  Wikipedia has a summary article with a table which has always been sufficient for my needs. Google finds it easily.
 
Every command on any Unix machine should have a manpage which explains, in detail, how each command, allowed options, should work.  **man apt-get**, for example.

---

