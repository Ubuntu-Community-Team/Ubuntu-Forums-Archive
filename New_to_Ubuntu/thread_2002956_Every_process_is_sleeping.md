---
title: "Every process is sleeping"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by deejaylight on 2012-06-13
Hi Guys!
Please help!
I have the same problem with skype and ubuntu 12.04.
Every about 30min it gets blocked in this futex_wait_queue_me.

Please if someone know what is the problem please let me know.
Or help me to troubleshoot this problem.

I would appreciate your help.

Thank you very much

---

### Post by oldos2er on 2012-06-13
Post moved to its own thread.

---

### Post by Redblade20XX on 2012-06-13
> **deejaylight said:**
> Hi Guys!
Please help!
I have the same problem with skype and ubuntu 12.04.
Every about 30min it gets blocked in this futex_wait_queue_me.

Please if someone know what is the problem please let me know.
Or help me to troubleshoot this problem.

I would appreciate your help.

Thank you very much

So what happens? Skype fails to respond? 

The  futex_wait_queue_me is a part of the process management system
and you'll most likely see most programs sleeping because they are being
state switched very quickly.

-Red

---

