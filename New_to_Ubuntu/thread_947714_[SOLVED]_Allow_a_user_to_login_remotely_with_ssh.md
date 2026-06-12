---
title: "[SOLVED] Allow a user to login remotely with ssh"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by Hospadar on 2008-10-14
I have a server/myth machine that I administer over ssh.  I have no trouble ssh-ing into my machine from anywhere, local network, outside, etc.  What I want to do is create a guest account so friends can use the machine when they need.

I added a user on the command line ```
 adduser guest 
``` and set a password.

What do I need to do to allow them ssh access? modify some ssh config file?  add them to some group?

Thanks for the help

Luke

---

### Post by Hospadar on 2008-10-14
Used useradd instead of adduser and the files in /etc/skel got copied over correctly so I could log in.

---

