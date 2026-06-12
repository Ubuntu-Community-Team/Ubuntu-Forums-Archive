---
title: "dual boot Ubuntu 7.04 ugrade to 8.04"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by blueboyMark on 2008-09-04
I have a dual boot Ubuntu 7.04 (the rest of the family are using WINXP in a separate partition on my PC). All runs ok. However
I have tried using the upgrade desktop window but get various errors. I have reset my user passwd in recovery but still will not update/upgrade. 
I Have Ubuntu 8.04 on disk - How do I install it.
Do I have to delete the partition, and start over?

---

### Post by Sef on 2008-09-04
> I have a dual boot Ubuntu 7.04 (the rest of the family are using WINXP in a separate partition on my PC). All runs ok. However
I have tried using the upgrade desktop window but get various errors. I have reset my user passwd in recovery but still will not update/upgrade. 
I Have Ubuntu 8.04 on disk - How do I install it.
Do I have to delete the partition, and start over?

You would have to have upgraded to 7.10 first, then upgrade to 8.04.

To dual boot, you would need to erase the root Linux partition and reinstall it.

However, do this first from the terminal (Applications > Accessories > Terminal)

paste or type in this command:


```
sudo fdisk -l
```
Small L That will show you your partitions.

Then paste or copy it here. Once here, we can tell you which partition to reformat.

---

### Post by blueboyMark on 2008-09-04
Thankyou for your help.

I made a mistake the pc does have 7.1 on it, not 7.04.
However when I try to upgrade I get: failed to ........

the underlying authorisation mechanism (sudo) does not allow you to run this program. Contact system administrator 

Can you help me with this please.

I have also tried at the terminal sudo fdisk -l 

nothing happens?

I have reset my passwd in recovery but still I get the message when every I try to in stall new programs.

---

### Post by Sef on 2008-09-05
Read [Psychocats fix sudo]("http://www.psychocats.net/ubuntu/fixsudo").

---

