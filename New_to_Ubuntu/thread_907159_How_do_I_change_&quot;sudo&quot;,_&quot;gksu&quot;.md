---
title: "How do I change &quot;sudo&quot;, &quot;gksu&quot;, and &quot;kdesu&quot; timestamp?"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by kenweill on 2008-09-01
How do I change "sudo", "gksu", and "kdesu" timestamp?

"When using sudo, the password is stored by default for 15 minutes. After that time, you will need to enter your password again."

How can i change the default settings? How can I change it to lower than 15 minutes". Or how can I change it to ask for a password everytime i wanted to run administrative commands?

---

### Post by WRDN on 2008-09-01
You need to edit the sudoers file, by opening the Terminal, and typing:

```
sudo visudo
```

You can also edit it by typing:

```
sudo nano /etc/sudoers
```

Find the line "Defaults env_reset" and add ",timestamp_timeout=5" to the end of it, so the line has been changed to:

> Defaults        env_reset,timestamp_timeout=5

If you wish you can change the number 5 to some other time. Change the timeout to 0 if you want to loose the sudo privileges immediately.

---

### Post by kenweill on 2008-09-01
Thank you very much.
It works.  :D

---

