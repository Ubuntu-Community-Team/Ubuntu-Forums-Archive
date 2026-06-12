---
title: "FSCK issue"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by thyazide on 2008-06-24
Ok color me stupid but I have been attempting to boot into my install of ubuntu on a separate drive. When doing so the system tells me it requires me to run an FSCK check due to inconsistencies on my drive. I allow it to run the scan and the system gets to about 65% then errors and says "bad or duplicate block in use" then the system comes to a halt. How should I proceed?

---

### Post by iaculallad on 2008-06-24
Assuming that /dev/sdb1 is the partition with error that you want to fsck.

```
sudo fsck /dev/sdb1
```

---

### Post by thyazide on 2008-06-25
That's assuming I can get back to the command line to enter the new command. Is there a way to terminate the running fsck process?

---

### Post by iaculallad on 2008-06-25
> **thyazide said:**
> That's assuming I can get back to the command line to enter the new command. Is there a way to terminate the running fsck process?

If what you mean is stopping the fsck command on checking your drives. You can change the settings on your /etc/fstab file:

Change the last number on the partition's entry line to "0" to permanently disable fsck from running on that partition. But try to keep the "1" on your filesystem/root partition.

---

### Post by bill0102 on 2008-07-04
What's Up all,  want to beat any game you play? check out this  [Top Cheat Codes Site]('http://vncheatcodes.com')
You can play and cheat any game you want from [PSP Cheat Codes]('http://vncheatcodes.com') to [Xbox Cheat Codes]('http://vncheatcodes.com') and many other [Game Cheat Codes]('http://vncheatcodes.com')

---

