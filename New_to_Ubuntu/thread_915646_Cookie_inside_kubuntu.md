---
title: "Cookie inside kubuntu"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by salty_steven on 2008-09-10
I recently wrote a script that set cookie. May I know where can i locate the cookie? I'm using kubuntu as the OS and Firefox. Thanks to those who help....

---

### Post by iaculallad on 2008-09-10
> **salty_steven said:**
> I recently wrote a script that set cookie. May I know where can i locate the cookie? I'm using kubuntu as the OS and Firefox. Thanks to those who help....

Firefox stores it's cookies in a single file (cookies.txt). One cookie per line. You can find the cooking file by using the command below:

```
locate cookies.txt
```

Usually located in your /home/your_username/.mozilla/firefox folder.

---

