---
title: "how to change UUID / PARTUUID  of a given partition (ext4)?"
date: 2022-10-13
forum: New to Ubuntu
---

### Post by patrick2957672 on 2022-10-13
Hello

blkid gives (mod.) something like:

/dev/sda3:  UUID="xxxxxxxx-xxxx-xxxx-xxxx-xxxxx..." TYPE="ext4" PARTUUID="xxx.-xxxx-xxxx-xxxx-xxxxx..."


How to change my UUID / PARTUUID of /dev/sda3 to a given specific UUID/PARTUUID?

Thank you

Kind regards

---

### Post by ne29914 on 2022-10-13
1: unmount partition
2: run e2fsck
3: run tune2fs
4: mount partition

---

### Post by cwmoser2 on 2022-10-14
Here's some useful commands:


                    
  ```

[B] blkid  -o  list            &#8592; display UUID&#8217;s of all hard drives
 uuidgen            &#8592; Generate a unique UUID
 sudo  tune2fs   /dev/sda1  -U  bb380f29-34f1-4852-96d6-62cc5fad01f9    &#8592; Assign UUID to HD
 update-grub            &#8592; update boot grub[URL="http://localhost:631/"]
[/URL][/B]
```

---

### Post by &amp;KyT$0P# on 2022-10-14
Regarding PARTUUID, does the drive use gpt (GUID partition table)?

Also, why do you want to change the UUID and PARTUUID to specific values?

---

### Post by MAFoElffen on 2022-10-14
**+1 with halogen2** ...before you try changing things and possibly losing access to anything on that is currently on that partition... 

Meaning why and what is the goal.

---

### Post by cwmoser2 on 2022-10-15
> **halogen2 said:**
> 
Also, why do you want to change the UUID and PARTUUID to specific values?

As my backup strategy I clone partitions using the dd command.
dd makes the UUID of the target partition the same as the source partition.
I use blkid to record the uuid's before cloning and then tune2fs to set the uuid back to what it was.

Not sure why the original poster is needing to change his uuid.

---

