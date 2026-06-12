---
title: "unable to boot Ubuntu with wubi"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by czgirb on 2012-06-05
Currently, the Ubuntu that I used was installing via Wubi.
Now, everytime I boot into Ubuntu it always:
* Ubuntu start screen do not showup
* It requires me to boot into **Windows** and **run chkdsk /r** => **reboot, and boot into Windows, finished the log-in and have it properly shut-down** => **reboot**.

I do this twice, but it always ends the same result.
Please help me ... cos I need to moved some files, which stored inside ubuntu.
Please ...............

---

### Post by wilee-nilee on 2012-06-05
Are you getting into Ubuntu at all, hard to tell from your description.

Is the Windows requiring the chkdsk every time to get in as well.

---

### Post by czgirb on 2012-06-06
SOORY ... may be my poor english makes you confuse.
Let me describe it one-by-one:

When I start the computer, it offer me a choice whether I want to boot **Windows XP Professional** or **Ubuntu 10.04** ... and I choose Ubuntu.
Again it offer me by which kernel I want to boot ... and I choose the latest one.
After that, Ubuntu start screen won't showup, and the following-like text is show-up:
> 
* ... please boot into **Windows** and **run chkdsk /r** => **reboot, and boot into Windows, finished the log-in and have it properly shut-down** => **reboot**.


Please help me for having my ubuntu's back.
Thank you.

---

### Post by czgirb on 2012-06-06
[SIZE=4]HELP ... HELP ... HELP ...
please ...........................[/SIZE]

---

### Post by czgirb on 2012-06-06
Based on my perception, the problem maybe caused from unpropper shut down process due to the system hang for more than 5 minutes.

---

### Post by wilee-nilee on 2012-06-06
> **czgirb said:**
> Based on my perception, the problem maybe caused from unpropper shut down process due to the system hang for more than 5 minutes.

There is only really one person on the forum who knows the wubi set up, they are on daily, and you have wubi in the header they will stop by, they are usually on during the day US time.

---

### Post by czgirb on 2012-06-06
> **wilee-nilee said:**
> There is only really one person on the forum who knows the wubi set up, they are on daily, and you have wubi in the header they will stop by, they are usually on during the day US time.

Would you mind for telling me who is the person?
**Thank you**


When it was started, as occasionally, the DOS require me to choose which OS that I want to boot, Windows XP Professional or Ubuntu 10.04 ... and I choose Ubuntu. Again it offer me by which kernel I want to boot in ... and I choose the latest one. After that, Ubuntu start screen won't showup, and the following-like text is show-up:

> 
Mount is denied because the NTFS volume is already exclusively opened. The volume maybe mounted or another software may use it which could be identified for example by the ... of the 'fused' command could not mount the partition /dev/disk/..-uuid/DA94067C94D65B19.
This could also happen if the file system is not clean because of an operation system error, interrupted boot process, an impropper shutdown, or unplugging of a removable device without first unmounting or ejecting it. To fix this, simply reboot into Windows, let it fully start, log in, run 'chkdsk /r', then gracefully shutdown and reboot back into Windows. After this you should be able to reboot again and resume the installation. (file system=NTFS, error code=16)
    I've done this four times ... but it always end to the same result.
    * 1st ... right-click C: => properties => tools' tab, checked & fixed disk error.
    * 2nd ... chkdsk /r + defragged by defraggler
    * 3rd ... chkdsk /r + defragged by Windows default's defragmenter
    * 4th ... chkdsk /r

All process ending to the same result.
Please help ...

---

