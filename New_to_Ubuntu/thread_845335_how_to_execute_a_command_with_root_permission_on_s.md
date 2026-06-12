---
title: "how to execute a command with root permission on startup?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by legolas_w on 2008-06-30
Hi
Thank you for reading my post
some commands need to have root permission to be executed and we use sudo or gksudo to execute them.

now how I can make execution of these kind of command automatic? for example in system startup?

thanks

---

### Post by sisco311 on 2008-06-30
Just put the commands in the /etc/rc.local file and make sure the file has execute permission. The script is executed at the end of each multiuser runlevel.

---

