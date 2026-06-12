---
title: "CPU dual core both cores syncing only after reboot"
date: 2018-02-09
forum: New to Ubuntu
---

### Post by ulitarism on 2018-02-09
I have a Toshiba Satellite C850-1DD Notebook with dual core Intel(R) Celeron(R) CPU B830 @ 1.80GHz with 64-bit Ubuntu 16.04.2 LTS installation. Approximately 90% of the cases when I boot the system and start Ubuntu it seems like only one core is taking up all the processes and the other core does virtually nothing, which results to slow performance of the notebook. This can be seen in the CPU history in System Monitor ([https://i.stack.imgur.com/hLxrD.png](https://i.stack.imgur.com/hLxrD.png)). However if I reboot the system then the both CPU cores are synced which results in an increase of the Notebook performance, which also can be seen in the CPU history in System Monitor ([https://i.stack.imgur.com/WEYCw.png](https://i.stack.imgur.com/WEYCw.png)).

I checked via htop the processes when one core is working significantly more than the other ([https://goo.gl/UMmC9t](https://goo.gl/UMmC9t)) and I found that the xorg process is taking up unusually much CPU performance ([https://goo.gl/DtW5mx](https://goo.gl/DtW5mx)), specifically the process called:

```
/usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
```

When I reboot then the performance is back to normal ([https://goo.gl/fd7Nwe](https://goo.gl/fd7Nwe), [https://goo.gl/zztWAz](https://goo.gl/zztWAz)).

My question is, is there a workaround so that both cores are synced the first time I boot the system, so that no core has high CPU usage in idle state? Many thanks in advance!

---

