---
title: "AMD Crossfire"
date: 2014-07-28
forum: New to Ubuntu
---

### Post by Dustin_Whisenhunt on 2014-07-28
Will it be possible to crossfire my A10-7859K APU with the R7250 on Linux? If so how would I be able to set it up

---

### Post by QIII on 2014-07-29
Folks, let's address [this]("http://ubuntuforums.org/showthread.php?t=2236777") post first, please.

---

### Post by Dustin_Whisenhunt on 2014-07-29
Thank you. I know it is possible on Windows but I would like to get it working on Linux.

---

### Post by QIII on 2014-07-29
OK.  But let's get your other issue fixed first, or this one won't matter.

---

### Post by Vladlenin5000 on 2014-07-29
> **Dustin_Whisenhunt said:**
> Thank you. I know it is possible on Windows but I would like to get it working on Linux.

No, it isn't. Unlike nVIDIA's SLI, CrossFire requires two identical cards.

---

### Post by Dustin_Whisenhunt on 2014-07-30
Alright. I'm able to get steam to open now. Now to try and see if I can get crossfire going

---

### Post by Dustin_Whisenhunt on 2014-07-30
> **Vladlenin5000 said:**
> No, it isn't. Unlike nVIDIA's SLI, CrossFire requires two identical cards.

[http://www.amd.com/en-us/innovations/software-technologies/dual-graphics#desktop](http://www.amd.com/en-us/innovations/software-technologies/dual-graphics#desktop)

According to a lot of the internet and AMD itself. Yes it does.

---

### Post by QIII on 2014-07-30
... but ...

It works for Windows.  I'm not sure if the Linux driver will do that. I'll have to dig, but I'm not hopeful.

Glad to see you got the driver sorted out.

Could you post the results of

```
 fglrxinfo 
```

Also, after you got the fglrx driver installed, did you do

```
 sudo amdconfig --adapter=all --initial 
```

---

