---
title: "can any help what does this mean ......."
date: 2011-12-09
forum: New to Ubuntu
---

### Post by blake7 on 2011-12-09
users/window~1/appdata/local/temp/wubi-11.10-rev241.log


iam trying to load this into window and this keeps coming up can you hellp

thank you

---

### Post by lisati on 2011-12-09
Did you install Ubuntu using Wubi?

"users/window~1/appdata/local/temp/" is likely your Windows system's %temp% directory, and "wubi-11.10-rev241.log" refers to wubi's log file. There might be an entry in the log file that can help you troubleshoot your system.

---

### Post by blake7 on 2011-12-09
[quote=lisati]
Did you install Ubuntu using Wubi?

"users/window~1/appdata/local/temp/" is likely your Windows system's %temp% directory, and "wubi-11.10-rev241.log" refers to wubi's log file. There might be an entry in the log file that can help you troubleshoot your system.[/quote]

where do i find this log file and what would i do next????


thank you

---

### Post by lisati on 2011-12-09
> **blake7 said:**
> where do i find this log file and what would i do next????


thank you

If you were trying to install Ubuntu "within" Windows - which is what wubi does - you will be able to find the log by clicking on Start->run, typing in
```
%temp%
``` and then pressing enter.

---

### Post by blake7 on 2011-12-09
would this effect a ubuntu if i was to wipe windoows????

i repalced it with ubuntu complete??

---

### Post by lisati on 2011-12-09
> **blake7 said:**
> would this effect a ubuntu if i was to wipe windoows????

i repalced it with ubuntu complete??

Short answer: yes.

If you look [here]("http://ubuntuforums.org/showthread.php?t=1519354"), you will find instructions for moving your Ubuntu installation to its own partition.

---

### Post by Rubi1200 on 2011-12-10
Whatever you decide to do, make sure all important files are backed up first!!!

---

