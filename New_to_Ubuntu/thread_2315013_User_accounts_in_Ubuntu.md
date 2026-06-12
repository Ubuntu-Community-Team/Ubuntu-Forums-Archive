---
title: "User accounts in Ubuntu"
date: 2016-02-25
forum: New to Ubuntu
---

### Post by krishna19 on 2016-02-25
Hi All,


I am a newbie to the Linux world. :)


I was trying to list all the user accounts created in my Ubuntu box.


ubuntu@host:~$ cut -d: -f1 /etc/passwd
root
daemon
bin
sys
sync
games
man
lp
mail
news
uucp
proxy
www-data
backup
list
irc
gnats
nobody
libuuid
syslog
messagebus
landscape
sshd
pollinate
ubuntu


I see a lot of user account created in the machine even like sshd and syslog. What's the use of those accounts?


Krishna

---

### Post by krishna19 on 2016-02-26
Any help would be appreciated.

---

### Post by bab1 on 2016-02-26
> **krishna19 said:**
> Any help would be appreciated.For the most part they are system users rather than mortal users (humans).  The are needed to run processes or access system files.

---

### Post by DuckHook on 2016-02-26
> **krishna19 said:**
> Any help would be appreciated.The way I understand it, Linux fine tunes usage privileges, even for admin and behind-the-scene tasks, by creating a pseudo-user for it and then restricting the privileges for that pseudo-user to only that task. For example, the man "user" has only enough privilege to bring up man pages and nothing else, because it has no business accessing anything else. Hence the zoo of "users" in your passwd file. They aren't actual flesh-and-blood users, and are perhaps a workaround inherited from the days when some developer invented this method as the easiest hack for solving the problem of privilege assignment. This is all just an educated guess on my part, so please don't go treating it as gospel.

---

