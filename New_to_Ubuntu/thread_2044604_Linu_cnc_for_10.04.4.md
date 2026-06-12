---
title: "Linu cnc for 10.04.4"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by johann1472 on 2012-08-19
I finally managed to install ubuntu 10.04.4 LTS besides my windows7, 64 bit
and now I am trying to find linux cnc (EMC2) for it but so far haven't found one.
Linux cnc 10.04 does not work with 64 bit. 
Anybody have any idea where to find it. 
Any help is apreciated.

---

### Post by cariboo on 2012-08-19
What have you tried so far? Did you download and burn the live iso to a CD or create a live usd drvice using unetbootin? What kernel are you using? You can check the kernel version by opening a terminal and typing:

```
uname -a
```

the output should look similar to this:

```
Linux alexis 3.5.0-10-generic #10-Ubuntu SMP Mon Aug 13 15:23:58 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

I running Quantal (12.10) so I have a much newer kernel from the 2.6 version your system should use.

---

### Post by johann1472 on 2012-08-20
HI Cariboo907,
 
This is what i got from terminal : 2.6.32-38-generic-Ubuntu SMP Wed Jan 4
 
11:12:07 UTC 2012 x86_64 GNU/Linux.
 
Everything works fine till I start to install the cnc part in terminal. Terminal 
 
starts the process but shuts down within seconds.

---

