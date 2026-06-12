---
title: "Default backup tool"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by jkennaly on 2013-02-06
I have been using the default backup tool with Quantal for a couple of months. I am pretty happy with it so far, but I have one issue I am not sure how to resolve.

In my home directory, I have a subdirectory called .gnupg used for encryption. This directory has a mode of 700.

I have this directory excluded from being backed up. However, every time the backup tool runs, when it is done I have to acknowledge an error that this directory was not backed up (it also refers to the directory as a file).

Is this a bug in the backup utility? Is there some way I can stop this error message other than chmod 744 on this directory?

---

### Post by Kopkins on 2013-02-07
I have used the default backup in 12.04 for some time now. I have never run into that problem and have the same permissions for .gnupg. How have you excluded this folder in your backups? I have a few folders that I do not backup and I never get error messages. 

Can you post the output of ```
ls -la | grep gnupg
```
Remember to run this from your home directory.
Assuming you're using Deja-Dup for backups please post output of ```
deja-dup --version
duplicity --version
```

Kopkins

---

### Post by jkennaly on 2013-02-07
Thank you for your help.

Yes, I have excluded the folder from my backup list, as shown in the attached screen shot.

Here is the output from the commands you asked me to run:

```
~$ ls -ld .gnupg | grep gnupg
drwx------ 2 root root 4096 Apr 18  2012 .gnupg
~$ deja-dup --version
deja-dup 24.0
~$ duplicity --version
duplicity 0.6.19
```

---

### Post by Kopkins on 2013-02-07
I set up my backup to exclude .gnupg and I did not get any error message on a full backup. My duplicity is 0.6.18 and my deja-dup is 22.0. So, they are a different versions, but I don't see why yours would have that problem and mine wouldn't. I would wait see if anyone else can help you out. I checked launchpad and didn't see any bugs for deja-dup similar to your issue. 

Best of luck,
Kopkins

---

### Post by jkennaly on 2013-02-07
Thanks for your help.

I guess I'll try filing a report with Launchpad.

---

