---
title: "Script in /etc/network/if-up.d/ isn't getting run"
date: 2021-03-04
forum: New to Ubuntu
---

### Post by vbensch on 2021-03-04
Title says it all. I have an executable script in the /etc/network/if-up.d/ folder. If I run sudo /etc/network/ifup.d/myscript it runs just fine, but it doesn't ever trigger on its own. I have googled the issue, but can't seem to figure out what I am doing differently from people for whom placing their runtime scripts there works. I am running 20.04.2 LTS.

---

### Post by TheFu on 2021-03-04
20.04 uses netplan.  ifupdown was deprecated.
[https://ubuntu.com/server/docs/network-configuration](https://ubuntu.com/server/docs/network-configuration)

---

### Post by ActionParsnip on 2021-03-05
What is the output of:
```

ls -la /etc/network/ifup.d/myscript

```
Please. 
Also, did you specify the shell using shebang at the top of the script as well?

---

