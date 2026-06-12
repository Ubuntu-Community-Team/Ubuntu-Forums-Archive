---
title: "New ubuntu installation running very slowly"
date: 2013-10-10
forum: New to Ubuntu
---

### Post by c_jackson on 2013-10-10
I have 2 identical HP G62 laptops for my kids. 

I installed Ubuntu 13.04 on one and it is fine. The other laptop started running extremely slowly under windows 7, so I re installed windows, which took several hours, and it ran even more slowly, so i installed the service packs, and the whole thing crashed.

So I installed Ubuntu 13.04 on it, but it is still running very slowly. It takes 5 minutes to boot, another 5 minutes to sign in, etc. This is substantially better than when it was running windows, but it is not even close to the other twin G62.

What should I be looking at? Could a virus have infected the bios, what other hardware problems could cause this?

Thanks!
Chris

---

### Post by heir4c on 2013-10-10
Boot up and choose in the Grubmenu the option: Memorytest  With that you control the RAM. 
You can test also your disk via "Disk-utility"

With the command glxgears you can do a test for the graphics

---

### Post by c_jackson on 2013-10-10
I installed over Windows, not a dual boot, so is there a grub menu?

---

### Post by Bucky Ball on 2013-10-10
Yes. Try hitting Esc after boot (might be shift, haven't used that method in awhile). You could also edit /etc/default/grub to get it to show but try the easier route first.

```
sudo nano /etc/default/grub
```

... and look for the line that says:

GRUB_TIMEOUT=0

... and change it to

GRUB_TIMEOUT=10

Press CTL+x then 'y' then reboot.

You should get to the grub menu where you will find the memtest.

---

### Post by heir4c on 2013-10-10
I don't know, I have no experience with Wubi. You can also use a live-cd/usb

---

### Post by Bucky Ball on 2013-10-10
> **heir4c said:**
> I don't know, I have no experience with Wubi. 

No one said anything about Wubi. OP installed OVER Windows, not inside it.

---

### Post by heir4c on 2013-10-10
Ok, I misunderstood sorry

---

### Post by MrMichaelHill on 2013-10-10
Do you have an ubuntu live CD?

boot from that and as stated run mem test. I smell a dying drive though.

Load into a Live Ubuntu from the disk and run disk utility, that will give you any SMART errors. If it is as bad as it sounds then there will be a little red dot next to SMART status

---

### Post by c_jackson on 2013-10-10
Got the grub running using the shift key. I had to hold it for a few minutes. The memory test has been running for ~20 minutes or so, no errors do far

---

### Post by c_jackson on 2013-10-10
Pass complete no errors found in the ram memory test, onto the hard drive test.

---

### Post by c_jackson on 2013-10-10
Using the Disks the overall assessment is "Disk is OK, 122 bad sectors"

---

### Post by c_jackson on 2013-10-10
I ran the disk utility and the result was :

"Disk is OK, 122 bad sectors"

Is this the problem?

---

### Post by QIII on 2013-10-10
Hello!

Hard to say if it is THE problem, but it is a problem significant enough that you might as well stop where you are and replace the disk.

It will only get worse.

Best wishes!

---

### Post by c_jackson on 2013-10-10
Just finished the short test and extended smart tests, and both failed.

So thanks for all the help!

---

### Post by MrMichaelHill on 2013-10-10
EDIT for daftness


I thought it sounded like a disk issue! boom!

Get a SSD ;)

---

