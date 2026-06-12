---
title: "Verify if disk drive is flash"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by sandeeppawar on 2012-04-29
Hello,

I am doing some project in which I need to check if my disk drive is flash or not (disk path will be input).

I tried with some commands like

lshw
hdparm
lspci

But I'm not able to verify flash disk. I'm not understanding which specification (in th output of these commands) should I look into to check for flash memory.

Can anyone please help me.

Thanks and Regards,
Sandeep P.

---

### Post by matt_symes on 2012-04-29
Hi

You can check if the drive is removable.

```
cat /sys/block/sda/removable
```Change sda is required.

You can also test if it is a rotational drive

```
cat /sys/block/sda/queue/rotational
```Kind regards

---

### Post by sandeeppawar on 2012-05-01
Thanks a lot for response!!

But I am little confused is this information has any relation with disk being "flash".
I'm mean there can be removable devices which are not flash.

Regards,
Sandeep.

---

### Post by matt_symes on 2012-05-01
Hi

* If the drive is not removable and not rotational then (presumably as i cannot test this) it an internal SSD drive.

* If the drive if removable and not rotational then it is flash.

* External rotational hard drives show up the same as internal ones but you can check the bus it is on i suspect.

Take a look at this

```
matthew@matthew-Aspire-7540 ~ % ls -d /sys/block/sd?
/sys/block/sda  /sys/block/sdb  /sys/block/sdc
matthew@matthew-Aspire-7540 ~ %
```There are three drive on my system at the moment.

* sda is the internal rotational drive
```

matthew@matthew-Aspire-7540 ~ % cat /sys/block/sda/{removable,queue/rotational}
0
1
matthew@matthew-Aspire-7540 ~ %
```* sdb is an external rotational drive
```

matthew@matthew-Aspire-7540 ~ % cat /sys/block/sdb/{removable,queue/rotational}
0
1
matthew@matthew-Aspire-7540 ~ %
```* sdc is an external flash drive.

```
matthew@matthew-Aspire-7540 ~ % cat /sys/block/sdc/{removable,queue/rotational}
1
0
matthew@matthew-Aspire-7540 ~ %
```There is a load of information you can pull out of sysfs for information about the drives including which bus they are on. That can be used vto tell you if the drive is an internal or external drive.

This is also only one method of doing this.

Have you look at udevadm ? Change X below as required.

```
udevadm info --query=property --name /dev/sdX
```Or even udisks.

```
udisks --dump
```This will spit out a load of information about the connected drives and

```
udisks --show-info /dev/sdX
```for specific drives.

You can the grep, sed, awk, or parameter substitute the output to your hearts content :)

_Check out the man pages for both._

Kind regards

---

