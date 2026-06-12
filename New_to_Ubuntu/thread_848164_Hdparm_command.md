---
title: "Hdparm command"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2008-07-03
I have read the previous threads on the hdparm command, but none quite answer my query , which is , how do I check if my i/o is set to 32 bit ?
I have looked at hdparm.conf but am reluctant to mess with it , but it seems
that all you have to do is remove the " #" and this line will be executed , is that correct , or how do I add the " -c "  to /dev/sda1  ?

---

### Post by unutbu on 2008-07-03
To check if you have IO_support set to 32-bit:
```
% sudo hdparm -c /dev/sda

/dev/sda:
 IO_support    =  0 (default 16-bit)
```

From the `man hdparm` page:
```

       -c     Query/enable (E)IDE 32-bit I/O support.  A numeric parameter can be  used
              to  enable/disable 32-bit I/O support: Currently supported values include
              0 to disable 32-bit I/O support, 1 to enable 32-bit data transfers, and 3
              to  enable 32-bit data transfers with a special sync sequence required by
              many chipsets.  The value 3 works with nearly all  32-bit  IDE  chipsets,
              but  incurs  slightly  more  overhead.  Note that "32-bit" refers to data
              transfers across a PCI or VLB bus to the interface card only; all  (E)IDE
              drives still have only a 16-bit connection over the ribbon cable from the
              interface card.
```

My experience with hdparm has been that it is fine for querying the state of a sda drive, but it has trouble configuring sda drives:
```
% sudo hdparm -c3 /dev/sda

/dev/sda:
 setting 32-bit IO_support flag to 3
** HDIO_SET_32BIT failed: Invalid argument**
 IO_support    =  0 (default 16-bit)

```
I think this has to do with the libata developers deciding not to implement all HDIO_* commands:
> 
libata intentionally does not support all the HDIO_xxx ioctls that were supported by the older IDE driver. It is now preferred to use SG_IO as a generalized ATA command submission method, rather than creating a myriad of ioctls for each specific purpose.

See [http://linux-ata.org/faq.html#old_ioctls](http://linux-ata.org/faq.html#old_ioctls)

I could be wrong; I'm just trying to understand hdparm / libata myself.

---

### Post by ex-wirecutter on 2008-07-03
Thanks for that , did you see my reference to the " # " in the hdparm.conf file , because in mine the i/o 32 bit line has one in front of it and wonder if deleting the " # " will enable 32 bit ?

---

### Post by unutbu on 2008-07-03
I think removing the # from this line
```
#io32_support = 1
```
in /etc/hdparm.conf is equivalent to running
```
sudo hdparm -c1 /dev/sda
```
from the terminal, except that editing /etc/hdparm.conf will make the change at boot time, while running the hdparm command from the terminal will only affect the machine until it is rebooted.

I think you can safely try the hdparm -c1 command from the terminal. If it works, then you can edit hdparm.conf to make the change permanent.

---

### Post by ex-wirecutter on 2008-07-03
Further to the last , I understand from a Linux mag. that you can add
-c 1/dev/hda to the RC.LOCAL file , but can't seem to see how you do this .

---

### Post by unutbu on 2008-07-03
You could put the hdparm command in /etc/rc.local too:
```

gksu gedit /etc/rc.local
```

Add

```
hdparm -c1 /dev/sda
```

above the line that says
```

exit 0
```

---

### Post by ex-wirecutter on 2008-07-03
THANKS ! That was what I needed to know , Ill give it a try .

---

### Post by ex-wirecutter on 2008-07-03
Did as you suggested but it simply reverted to 16 bit default .
Never mind it was worth a try and nothing lost.
Thanks again , signing off now .

---

