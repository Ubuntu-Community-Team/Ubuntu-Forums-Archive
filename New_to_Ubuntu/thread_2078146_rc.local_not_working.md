---
title: "rc.local not working"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by mubas32 on 2012-10-30
Clicking noise from hard drive while operating on battery power
 
I run this command on terminal

echo 0 | sudo tee /sys/module/snd_hda_intel/parameters/power_save 

and it stopped
 
And to solve it permanently I added the following line above "exit 0" in "/etc/rc.local". 

echo 0 > /sys/module/snd_hda_intel/parameters/power_save

But after restarting it doesn't seems working

---

### Post by NikTh on 2012-10-30
Hi , 
try to add a sleep (delay time) . 

make the line inside rc.local like this 

```
(sleep 3 ;  echo 0 > /sys/module/snd_hda_intel/parameters/power_save) &
``` 

Be aware that the line must be **before** _exit 0_

Thanks

---

### Post by mubas32 on 2012-10-30
Thank You for your time, But Its not working

---

### Post by NikTh on 2012-10-30
Are you sure that the command works from terminal ? 

If Yes , then maybe you can increase the delay option .. 

eg: ```
sleep 10
```

Thanks

---

### Post by mubas32 on 2012-10-30
ok will try that

---

### Post by varunendra on 2012-11-01
> **mubas32 said:**
> Clicking noise from hard drive while operating on battery power
 
I run this command on terminal

echo 0 | sudo tee /sys/module/snd_hda_intel/parameters/power_save 

and it stopped
snd_hda_intel is an audio driver and it has nothing to do with HDDs. Either the noise was coming from speakers (may happen), or it was just a coincidence that the noise stopped using above command.

If you are sure it is coming from HDD, then it is an indication of failing HDD (the noise is made due to unexpected read failures - for whatever reasons), as we all know. Backup your data, then try whatever workaround you have.

And by the way,the command to get/set HDD parameters (including power management) is **hdparm**.

---

### Post by mubas32 on 2012-11-01
Thanks for your message, By increasing sleep time my problem had stopped...

---

### Post by mubas32 on 2012-11-01
Thanks man....its OK now

---

