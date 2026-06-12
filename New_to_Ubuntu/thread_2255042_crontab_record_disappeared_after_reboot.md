---
title: "crontab record disappeared after reboot"
date: 2014-12-01
forum: New to Ubuntu
---

### Post by marchello_lippi2 on 2014-12-01
Hi all, 

I created crontab record and it worked fine. 
Now crontab record disappeared after reboot. 
How can it be and how to solve?

---

### Post by ian-weisser on 2014-12-01
Were you using a Guest account?
Or a non-persistent Live environment?
Are you logging in as the same user?
Are you looking in the correct location?
Did you install something else that deletes crontabs?

---

### Post by marchello_lippi2 on 2014-12-02
> Were you using a Guest account?

No. 

>Or a non-persistent Live environment?

Don't know what is it honestly. 

> Are you logging in as the same user?

Yes. 

> Are you looking in the correct location?

I just tried to perform "crontab -l" to see my record that I set yesterday, it is absent now. 

> Did you install something else that deletes crontabs?

I can only think about anacron. Does it delete crontabs?

---

### Post by steeldriver on 2014-12-02
Did you create a user-crontab or a root crontab (i.e. **sudo** crontab -e ...)?

---

### Post by marchello_lippi2 on 2014-12-02
> **steeldriver said:**
> Did you create a user-crontab or a root crontab (i.e. **sudo** crontab -e ...)?


Both, first time it was crontab -e and second time it was sudo crontab -e and both disappeared somehow.

---

### Post by ian-weisser on 2014-12-02
Does anything else vanish or revert?
Downloaded files? Data? Settings?

---

### Post by marchello_lippi2 on 2014-12-02
> **ian-weisser said:**
> Does anything else vanish or revert?
Downloaded files? Data? Settings?

Nope, only crontab records under root and my unprivileged user. Wierd...

---

### Post by ian-weisser on 2014-12-02
Weird indeed.
I have never seen a problem like that before.

Were I investigating (and grasping at straws), I would create a fresh cron job that writes a log entry.
Then, when the log entries cease, I would know the time of vanishing.
Perhaps the vanishing can be correlated with another event.

---

