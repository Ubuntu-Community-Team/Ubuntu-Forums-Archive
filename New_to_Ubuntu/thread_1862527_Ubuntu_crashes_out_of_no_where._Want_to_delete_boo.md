---
title: "Ubuntu crashes out of no where. Want to delete boot partition."
date: 2011-10-16
forum: New to Ubuntu
---

### Post by kiran_viswm on 2011-10-16
BUG: unable to handle kernel paging request

Due to this bug my laptop loaded with ubuntu OS crashes most of the time. I want to format the boot partition and install a new os (Hoping this will solve). But the installation also crashes showing the bug report. Please suggest any ways to handle the situation. 
NOTE: i only want to delete the boot partition as other partitions contain valuable data back-ups.

Is there any way i could connect my laptop to my desktop PC as a usb and delete the boot partition?

Hoping that some one will help me.. :(
Thanks in advance..

---

### Post by Mark Phelps on 2011-10-17
> **kiran_viswm said:**
> Is there any way i could connect my laptop to my desktop PC as a usb and delete the boot partition?


You could try booting from the Ubuntu CD, choosing Try Ubuntu, opening a disk utility -- and deleting the partition that way.

If that doesn't work, you may have to remove the hard drive from the laptop, connect it to another PC using an adapter, and then delete the partition.

---

### Post by kiran_viswm on 2011-10-17
> **Mark Phelps said:**
> You could try booting from the Ubuntu CD, choosing Try Ubuntu, opening a disk utility -- and deleting the partition that way.

If that doesn't work, you may have to remove the hard drive from the laptop, connect it to another PC using an adapter, and then delete the partition.
Thanks for the reply!!
i deleted the boot partition using a ubuntu live usb.
But when i try to install ubuntu system crashes as happened before.
Would it be a hardware complaint?
But the details of the bug says that it is some memory problem.
What to do?

---

### Post by Mark Phelps on 2011-10-17
I believe there's an option when you boot using the LiveCD to run MEMTEST.  IF that is there, use that to check your memory.

Also, if you have more than one memory stick in place, you can experiment with using only one at a time.  That way, if one one is defecting, you can run using the other one until you replace the defective one.

---

### Post by kiran_viswm on 2011-10-18
That helped !! it was the problem with the ram chip.. :)
thanx a lot.. :)

---

