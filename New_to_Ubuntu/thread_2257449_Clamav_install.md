---
title: "Clamav install"
date: 2014-12-19
forum: New to Ubuntu
---

### Post by Rrory on 2014-12-19
My computer is freezing so I tried to install ClamAv from the dependencies but when I type in the terminal
*apt-get install clamav*

I get this message:
claudia@claudia-HP-15-Notebook-PC:~$ apt-get install clamav
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I have no clue what this means.....

---

### Post by flaymond on 2014-12-19
> Permission Denied


- That mean you need to put sudo(super user priviledges/admin priviledges) to install from the APT. 

Run like this -


```
sudo apt-get install clamav
```


Tthis command will make you as admin to install the package.

---

### Post by Rrory on 2014-12-19
thank you! worked like charm

---

### Post by flaymond on 2014-12-19
You should learn about some basics using Bash, because it will help you a lot on any Linux distros. You can learn about Linux and how to use the Terminal/Bash in here - [http://linux-training.be/files/books/LinuxFun.pdf](http://linux-training.be/files/books/LinuxFun.pdf) 


You have to do some read, but you can do almost everything just from the Terminal on Linux.

Anyway, good job for the installed clamav!

---

### Post by Rrory on 2014-12-20
yes I ran the clamav all from the terminal and I'll continue that way, I really find it easier....So thanks for the help and the links, I'll really enjoy my reading:)

---

### Post by Bucky Ball on 2014-12-20
Well done installing clamav, but not sure what that has to do with your freezing computer problem. :-k

You might be better off trying to fix that on a new thread.

---

### Post by Rrory on 2014-12-20
Okay I shall...I guess I was thinking back in the past of viruses and my old windows system freezing. ...

---

### Post by deadflowr on 2014-12-20
Is the freezing new?
Did it start after you did this
[http://ubuntuforums.org/showthread.php?t=2256490](http://ubuntuforums.org/showthread.php?t=2256490)

Or has it been longstanding.

---

### Post by Rrory on 2014-12-20
the freezing is brand new and did start after I did the above...

---

### Post by stalkingwolf on 2014-12-20
have you tried using the recovery mode and fix broken packages?

---

### Post by Rrory on 2014-12-20
if I boot into recovery mode, then my /boot file will be too small...arg it's a circular problem. I think first I need to repartition my uefi and boot files....This uefi business is really huge now  for me..

---

