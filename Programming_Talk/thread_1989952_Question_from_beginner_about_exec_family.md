---
title: "Question from beginner about exec family"
date: 2012-05-29
forum: Programming Talk
---

### Post by MaximusGlory on 2012-05-29
Hi. I am new to C programming on Ubuntu. 

My question is, after forking a new process, which call from the exec family can I use to execute a file with options and any other related arguments - for instance, a command from the /bin directory? By accepting arguments from the command line, using argc and argv, I can execute commands, like 'ls' and 'date', with no options, using execlp. I was wondering which exec call to use if I wanted to execute something like 'ps aux'? 

Thanks.

---

### Post by nothingspecial on 2012-05-29
*Thread moved to **Programming Talk**.*

---

### Post by Bachstelze on 2012-05-29
Have you read the manual page for execlp()?

---

