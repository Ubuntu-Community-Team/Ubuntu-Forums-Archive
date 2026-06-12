---
title: "Radeon 9200 Driver"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by azizmars on 2008-11-05
Okay well i was trying to raise my brightness like i can on my windows. I installed the ATI Control Centre thing, but now its telling me that i need to get the driver. So i was wondering if anyone can tell me how to install the driver or get the driver? I searched around but the links some people posted for help might aswell be in a different languge, i didnt understand a thing. So yeah please keep it simple if you can. Oh and im on Ubuntu 8.10. Thx for the help guys. If you need more info or something PM or IM me on AIM my SN is AZIZMARS.....

---

### Post by Peter09 on 2008-11-05
is it asking for a driver to be enabled in

System->Administration->Hardware Driver

---

### Post by azizmars on 2008-11-05
> **Peter09 said:**
> is it asking for a driver to be enabled in

System->Administration->Hardware Driver

It says "No Proprietary drivers are in use on this system." What does that mean? or what am i supose to do? Thx for the help Peter....

---

### Post by Peter09 on 2008-11-05
Can you post the output of the terminal command

```
lshw -C display
```

---

### Post by azizmars on 2008-11-05
> **Peter09 said:**
> Can you post the output of the terminal command

```
lshw -C display
```

If i understood correct i put that code in terminal and this is what it wrote 
```
 azizmars@ubuntu:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RV280 [Radeon 9200]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=64 mingnt=8
azizmars@ubuntu:~$ 

```

---

### Post by Peter09 on 2008-11-05
ok, you have not got the correct driver installed.

First try, boot into recovery mode and select xfix

---

### Post by azizmars on 2008-11-05
> **Peter09 said:**
> ok, you have not got the correct driver installed.

First try, boot into recovery mode and select xfix

How do i boot in recovery mode???? Once again thx for the help Peter...

---

### Post by Peter09 on 2008-11-05
At the grub prompt hit the ESC key. This should stop the boot and give you the option to scroll down the lines to the recovery mode option - normally the second line down. Once there hit enter to start the process.

---

### Post by azizmars on 2008-11-05
Kk im going to go do it and tell u what happens brb in a little bit....

---

### Post by azizmars on 2008-11-05
Okay i did it now what should i do?

---

### Post by Peter09 on 2008-11-06
Hi azimars,
what happened did it work?

---

### Post by Deeta on 2008-11-10
I have the same problem and a very similar GPU.
xfix certainly did not work for me :-/

```

  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: RV280 [Radeon 9200 PRO]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=64 mingnt=8

```

Given Azimars question 'what he should do now' I would assume that it did not work for him as well.

---

