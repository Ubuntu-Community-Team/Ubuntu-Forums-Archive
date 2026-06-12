---
title: "Mozilla Firefox Freeze"
date: 2017-06-02
forum: New to Ubuntu
---

### Post by sed_faster on 2017-06-02
Some times my firefox freeze and I need reboot all my system to fix this problem!
My version is 53.0.2 (64bits).

When occur this I can't resolve through kill -9 pid or do this from "system tools"->"task manager". I simply need reboot all system!

My system is:

1-https://www.asus.com/Motherboards/PRIME-B250-PRO/
2-I5 7500
3-8Gb Ram
4-SSD 120GB

Is there any possibility of seeing log firefox log to discovery what contribute to this situation?

```

user@user:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty
user@user:~$ uname -a
Linux user 4.10.0-21-generic #23-Ubuntu SMP Fri Apr 28 16:14:22 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```


Thanks

---

### Post by vasa1 on 2017-06-02
Have you tried "about:crashes"?

---

### Post by sed_faster on 2017-06-02
How can I execute this command on terminal?
thanks

---

### Post by howefield on 2017-06-02
> **Edgar_Oliveira said:**
> How can I execute this command on terminal?

Try it in the web browser URL bar.

---

### Post by sed_faster on 2017-06-02
The result was
```

No crash reports have been submitted.

```
maybe because I need reset all system, through physical button on box pc or option shutdown from menu lxde

---

### Post by Impavidus on 2017-06-02
Maybe this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1674838](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1674838)
It should be quite obvious in your /var/log/kern.log.

You should get a fix with the regular updates in a few days. If you can't wait (I couldn't), you can enable the proposed repository and install kernel 4.10.0-22. Best to disable the proposed repository afterwards.

---

### Post by Richard_Hainsworth on 2017-07-30
I have just experienced the same problem with
uname -a
Linux merlin 4.10.0-28-generic #32-Ubuntu SMP Fri Jun 30 05:32:18 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu completely froze. Mouse not working, keyboard not working. Also on restarting significant delays in loading mouse drivers. Firefox then would not start without crashing.

Only workaround was to download Chrome.

---

### Post by sed_faster on 2018-07-19
Meanwhile my ubuntu, maybe because of the updates, no longer give problems! I prefer Firefox because the consumption the ram is more less.

---

