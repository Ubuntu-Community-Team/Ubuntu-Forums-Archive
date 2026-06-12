---
title: "Making source commands operate on boot-up."
date: 2012-05-01
forum: New to Ubuntu
---

### Post by newport_j on 2012-05-01
Is there a way to have a source command such as 
 
source ... ia32
 
run automatcally upon booting the Ubuntu pc up?
 
I run a source command every day, sometimes several times a day (usually when the system goes to screensaver and is then unlocked), I must re-enter the source ... ia32 command. That seems unnecessary. Once on boot-up should be enough, so how do I modify a file (and which file do I modify) to make this happen on boot up and make it permanent? 
 
Thanks in advance.
 
Newport_j

---

### Post by codemaniac on 2012-05-01
Add your **source **command to the system file /etc/rc.local.
```
echo '/path/to/your/command' >> /etc/rc.local
```

---

