---
title: "cannot load software"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by LinuxFred on 2012-06-08
Hi I am new to linux download ubuntu have been trying to load XAMPP get as far as unzip end of line is -C/opt this is when the terminal freezes after a couple of hours restarting it going into the opt directory I find nothing there this has happened with Chrome as well. Can any one help me get started? please, please.

---

### Post by r7m on 2012-06-08
Can you copy/paste exactly what is in the terminal when this happens?

---

### Post by kanikilu on 2012-06-08
Also, how are you trying to extract this to /opt? The official XAMPP for Linux instructions say to use **su** to login as root, but that won't work on Ubuntu unless you enable root - which isn't supported here, and isn't necessary in this case. Just do:

```
sudo tar xvfz xampp-linux-1.7.7.tar.gz -C /opt
```

Going by your first post, maybe you forgot the space between -C and /opt??

---

