---
title: "ssh problem"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Foxfire on 2008-07-05
When using my laptop I can see and share with my Desktop.  But I cant see or share from my Desktop to my laptop

---

### Post by cariboo on 2008-07-05
Ssh is not your problem, you didn't say which computer had Ubuntu on it. You need to install samba on the computer that Ubuntu is installed on in order to share files. See this guide here:

[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

Jim

---

### Post by JillSwift on 2008-07-05
You can share files via ssh as well, Cariboo.

Foxfire, make sure your laptop is running the ssh daemon. I'm fair sure by default that's not running (may not even be installed.)

---

### Post by Vivaldi Gloria on 2008-07-05
> **Foxfire said:**
> When using my laptop I can see and share with my Desktop.  But I cant see or share from my Desktop to my laptop

You have not given much info, have you? Is ssh-server installed? Is sshd running? What error messages do you get? What happens when you give the command

```
ssh localhost
```

in your desktop?

---

### Post by frankos44 on 2008-07-05
On laptop assuming its running Ubuntu

$ sudo apt-get install openssh-server

---

### Post by hyper_ch on 2008-07-05
I don't understand the problem...

how do you want to share? where do you fail? how can you access the other one?

---

