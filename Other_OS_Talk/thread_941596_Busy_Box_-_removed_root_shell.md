---
title: "Busy Box - removed root shell"
date: 2008-10-08
forum: Other OS Talk
---

### Post by eludlow on 2008-10-08
I think I've stupidly managed to lock myself out of the root account....

SSHd in as root, installed bash and then opened /etc/passwd to change default shell - instead of saying /opt/bin/bash I set it to /bin/bash  :oops: 

Now I obv can't login as root to change it back-  anyone got any suggestions?  Could I create a link of some sort from /bin/bash to /opt/bin/bash?

Thanks in advance.

Ed Ludlow

---

### Post by eludlow on 2008-10-08
OK problem solved - in my confusion I still had another SSH window open, logged in as root....thank god!

---

