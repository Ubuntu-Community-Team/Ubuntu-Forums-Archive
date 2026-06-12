---
title: "USB drive not recognized in fdisk II"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by rwslippey on 2012-04-04
Hello,


Having the same issue here, tried several of the suggestions above to no avail. Brand new drive on a ubuntu 10.04 Server. Just trying to use the 1TB drive for backup.

Rules out the above and hardware issues. Can't mount or even see anything in fdisk -l  to include other usb thump drives?


Any suggestions?

---

### Post by cariboo on 2012-04-05
I moved this to a thread of it's own, as the op posted this question in a solved thread. Moving it to a thread of it's own should result in getting a solution to the problem quicker.

What does dmesg tell you just after you have plugged in the drive? I'd suggest you paste the output of :

```
demsg | tail  -n10
```

just after you have plugged your usb drive in, in your next post.

The output should look something like this:

```
dmesg | tail -n10
[13448.122943] sd 4:0:0:0: [sdc] Write Protect is off
[13448.122948] sd 4:0:0:0: [sdc] Mode Sense: 45 00 00 08
[13448.123440] sd 4:0:0:0: [sdc] No Caching mode page present
[13448.123445] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[13448.125689] sd 4:0:0:0: [sdc] No Caching mode page present
[13448.125693] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[13448.127454]  sdc: sdc1
[13448.129689] sd 4:0:0:0: [sdc] No Caching mode page present
[13448.129694] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[13448.129697] sd 4:0:0:0: [sdc] Attached SCSI removable disk
```

---

