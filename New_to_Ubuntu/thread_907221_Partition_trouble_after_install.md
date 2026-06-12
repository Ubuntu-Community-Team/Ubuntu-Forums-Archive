---
title: "Partition trouble after install"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by hesjnet on 2008-09-01
Hi Guys. Great forum.


I had Ubuntu 8.04 installed and running and decided that I wanted to try Xubuntu as an dual-boot alternative.

I re-partitioned the harddrive into 2 partitions:

one for ubuntu 8.04
one for Xubnuntu 8.04

After I installed Xubuntu and tried to start, it all went wrong. I got this error message after the bios had loaded:[B]

no bootable partition in table[/B]

I guess it is something I did, but what do I do to fix it?

Any ideas?:confused:

---

### Post by meindian523 on 2008-09-01
Looks like there is no partition which has the boot flag.

---

### Post by meindian523 on 2008-09-01
Do you also have Windows on your machine?

---

### Post by pmlxuser on 2008-09-01
you mean you have 2 root partitions (1 for Xubuntu, 1 for ubuntu)
strange that you did that, you dont need to install two different installation (duo boot) to run Xubuntu and Ubuntu. they basically are just Desktop enviroments.

So here is a solution if you don't have alot of important data

1. delete all the partition
2. install either ubuntu/ Xubuntu
3. install the other desktop depending on the option you choose in 2 using the repositories. 
```

$sudo apt-get install x-desktop 

```
where x = ubuntu | xubuntu

in simple terms
do  the following when you install either xubuntu or ubuntu
-> run terminal
->type the following in the termina

```

$sudo apt-get install ubuntu-desktop

```
if you install xubuntu

OR type
```

$sudo apt-get install xubuntu-desktop

```
if you install ubuntu


at log in you can choose a session either ubuntu or xubuntu ;)

---

### Post by hesjnet on 2008-09-01
Thanks guys. Its only the ubuntu 8.04 partition that is flagged as boot... And yes. I have my whole life on that partition.

I just managed to change permissions on my home folder, so I'll probably just copy them out and do a clean install instead of messing around to much with sensitive settings ;)

And pmlxuser: THANKS alot. I'll do this when my data is extracted.

Thanks again.

---

