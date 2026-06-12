---
title: "kern.log file is 80GB"
date: 2017-08-25
forum: New to Ubuntu
---

### Post by cesard92 on 2017-08-25
Hey guys: 
I installed Ubuntu 16.04 on my laptop alongside with Windows 10 about 4 weeks ago and I've been having problems with the storage since the first week or two (my partition is about 110GB and never thought it wouldn't be enough, hehehe). I've been reading online but no luck so far. In the first couple of days, I had problems with the WiFi and I tried a few steps that I found online and they solved it, but maybe it made this other problem even worse. My kern.log file right now is 80GB and it doesn't seem to stop growing. Any suggestions??? Thanks in advance for your time!!! Any additional info, please let me know.

---

### Post by deadflowr on 2017-08-25
Post the output for
```
tail /var/log/kern.log
```
that should give us an idea of what's causing the gluttony.

*tail outputs the end of a file, and since the file is growing it should tell us what the last/latest entries are.

Also, it'd help to know what you fiddled with for the wifi situation.

---

### Post by cesard92 on 2017-08-25
neno@Ubuntu:/var/log$ tail kern.log
Aug 25 08:09:08 Ubuntu kernel: [ 2407.300622] pcieport 0000:00:1c.5:    [ 0] Receiver Error        
Aug 25 08:09:08 Ubuntu kernel: [ 2407.300628] pcieport 0000:00:1c.5: AER: Corrected error received: id=00e5
Aug 25 08:09:08 Ubuntu kernel: [ 2407.300633] pcieport 0000:00:1c.5: can't find device of ID00e5
Aug 25 08:09:08 Ubuntu kernel: [ 2407.300634] pcieport 0000:00:1c.5: AER: Corrected error received: id=00e5
Aug 25 08:09:08 Ubuntu kernel: [ 2407.300638] pcieport 0000:00:1c.5: can't find device of ID00e5
Aug 25 08:09:08 Ubuntu kernel: [ 2407.300651] pcieport 0000:00:1c.5: AER: Corrected error received: id=00e5
Aug 25 08:09:08 Ubuntu kernel: [ 2407.300656] pcieport 0000:00:1c.5: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e5(Receiver ID)
Aug 25 08:09:08 Ubuntu kernel: [ 2407.300661] pcieport 0000:00:1c.5:   device [8086:9d15] error status/mask=00000001/00002000
Aug 25 08:09:08 Ubuntu kernel: [ 2407.300663] pcieport 0000:00:1c.5:    [ 0] Receiver Error        
Aug 25 08:09:08 Ubuntu kernel: [ 2407.300669] pcieport 0000:00:1c.5: AER: Corrected error received: id=00

---

### Post by cesard92 on 2017-08-25
About the wifi spe, I followed some steps online and found out the model of my wireless adapter (RTL8821AE), downloaded the drivers from git rtlwifi_new and then installed them. I haven't been able to find the exact website with the instructions I followed.

---

### Post by oldfred on 2017-08-25
What brand/model system?

Some have run away log files & need a boot parameter.
 Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

---

### Post by cesard92 on 2017-08-25
It's actually an ASUS F555U!! I'm gonna try those links and let you know.

---

### Post by cesard92 on 2017-08-29
I tried those steps and so far I think it's working better. My kern.log files are less than 1GB, so I have my fingers crossed. I will keep and eye on it for a few days, but IT REALLY LOOKS GOOD, so THANK YOU SOOO MUCH oldfred!!!

---

### Post by oldos2er on 2017-08-29
If your problem is solved,  please mark the thread Solved under Thread Tools at the top of the page. Thanks!

---

