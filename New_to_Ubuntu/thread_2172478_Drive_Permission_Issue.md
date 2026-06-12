---
title: "Drive Permission Issue"
date: 2013-09-05
forum: New to Ubuntu
---

### Post by narendra4 on 2013-09-05
Hello, I have Recently installed Ubuntu in my Dell Inspiron 1545. but now one of the free partition of 199gb does not allow to copy paste any data in that. I have checked the permission also it shows You are not root so u can not access permission.what should i do?

---

### Post by AnotherBrian on 2013-09-05
ctrl-alt-T will get you terminal. 
Then do 
sudo nautilus

do whatever your heart desires.

---

### Post by nativehound on 2013-09-05
Best to alway use ```
gksudo
``` when launching a GUI with elevated privileges.

---

### Post by narendra4 on 2013-09-05
Thanks for you help but i am new to linux. will you please ellaborate on same?
I have attached image showing the permission window.

---

### Post by nerdtron on 2013-09-05
Hit Ctrl+Alt+T
When you open a Terminal window (a command line) type:

```
gksudo nautilus
```

You'll be asked for a password. Then you can do anything you want using that nautilus window.

---

### Post by narendra4 on 2013-09-05
yeah I got that thank you buddy

---

