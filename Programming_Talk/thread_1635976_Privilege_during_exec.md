---
title: "Privilege during exec"
date: 2010-12-02
forum: Programming Talk
---

### Post by TennTux on 2010-12-02
There is a command that I run on a regular basis with one of two sets of parameters. To run with these parameters requires root privilege. I would set the sticky bit but that would open an unnecessary security hole. However, I am comfortable with giving just these two sets for parameters privilege.

So, I wrote a simple C++ application that checks for one of two values on the command line and *exec*'s the real command with the fixed parameters. I was then able to set the sticky bit *chmod u+s xyz* and this worked in Ubuntu 10.04. However, I have installed Ubuntu 10.10 from scratch and I'm now getting errors that amount to the *exec*'d command not having root privilege.

I'm still getting my system up to speed so don't have all my documentation up to date yet. I suspect, when I exec, I have to explicitly pass on privilege as a safe guard against security leaks.

Would somebody point me in the right direction.

---

### Post by ziekfiguur on 2010-12-03
Wouldn't it be easier to just allow the commands, with fixed parameters, to be run with root privileges in the sudoers file?

---

### Post by TennTux on 2010-12-03
> **ziekfiguur said:**
> Wouldn't it be easier to just allow the commands, with fixed parameters, to be run with root privileges in the sudoers file?

It was my impression that the sudoers file specified what commands a given user could invoke as super user. My issue is also one of abbreviating a command and limiting the need to provide a password for "sudo".

I can currently run "sudo command 'with all' 'the parameters' 'and provide' 'a password' 'to boot'" or I can run "mycommand do" and "mycommand undo". Call me lazy but sometimes stopping to remember all the parameters and fixing typos is a pain.

Or did I misunderstand your post or what sodoers does? :)

---

### Post by ziekfiguur on 2010-12-06
No, you're right, if you're to lazy to type sudo you shouldn't use the sudoers file.
The s bit makes it possible to run the executable with the pivileges of its owner, so you should check if the file is owned by root. (and than set the s bit again, 'cause it's reset by chown)

---

