---
title: "Processor and memory upgrade"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by its_jon on 2008-09-05
hi.....

How simple is it to upgrade processor and memory (after) installing the latest Ubuntu.

I have my install working great with the exception of midi....
I am finding that I want to enable many of the advanced desktop features so .... its time to upgrade.

Im running

biotec gforce6100-m9 mobo
amd 64 3200+
768 ram

Thinking of upgrading to

biotec gforce6100-m9 mobo
AMD Athlon64 4450e Socket AM2 Dual-Core Processor 
2X 1Gb 400Mhz PC3200 184Pin DDR Memory 

New flatscreen monitor


I would appreciate knowing if this is a simple case of plugging the new stuff in and rebooting ?? .... bieng a linux newb im cautious about hardware.

Better to ask now eh?! :)

Also welcome any thoughts on a better way to upgrade !.... the items I have chosen fit my budget but if I can buy better for the same cost I would be pleased to know about it...

Thanks
John 
Scotland

---

### Post by Cypher on 2008-09-05
Run the command
```

uname -a

```
and look to see if you see the words SMP after the version of Kernel.

You can safely upgrade the memory and you the new amount should be properly detected and used without any intevention from you. You can confirm the total memory changes from 768MB to 2GB with
```

free -m

```
On your current machine it should report a number around 720 for the Mem: Total field. This number should increase to approx. 2000 when you upgrade your memory.

If the Kernel query command above reported SMP then when you upgrade your CPU to the new Dual-core processor it will be taken full advantage of. You can confirm that both cores were seen by doing
```

cat /proc/cpuinfo

```
You should see 2 Processors listed (the 2 cores look like 2 CPUs to Linux)..

---

### Post by its_jon on 2008-09-05
Thanks !.....

I got this ....

2.6.24-19-generic #1 SMP

No kernal..... is 2.6.24-19- the kernel ?

---

### Post by gmxgeek on 2008-09-05
> **its_jon said:**
> Thanks !.....

I got this ....

2.6.24-19-generic #1 SMP

No kernal..... is 2.6.24-19- the kernel ?

Yes, you are using the generic 2.6.24.19 kernel, as opposed to server edition, etc.

---

### Post by its_jon on 2008-09-05
Thanks everyone... 

I know have the confidence ..

greetz from Scotland
JOn

---

### Post by elmoosecapitan on 2008-09-05
Upgrading your RAM should not cause any problems. The only difference you will see will be the insane improvement of performance and a massive decrease in battery life. Good luck!

---

