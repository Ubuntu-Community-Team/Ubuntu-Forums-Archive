---
title: "portable chromium in ubuntu?"
date: 2018-01-06
forum: New to Ubuntu
---

### Post by dave1710 on 2018-01-06
hi, I have been looking for a portable version of chromium or google chrome in ubuntu but I haven't been able to find one, I need to use two proxies at the same time that's why I need a portable version, the ones I have found are too old , Is there any version like this around ? any other solution ?

---

### Post by TheFu on 2018-01-06
A few other solutions.

Chromium supports specifying the proxy at runtime on the command line.  **--proxy-server=host:port** The manpage has more information.

Also, you can run multiple separate instances using either a container, virtual machine or a cname management tool like firejail.  I use **firejail** all the time, usually in --private mode.

---

### Post by dave1710 on 2018-01-08
I'm going to try that, thanks.

---

### Post by TheFu on 2018-01-08
> **dave1710 said:**
> I'm going to try that, thanks.

If this is solved, please post how you decided to do it and how well it worked.  Then mark the thread as 'solved' using the thread tools above. All of this helps the community. Chances are that you aren't the only person with the same question.

---

