---
title: "A simple add usr script"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by dennyaaa on 2012-01-02
So, I am doing a little exercise with some basic Linux scripting and was wondering if there is any simple way to make a script that adds a new user to the passwd file in Ubuntu 11.10? Complete with his/hers own password, home dir and all the other feats that a new user gets from the GUI add system.

Thanks in advance :)

---

### Post by sisco311 on 2012-01-02
Hi and welcome to the forums!

You can use the **adduser** command (See: **man adduser**). 


Other commands for managing users and groups are:

**useradd** - low level utility for adding users
**groupadd** - create group
**usermod** - modify a user account
**groupmod** - modify a group definition on the system
**adduser, addgroup** - On Debian and Ubuntu they are front ends to the low level tools like useradd, groupadd and usermod
**userdel** - delete a user account and related files
**groupdel** - delete a group
**deluser, delgroup** - On Debian and Ubuntu they are front ends to the low level tools like userdel and groupdel
**gpasswd** - administer /etc/group and /etc/gshadow
**passwd** - change user password
**chfn** - change real user name and information
**chsh** - change login shell
**vipw, vigr** - edit the password, group, shadow-password or shadow-group file

The files which store local user informations are:

/etc/passwd - the password file (see: **man 5 passwd**)
/etc/shadow - the shadowed password file (see: **man 5 shadow**)
/etc/group - group file (see: **man 5 group**)
/etc/gshadow - the shadowed group file (see: **man 5 gshadow**)

---

### Post by dennyaaa on 2012-01-03
Thanks for the reply sisco311. But I am looking for a more specific walkthrough on how to write a simple script. I have been trying alot the last 2 days and I really cant seem to get it to work since I am totally new to the script language :)

---

### Post by Lars Noodén on 2012-01-03
Which scripting language?

If you mean Bash, then here are some places to start:

[http://mywiki.wooledge.org/BashGuide/](http://mywiki.wooledge.org/BashGuide/)
[http://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by dennyaaa on 2012-01-03
Thanks, will give it a look :)

---

### Post by Lars Noodén on 2012-01-03
You can also do scripting in python or perl.  Many systems scripts are written in either scripting language.

---

