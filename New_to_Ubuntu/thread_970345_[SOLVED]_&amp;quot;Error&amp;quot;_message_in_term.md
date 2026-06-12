---
title: "[SOLVED] &amp;quot;Error&amp;quot; message in terminal window"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Beth1957 on 2008-11-04
My husband re-did my network settings yesterday and since then I've been getting the following message in the terminal window:-

```
liz@liz-laptop:~$ sudo modprobe -r ehci_hcd
sudo: unable to resolve host liz-laptop
[sudo] password for liz: 
```

It's not a huge deal, as it seems that whatever command I put in works anyway - however, I find it slightly worrying in case it's a symptom of something drastically wrong!

Any advice, please?
I'm running HH.
Thanks,

---

### Post by prshah on 2008-11-04
> **Beth1957 said:**
> 
```
liz@liz-laptop:~$ sudo modprobe -r ehci_hcd
sudo: unable to resolve host liz-laptop
[sudo] password for liz: 
```


Check your /etc/hosts file; it should contain an entry similar to ```
127.0.0.1 liz-laptop
``` If it's not there, exactly as shown above, add it, but don't disturb any other settings already in there. If you find a wrong looking entry for liz-laptop (eg, liz-laptop.localhost), change it.

If you have doubts about what to change / add, post the contents of your /etc/hosts file, and correct hostname.```
cat /etc/hosts
hostname
```

Post back if you still have trouble.

---

### Post by Beth1957 on 2008-11-09
Cheers... yes, my husband had changed the host name to try to network my laptop. I'm all sorted now! Thank you.

---

