---
title: "Firefox does not start"
date: 2019-06-20
forum: New to Ubuntu
---

### Post by crisissurya on 2019-06-20
Hello! I'm having exactly the same problem. I'm a newbie so have no idea what to do. It seems you solved the issue. Can you please help out here?

---

### Post by yetimon_64 on 2019-06-21
> **crisissurya said:**
> Hello! I'm having exactly the same problem. I'm a newbie so have no idea what to do. It seems you solved the issue. Can you please help out here?

Follow the instructions in post 3 that Impavidus posted, start firefox in terminal and post your results back here.
If you already have checked and found that libatomic1 is missing, as was the case for the OP, then in terminal issue the next command to install the missing package ...
```
sudo apt install libatomic1
```
If your problem was with libatomic1 missing, and does not include any other issues as well, firefox should now work after using the above code.

Regards, yeti.

---

### Post by wildmanne39 on 2019-06-21
Moved to own thread from here:

[https://ubuntuforums.org/showthread.php?t=2408041](https://ubuntuforums.org/showthread.php?t=2408041)

---

