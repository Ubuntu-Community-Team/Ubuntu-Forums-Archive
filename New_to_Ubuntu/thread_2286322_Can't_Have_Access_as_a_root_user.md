---
title: "Can't Have Access as a root user"
date: 2015-07-11
forum: New to Ubuntu
---

### Post by chuks3 on 2015-07-11
Please how do i add my root user name to sudeors file in my Ubuntu operating system ? I am new to Linux and i was doing some experiment with my terminal and i think i mistakenly remove my root user details from sudoers file. And because of that, i can not have access as a root user now.

---

### Post by Vladlenin5000 on 2015-07-11
Hi and welcome.
What do you mean by "access as root user"? The first user in an installed system is, by default, in that group. And whenever elevated privileges are needed you should precede your command by "sudo".
Try it with any 'neutral' command like, for example, ```
sudo apt-get update
```.
If you really messed up your system, an error message saying you aren't part of that group should appear.

---

### Post by oldos2er on 2015-07-11
Please tell us exactly what you entered into the terminal.

Ubuntu doesn't have a root account by default. While you can add one, it's unnecessary and subverts Ubuntu's security model; see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more info.

---

