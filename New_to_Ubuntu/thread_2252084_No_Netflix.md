---
title: "No Netflix"
date: 2014-11-08
forum: New to Ubuntu
---

### Post by ray9 on 2014-11-08
Ubuntu 14.04 LTS.  Chrome won't install "wrong architechure amd64".  What can I do?

---

### Post by QIII on 2014-11-08
Hello!

Are you running a 64bit operating system?  Did you download the 32bit version of Chrome?

Perhaps vice versa?

You need to download the .deb that matches the bit width of your OS.

Cheers!

---

### Post by ray9 on 2014-11-08
I'm running 64 bit and downloaded the 64 bit, I think.  How can I check my version of Linux?  OMG I am running the 32 bit version!  What can I do now?  How can I reinstall w/o losing EVERYTHING?

---

### Post by QIII on 2014-11-08
Issue the following command in the the terminal

```

uname -a
```

If you see "x86_64" towards the end, you are running a 64 bit version of Ubuntu.

---

### Post by ray9 on 2014-11-08
3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux  I'm running 2 drives one with Mint 17 and one with Ubuntu 14.04.  I thought they were both 64 bit.

---

### Post by QIII on 2014-11-08
You can check Mint the same way.

So, I guess the thing to do would be to make sure you install the 64-bit version of Chrome.

---

### Post by ray9 on 2014-11-08
Mint is 64 bit and I installed Chrome w/o a hitch.  Now, my computer is 64 bit, should  reinstall Ubuntu 64 bit or leave it at 32?  Will I lose everything if I reinstall or can I save "home"?

---

### Post by yancek on 2014-11-08
You can save home if it is on a separate partition or you can back it all up and copy it back after installing.

---

### Post by deadflowr on 2014-11-08
> **ray9 said:**
> 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux  I'm running 2 drives one with Mint 17 and one with Ubuntu 14.04.  I thought they were both 64 bit.

Which one is this?
(Mint or Ubuntu's uname -a output)
because it reads as 64-bit.
[call me confused]

---

### Post by ray9 on 2014-11-09
That would be Mint.  Thanks for all the replies.  The 32 bit Ubuntu version is working fine so I'm going to leave it alone.  It seems that I got the 2 DVD's mixed up and miss labled.  The 32 is the 64 and vice versa.

---

