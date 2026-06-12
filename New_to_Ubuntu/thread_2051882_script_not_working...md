---
title: "script not working.."
date: 2012-09-02
forum: New to Ubuntu
---

### Post by ganga1234 on 2012-09-02
this is the script to disable ehci_hcd and restarting nm-applet..need help to get it work.

#!/bin/bash
cd /sys/bus/pci/drivers/ehci_hcd/
echo "user passwd" | sudo sh -c 'find ./ -name "0000:00:*" -print | sed "s/\.\///" > unbind'
echo "user passwd" | sudo restart network-manager
nm-applet

---

### Post by ganga1234 on 2012-09-02
waiting ....

---

### Post by buckeyered80 on 2012-09-02
I am seeing some issues in your sed statement.
Before you run the script, type ```
set -vx
```
This will put the script in debug mode and then send us the output. We should be able to find where it is failing.

---

### Post by Bodsda on 2012-09-02
> **ganga1234 said:**
> this is the script to disable ehci_hcd and restarting nm-applet..need help to get it work.

#!/bin/bash
cd /sys/bus/pci/drivers/ehci_hcd/
echo "user passwd" | sudo sh -c 'find ./ -name "0000:00:*" -print | sed "s/\.\///" > unbind'
echo "user passwd" | sudo restart network-manager
nm-applet

Your missing a single quote after -print
You may also want to revisit your posting attitude. We are all volunteers here.

Bodsda

---

### Post by ganga1234 on 2012-09-02
it s working in terminal but not as a start up application...i wanna make it as start up application when i boot my machine;);)by the way sorry4 the delay..workin in office:p:p

---

### Post by Bodsda on 2012-09-02
> **ganga1234 said:**
> it s working in terminal but not as a start up application...i wanna make it as start up application when i boot my machine;);)by the way sorry4 the delay..workin in office:p:p

On startup or on login?

---

### Post by ganga1234 on 2012-09-02
on login though

---

### Post by Bodsda on 2012-09-02
> **ganga1234 said:**
> on login though

Try this
[http://bit.ly/NFJFh8](http://bit.ly/NFJFh8)

---

