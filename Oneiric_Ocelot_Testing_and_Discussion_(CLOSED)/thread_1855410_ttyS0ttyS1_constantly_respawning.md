---
title: "ttyS0/ttyS1 constantly respawning"
date: 2011-10-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Space_Balls on 2011-10-06
On my oneiric test install my syslog is constantly flooded with the following messages:
```
Oct  6 11:33:24 $hostname kernel: [ 5125.606727] init: ttyS1 main process (18891) terminated with status 1
Oct  6 11:33:24 $hostname kernel: [ 5125.606759] init: ttyS1 main process ended, respawning
Oct  6 11:33:24 $hostname kernel: [ 5125.610204] init: ttyS0 main process (18892) terminated with status 1
Oct  6 11:33:24 $hostname kernel: [ 5125.610235] init: ttyS0 main process ended, respawning
Oct  6 11:33:34 $hostname kernel: [ 5135.617123] init: ttyS1 main process (18894) terminated with status 1
Oct  6 11:33:34 $hostname kernel: [ 5135.617160] init: ttyS1 main process ended, respawning
Oct  6 11:33:34 $hostname kernel: [ 5135.620529] init: ttyS0 main process (18895) terminated with status 1
Oct  6 11:33:34 $hostname kernel: [ 5135.620557] init: ttyS0 main process ended, respawning

```

I doubt that it is related, but I'm also having trouble with my mounted nfs4 shares, my server(debian lenny) giving me the message:
```

nfsd: too many open  connections, consider increasing the number of threads.

```
no trouble with the ~45 ubuntu natty machines connected to it.

---

### Post by dino99 on 2011-10-06
try:

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a
(can take a while)

---

### Post by Space_Balls on 2011-10-06
The same install on a different system doesn't exhibit either one of these two errors. Going to reinstall the first machine to see if it is gone now or if I can track it down. I have a hunch it might be related to Intel AMT.

---

### Post by Space_Balls on 2011-10-06
New install also has the same ttyS0/S1 problems, so I assume it is having trouble with the Intel AMT Serial-over-Lan consoles. I will investigate the issue and see if I can figure out a workaround/fix.

Has anyone else tested Oneiric on an Intel AMT System (in this case, AMT 7.0 on a Q67 board + i5 2400).

---

