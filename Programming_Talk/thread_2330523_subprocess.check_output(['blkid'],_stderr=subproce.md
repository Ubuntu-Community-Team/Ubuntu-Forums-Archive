---
title: "subprocess.check_output(['blkid'], stderr=subprocess.PIPE)"
date: 2016-07-12
forum: Programming Talk
---

### Post by simonwatsonsjw on 2016-07-12
Hi All,
My computer is running Ubuntu 16.04 LTS. I am writing a python3 script which starts an iscsi connection to my nas using iscsiadm and then runs a psql database cluster on there from my computer. 
My issue is that after setting up the iscsi connection successfully, I use blkid to find the UUID corresponding to the new connection so I can mount it. 
When I stop the code execution just before calling the blkid in python3, then let it run, it returns the UUID correctly. 
When I let the code run without stopping, blkid does not pick up the new UUID just added via the previous iscsiadm execution.

I think that the issue is that there is some delay in blkid picking up the new UUID. 

Could you advise if:
1) there is someway of triggering a 'refresh' of blkid prior to calling it from my python3 script? 
2) there is an alternate method of obtaining the UUID of the volume just connected via iscsi?

I have attached the relevant snippet of code I'm using below. (Logging and error catching removed but testing shows they don't impact the issue).

Thanks and regards,

Simon

```

#! /usr/bin/env python3

import subprocess

p = subprocess.run(['iscsiadm', '-m', 'node', '-L', 'all'], stdout=subprocess.PIPE, stderr=subprocess.PIPE, check=True)

bytUUID = subprocess.check_output(['blkid', '-s', 'UUID', '-o', 'value', '/dev/sdb1'], stderr=subprocess.PIPE)

```

---

