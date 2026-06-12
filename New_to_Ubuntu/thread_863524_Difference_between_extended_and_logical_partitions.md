---
title: "Difference between extended and logical partitions"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by sandeepy on 2008-07-18
I haven't understood yet. Please enlighten me.

thanks.

---

### Post by JagDragon on 2008-07-19
On a disk, there can only be four primary partitions. So, what happens if we need more? One of those primary partitions is turned into an **extended** partition, in which **logical** partitions can reside. So the extended partition is like a "container" for logical partitions.

The drawback to logical partitions is that they cannot be booted from.

Did that clear it up?

---

### Post by dexter.deepak on 2008-07-19
extended and logical partitions are same !!
may be you are looking for difference between primary and extended partitions..

---

### Post by coffeecat on 2008-07-19
Couldn't explain better than JagDragon, except to add:

Primary or Extended partitions are numbered sda1, sda2, sda3 or sda4. Logical partitions are numbered sda5 upwards. All for obvious reasons when you consider, but it's useful - you can tell a logical partitions at a glance.

Note - substitute sdb for second drive, and sdc, sdd and so on. And hda if the system is using the older ata drivers on an ide drive.

**Edit:** and I should clarify JagDragon's last comment. Windows cannot boot from a logical partition, but Linux can. :cool: I should know. I'm posting from Mandriva atm which is in sda12 (a logical partition) in this multiboot, and I didn't have any problems booting-up. :wink:

---

### Post by coffeecat on 2008-07-19
> **dexter.deepak said:**
> extended and logical partitions are same !!

This is **not** correct. Look at the post previous to yours.

---

### Post by sandysandy on 2008-07-19
> **JagDragon said:**
> 

The drawback to logical partitions is that they cannot be booted from.



i think you can boot from logical partitions. depends on ur bootmanager.

regards

---

### Post by dexter.deepak on 2008-07-19
oh !! i am really sorry for that post!! just feeling a bit sleepy..
anyways, this is what JagDragon says:
```
The drawback to logical partitions is that they cannot be booted from
```
you cant even boot from the extended drive..only a primary partition can be booted,

---

### Post by JagDragon on 2008-07-19
> **coffeecat said:**
> Windows cannot boot from a logical partition, but Linux can. :cool: I should know. I'm posting from Mandriva atm which is in sda12 (a logical partition) in this multiboot, and I didn't have any problems booting-up. :wink:

Thanks for that, you learn something new everyday. I should have known that Linux can do that, what can't it do, eh? :mrgreen:

---

### Post by bigken on 2008-07-19
> **dexter.deepak said:**
> oh !! i am really sorry for that post!! just feeling a bit sleepy..
anyways, this is what JagDragon says:
```
The drawback to logical partitions is that they cannot be booted from
```you cant even boot from the extended drive..only a primary partition can be booted,


take a look here 


[http://ubuntuforums.org/showthread.php?t=246741](http://ubuntuforums.org/showthread.php?t=246741)

you can boot from a extended partition

---

### Post by coffeecat on 2008-07-19
> **dexter.deepak said:**
> just feeling a bit sleepy..
anyways, this is what JagDragon says:
```
The drawback to logical partitions is that they cannot be booted from
```you cant even boot from the extended drive..only a primary partition can be booted,

Have a look at the edit to my first post about booting from logical partitions - and then get yourself a good night's sleep. :wink:

---

### Post by linfidel on 2008-07-19
> **sandeepy said:**
> I haven't understood yet. Please enlighten me.

thanks.In case the previous posts are not clear... in a nutshell:
You can create an extended partition from unused space using the partition editor.  Once you have done this, you can create any number of logical drives inside the extended partition.

An extended partition needs to have at least one logical drive to be useful.

But, as stated earlier, the extended partition actually lives in a primary partition, so you can't create an extended partition once you have used up all the primary partitions.

It's usually best not to use primary partitions unless you need to.  I don't think it's impossible to boot Windows from an extended partition, but it's probably not straightforward - I've never tried it.

Edit:  Sorry if I repeated information - while writing my post, more were added that I didn't see before entering mine.

---

