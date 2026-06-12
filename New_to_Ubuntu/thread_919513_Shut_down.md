---
title: "Shut down"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Dadsgé on 2008-09-14
hy,

I'm using ubuntu on an asus eee laptop
but if i shut down ubuntu, the light of my laptop stays on...
so i always need to push the 'on' button for some seconds till my laptop shuts  down either...
can I solve this problem?

mvg
dadsgé

---

### Post by cmnorton on 2008-09-14
This sounds like the Asus is not taking the shutdown -h into a power down state. shutdown -h means halt, and on older hardware, halt is what the system does, not power off.

In addition, I would query any support web addresses that came with your Asus to see what their take is, given they chose the Ubuntu variant and installed it.

---

### Post by panhandle on 2008-09-14
Does ```
sudo shutdown -P now
``` work for you?

see 

```
man shutdown
```

Also, I believe the Eee PC does consume some power even in the "off" state.

I've read reports of total battery depletion after (9) days of inactivity.

If the above code does not help, perhaps there is some connection, and maybe the eee boards might be of more service.

---

