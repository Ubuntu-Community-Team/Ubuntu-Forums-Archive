---
title: "8 GB Flash partitioned too small.  Solution?"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-09
I have 11.10 installed and running great on a 8 GB USB flash drive.

So far I love it, even with unresolved issues:  LAN to another PC, LAN printer, etc.

(There is the thumb drive for a temporary fix)

Unfortunately, I made my primary partition  about 2.75 GB and Ubuntu gives me the "almost out of memory" warning.

I have 4 GB left to expand into.

I cannot boot the USB and run gparted because the flash is active.

Gparted needs to run as root to see the USB (sdb5 and sdb6)

I tried using my live CD in the trial mode, but it will not allow me to use the terminal as root:  su -l 

Ubuntu asks for a password and I tried 'Ubuntu'.

I have no idea about how to proceed.

Can I get there from here?

---

### Post by dmouck on 2012-04-09
To be root from the live CD, try "sudo su" or "sudo bash"

---

### Post by Cheesemill on 2012-04-09
> **dmouck said:**
> To be root from the live CD, try "sudo su" or "sudo bash"
The preferred method is:
```
sudo -i
```

To run gparted from the Live CD just open a terminal and type:
```
gksudo gparted
```
You shouldn't be asked for a password as there isn't one on the Live CD.

---

### Post by dmouck on 2012-04-09
> **Cheesemill said:**
> The preferred method is:
```
sudo -i
```


Thanks! I hadn't seen that before, so I checked "man sudo" to read up on it.

Cheers!

---

### Post by Boyntonstu on 2012-04-09
> **Cheesemill said:**
> The preferred method is:
```
sudo -i
```To run gparted from the Live CD just open a terminal and type:
```
gksudo gparted
```You shouldn't be asked for a password as there isn't one on the Live CD.


[SIZE=4]PERFECT!  Thanks!

It now has 6.47MB  and 1007 swap.

How could I learn these tricks without you?

Impossible!

The moral of the story is if you work at it and ask questions here, you will reach your goals.

(Even if you are a 73 year old graybeard)

Solved!!!!


[/SIZE]

---

