---
title: "Can't Mount Harddrive"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by Joseph5000 on 2008-09-21
New hard drive, At first I could mount it, but now I can't. Error as follows.
$MFTMirr does not match $MFT (record)

---

### Post by wolfen69 on 2008-09-21
i'm afraid this will require windows to fix.  MFT is Master File Table which is a windows thing. with an xp cd you can run "chkdsk /f" (no quotes) in recovery console.

---

### Post by Joseph5000 on 2008-09-21
You find me lost. How can it run at first, then after 10GB download it crashes, and then I can't restart it. Yes, I checked through XP, and that OP can see it, But why can't Ubuntu Mount it?
Are you saying that the evil XP has taken over in the middle of the process ad I can use this (external) Hard drive only with windows?

---

### Post by sayakb on 2008-09-21
At a terminal:
```
sudo apt-get install ntfsprogs
```
Then run **ntfsfix** on the drive.

---

### Post by Joseph5000 on 2008-09-21
Here comes the bloody beginner. I run the command you wrote, but how do I run a ntsffix?

---

### Post by sayakb on 2008-09-21
Just the same way you run the command! :)
Details of package ntfsprogs: [http://packages.ubuntu.com/hardy/ntfsprogs](http://packages.ubuntu.com/hardy/ntfsprogs)

EDIT: w00t! 2800 up! :D

---

