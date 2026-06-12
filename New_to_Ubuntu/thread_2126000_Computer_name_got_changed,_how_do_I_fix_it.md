---
title: "Computer name got changed, how do I fix it?"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by jemvyc on 2013-03-15
In the process of updating to Ubuntu 12.10, my computer's name got changed.  I'm sure I must have done it, but how do I fix it?

Thanks

Jim

---

### Post by plucky on 2013-03-15
> **jemvyc said:**
> In the process of updating to Ubuntu 12.10, my computer's name got changed.  I'm sure I must have done it, but how do I fix it?

Thanks

Jim

Open a terminal and run ```
gksudo gedit /etc/hosts /etc/hostname
``` and change the hostname in both of those files.Save then reboot.

Good Luck

---

### Post by jemvyc on 2013-03-16
Thanks.  

I knew it must be something simple.  I just could not find it.

Jim

---

### Post by SuperFreak on 2013-03-16
Not meaning to hijack this thread, but out of interest by changing the computer name does this change the prompt at the terminal or the login name?

---

### Post by plucky on 2013-03-17
> **SuperFreak said:**
> Not meaning to hijack this thread, but out of interest by changing the computer name does this change the prompt at the terminal or the login name?

Prompt at terminal is "username@computer name" so the computer name will change but the username remains the same.

Good Luck

---

### Post by SuperFreak on 2013-03-17
thanks

---

