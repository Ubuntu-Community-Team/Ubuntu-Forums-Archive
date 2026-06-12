---
title: "Ssh"
date: 2014-02-08
forum: New to Ubuntu
---

### Post by john148 on 2014-02-08
Hi everyone,  I am trying to download ssh-server and for some reason all the files give me an error.  I attached the screenshot.  I cannot figure out what is going on.  Thank you for the help in advance,

John

[ATTACH=CONFIG]250189[/ATTACH]

---

### Post by deadflowr on 2014-02-08
What's the output for
```
sudo apt-get update
```
If no errors come up, try installing ssh again.

---

### Post by john148 on 2014-02-08
I tried the update and same thing

---

### Post by deadflowr on 2014-02-08
What about
```
sudo apt-get upgrade
```

---

### Post by llamabr on 2014-02-08
It looks like you're not online.  post the output of:
```
sudo apt-get upgrade
```

---

### Post by prasys on 2014-02-09
It looks like you are having issues with connectivity. Are you connected to the Internet ?

Try by pinging 

```
 ping google.com 
```

Alternatively you may follow suggestion given by llamabr/deadflowr

---

