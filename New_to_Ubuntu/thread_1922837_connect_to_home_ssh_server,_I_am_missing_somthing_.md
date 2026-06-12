---
title: "connect to home ssh server, I am missing somthing obvious..."
date: 2012-02-09
forum: New to Ubuntu
---

### Post by john1923 on 2012-02-09
This is one of those problems where I don't know a piece of assumed knowledge, so I am not understanding the How To guides.

I have set up ssh on one of my computers at home. I can log into it from within my home network by typing 

```
ssh username@IPadressOfServer
```This works fine.

How do I access my server from outside my home network?

As I understand it all of my home computers have the same external ip address, so I need to specifiy that IP address then my individual machine's IP address? 

Is this right, and what does the command look like. Or is there a better way of doing it?

Thanks in advance.

All computers have Ubuntu 10.04 LTS.

---

### Post by lechien73 on 2012-02-09
To do this from outside, you would need to forward tcp port 22 from your Internet router to port 22 of the IP address of the home server. How to do this depends on your specific Internet router.

When you have, then you can connect from outside with:

```
ssh username@external-ip-address
```

---

### Post by john1923 on 2012-02-09
Thank you, that makes a lot of sense.

---

### Post by hovzio on 2012-02-09
If your not bound by a static IP it's also easiest to use a service such as dyndns.org or something along those lines and then point your router/gateway at that.. For example, my provider changes my ip everyday at 12:00.. with dnydns I can always use a regular url and dyndns will point that url to my dynamic ip.. hope that helps.

---

### Post by Rafterman414 on 2012-02-09
> **hovzio said:**
> If your not bound by a static IP it's also easiest to use a service such as dyndns.org or something along those lines and then point your router/gateway at that.. For example, my provider changes my ip everyday at 12:00.. with dnydns I can always use a regular url and dyndns will point that url to my dynamic ip.. hope that helps.

In the past I too have used dyndns and it worked nicely. I have not used it in awhile but I recently read that it is no longer free. Is this true? Another service that offers something similar is no-ip.

---

