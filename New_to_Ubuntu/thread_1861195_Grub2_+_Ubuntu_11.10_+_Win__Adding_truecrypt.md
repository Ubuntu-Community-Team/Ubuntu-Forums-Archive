---
title: "Grub2 + Ubuntu 11.10 + Win  Adding truecrypt"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by Yoast on 2011-10-15
I have two computers. Bith have Grub2 Ubuntu 11.10 and Win (one vista, one 7 home premium). How hard is it to add truecrypt afterwards? Is it as easy as encrypting the two partitions and that's it?

---

### Post by Lisiano on 2011-10-15
Please note that Grub does not support partition encryption so you can't encrypt the Ubuntu root with Truecrypt. However you can still do it to Windows.
The ideal way to do this would be to first install Windows, encrypt it with Truecrypt AS A PARTITION, then install Ubuntu.
The problem with encrypting later is that Truecrypt will attempt to overwrite the MBR (Grub) and as such, break booting for BOTH Windows and Ubuntu.

---

### Post by ajgreeny on 2011-10-15
I think you will need a separate /boot partition to be able to do what you want, and not encrypt that partition.

But why not make as separate /home partition and just encrypt that, not the /root partition.  Your /home is where all your personal files are after all, not in the /root partition.

---

### Post by Yoast on 2011-10-15
Thanks. I was fearing something like that. A bit of a pity.

---

### Post by Yoast on 2011-10-15
Thanks. I may consider that. 
I must admit that I was hoping for a one-decrypt-password-at-boot option for simplicity's sake. But this sounds liek a liveable alternative.

> **ajgreeny said:**
> I think you will need a separate /boot partition to be able to do what you want, and not encrypt that partition.

But why not make as separate /home partition and just encrypt that, not the /root partition.  Your /home is where all your personal files are after all, not in the /root partition.

---

