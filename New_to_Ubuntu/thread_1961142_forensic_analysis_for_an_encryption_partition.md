---
title: "forensic analysis for an encryption partition"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by herbert tamayo on 2012-04-18
Hi, my data is encrypted using cryptsetup, I was tryingmy s to uncrypt permanently this partition (dev/sda2), the only commands I typed was:

```

1. cryptsetup status enc-disk
2. load gparted and tries to format the partition as ext3, obviously I got an error

```

after that i work with my files without a problem, the partition was mounted and everything was fine, when the day ended I put my laptop in hibernate mode and when I wake up my system the data was ok.

last night i shutdown my system, this morning, trying to mount the partition
```

sudo cryptsetup luksOpen /dev/sda2 enc-disk

```

when i type my passphrase it does not open!, after 3 tries i got the message that 

```

No key available with this passphase

```


so, obviously I did not change my passphase- even I don't know how to change it- but I don't get in, so my questions are:

1. what commands should I use to analyze what is wrong?
2. is there a way to add another key?
3. what is going on with my partition, how can i do an analyze?

regards

---

### Post by herbert tamayo on 2012-04-18
in fact, the main problem I think it's for some reason, the key seems to be different, but I didn't not change it, because i don't know why.

using luksDump the partition is read it as encrypted, and the slot 0 is enabled

but the dm-crypt module is not loaded it, my new question is:

what else things should i check?

---

