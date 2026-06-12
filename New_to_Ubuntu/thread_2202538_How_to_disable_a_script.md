---
title: "How to disable a script"
date: 2014-01-29
forum: New to Ubuntu
---

### Post by yan_solo on 2014-01-29
Hi, I tryed to fix a problem I have with that solution.
[http://ubuntuforums.org/showthread.php?t=1978290](http://ubuntuforums.org/showthread.php?t=1978290)

But that does not work. And it prevent suspend to work. 
My question is how to remove permission for that script to run. 

I did that but did not work?```

sudo chmod 750 /etc/pm/sleep.d/20_custom-ehci_hcd
```

To reverse```

sudo chmod 755 /etc/pm/sleep.d/20_custom-ehci_hcd
```

---

### Post by Dave_L on 2014-01-29
Try removing execute permission:

```
sudo chmod 644 /etc/pm/sleep.d/20_custom-ehci_hcd
```

---

### Post by ajgreeny on 2014-01-29
```
sudo chmod -x /etc/pm/sleep.d/20_custom-ehci_hcd
``` would do the same thing as the above **chmod 644** command

---

