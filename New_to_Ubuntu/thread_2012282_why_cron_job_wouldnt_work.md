---
title: "why cron job wouldnt work?"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by 007casper on 2012-06-28
I set up a cron job.  It worked for a day or two and then stopped working.

I cant figure out why...

crontab -e
> 
# m h  dom mon dow   command
*/15 * * * * /root/repeat/file.sh


then, the file.sh
> 
-rwxr--r-- 1 root root  337 2012-06-14 04:41 file.sh


please advise

---

### Post by papibe on 2012-06-28
Hi 007casper.

Is that your regular user's crontab? If so, you don't have execution permission.

Regards.

---

### Post by 007casper on 2012-06-28
>>you don't have execution permission.

you mean it should be
-rwxr-xr-- 1 root root 337 2012-06-14 04:41 file.sh

---

### Post by papibe on 2012-06-28
More like:
```
-rwxr-xr-**[COLOR="Red"]x[/COLOR]** 1 root root 337 2012-06-14 04:41 file.sh
```
Because you are not member of the 'root' group.

Regards.

---

### Post by 007casper on 2012-06-28
thanks

---

