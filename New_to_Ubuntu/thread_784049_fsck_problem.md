---
title: "fsck problem"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by ggaaron on 2008-05-06
I have a problem with ubuntu and fsck - I mean, I have an external drive added to fstab, so it will mount in the same place all the time. The problem is, that if I unplug it, then ubuntu on startup tells me that a drive is missing and fsck error occurred. How can I disable this check, so it will just ignore missing drives?

Thanks in advance
Aaron

---

### Post by glennric on 2008-05-06
Add the option "noauto" (without the quotes) to fstab.

---

### Post by ggaaron on 2008-05-06
Then it won't ever auto mount - it should mount when there is drive plugged in, but not panic and abandon boot when there isn't...

---

### Post by philinux on 2008-05-06
> **ggaaron said:**
> I have a problem with ubuntu and fsck - I mean, I have an external drive added to fstab, so it will mount in the same place all the time. The problem is, that if I unplug it, then ubuntu on startup tells me that a drive is missing and fsck error occurred. How can I disable this check, so it will just ignore missing drives?

Thanks in advance
Aaron

Do you unmount it before unplugging?

---

### Post by jw5801 on 2008-05-06
> **ggaaron said:**
> I have a problem with ubuntu and fsck - I mean, I have an external drive added to fstab, so it will mount in the same place all the time. The problem is, that if I unplug it, then ubuntu on startup tells me that a drive is missing and fsck error occurred. How can I disable this check, so it will just ignore missing drives?

Thanks in advance
Aaron

Alter the lines in /etc/fstab so that the two numbers at the end are both 0, ie:
```
# /dev/sdb1
LABEL=testing   /mnt/testing    reiserfs relatime       0      0
```

That will tell fsck that it doesn't need to worry about checking these drives.

---

### Post by ggaaron on 2008-05-06
I do unmount the drive.

If I change last numbers to 0 0, then fsck won't check my drive even then it is plugged. It is rather not fsck, but ubuntu/upstart problem - it shouldn't stop booting when not crucial drives are missing.

---

### Post by bodhi.zazen on 2008-05-06
There is no simple solution. The only other option I can think of would be to write a script, testing for the presence of your drive (by uuid) and if so mount the device.

You can then unmount the device and manually run fsck if needed.

---

### Post by ggaaron on 2008-05-06
Ok, I've altered the checkfs script to ignore fsck exitcode 8, It skips not present devices now, but it does kill splash when fsck exits with error. What I've done is:
if [ "$FSCKCODE" -gt 1 ] changed to if [ "$FSCKCODE" -gt 1 ] && [ "$FSCKCODE" -ne 8 ]
in two places, but I can't see what kills the splash.

---

### Post by ggaaron on 2008-05-06
I fixed this by applying the solution above also to /lib/init/usplash-fsck-functions.sh file. Now everything works=) Thanks for your support and help.

Aaron

---

