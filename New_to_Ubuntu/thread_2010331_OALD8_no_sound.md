---
title: "OALD8 no sound"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by IVANNHS on 2012-06-25
Hello,

   I installed OALD8 on ubuntu 12.04 but I cannot hear the pronunciation of the words. 

thanks in advance
Yiannis P.

---

### Post by Hadaka on 2012-06-25
try this 

[http://forums.debian.net/viewtopic.php?f=16&t=61164](http://forums.debian.net/viewtopic.php?f=16&t=61164)

#line 3 refers to no sound#

hope this helps.

---

### Post by IVANNHS on 2012-06-25
ioannis@ioannis-GA-MA74GM-S2H:~$ su
Password: 
root@ioannis-GA-MA74GM-S2H:/home/ioannis# modprobe snd-pcm-oss
FATAL: Module snd_pcm_oss not found.
root@ioannis-GA-MA74GM-S2H:/home/ioannis#

---

### Post by Hadaka on 2012-06-25
check your alsamixer to see if pcm has a value greater than 0

terminal ctrl/alt/t

code:
alsamixer

---

### Post by IVANNHS on 2012-06-25
The pcm is 100<>100
In ubuntu 11 I had no problems with the pronunciation in oald8

---

### Post by mgt2000 on 2012-07-11
I have the same problem and pcm in my system is 100 too

---

### Post by IVANNHS on 2012-07-12
> **mgt2000 said:**
> I have the same problem and pcm in my system is 100 too



I think oald8 uses the obsolete OSS sound API, which has been replaced by the ALSA API.  The OSS API was removed from the kernel last year (see bug #579300)

[http://askubuntu.com/questions/79740/xvidcap-error-accessing-sound-input-from-dev-dsp](http://askubuntu.com/questions/79740/xvidcap-error-accessing-sound-input-from-dev-dsp)

---

### Post by heroandtn3 on 2012-09-01
> **IVANNHS said:**
> Hello,

   I installed OALD8 on ubuntu 12.04 but I cannot hear the pronunciation of the words. 

thanks in advance
Yiannis P.

Try this:

```
$ padsp '/home/path_to_folder/oald8//oald8'
```

---

### Post by IVANNHS on 2012-09-01
It works!
thank you
Yiannis P.

---

