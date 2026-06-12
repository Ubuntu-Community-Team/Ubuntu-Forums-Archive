---
title: "Which software should I use to check the notebook in linux system when I buy it ?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by cwfdx on 2008-08-21
As you know,there're many softwares we can use to check the notebook(or laptop) we want to buy,but I don't know what to use in linux.when you want to buy a notebook with Ubuntu or some system like this preinstalled,which software can help us to check out?

Thank you!

Paladin

---

### Post by t0p on 2008-08-21
If you want to check for compatibility, the ubuntu Live CD is the ideal tool.  It comes with a load of software installed, plus you can check for hardware detection etc.

---

### Post by cwfdx on 2008-08-21
That's a good idea,I know what you mean,I can do the job without installing any software.But could you tell more detailed about it please?Such as which software could I use and what should I pay attention to?
Thank you for help.

---

### Post by t0p on 2008-08-21
You could check for sound card compatibility.  And maybe video drivers? Though I don't think you'll be downloading drivers while in the store...

I guess the most important thing will be to test it with the software you will be using on it the most.  So you need to think about what you will want it for.

---

### Post by cwfdx on 2008-08-21
My purpose is just to test if the hardware is the one as the seller said,such as CPU/Memory/Hardware/Video Card.There're lots of cheaters and you couldn't carefull enough.Maybe there's no such problems in your country:)In windows,we have a lot softwares to do this,EVEREST&#12289;CPU-Z&#12289;BatteryMon&#12289;HD Tune&#12289;DisplayX&#65292;and etc,I think there must be software with the same function in Linux.
I ask this question because I want to buy a laptop with Linux preinstalled,but I don't know how to test it:)
Maybe I didn't explain properly or our environment is quite different,thank you for the help,I appreciate it.

---

### Post by Joeb454 on 2008-08-21
In Windows you can run "dxdiag"

And in Linux you look at the files in ```
/proc/cpuinfo
/proc/meminfo
```

Not sure what you would look at for Video Cards though

---

### Post by hyper_ch on 2008-08-21
or run:

```

sudo lshw -html > ~/Desktop/system.html

```

That will put all hardware info in the file on your desktop.

---

### Post by billgoldberg on 2008-08-21
The system monitor should also tell you this.

Also, the 'lshw' command should tell you some things.

---

### Post by cwfdx on 2008-08-21
> **Joeb454 said:**
> In Windows you can run "dxdiag"

And in Linux you look at the files in ```
/proc/cpuinfo
/proc/meminfo
```

Not sure what you would look at for Video Cards though


What the seller told me maybe not true,I just want to check the authenticity.And they can modify BIOS to change someting and the parameter appeares more higher.For a example,the seller told you the video card in the notebook is 64M,but the truth is 32M and the system info is 64M video card too...Maybe there're no such problem in your country,everyone is honest:)
The same notebook,can be sold at the very different price just because the different seller and different buyer.The more you know about it,the chance being cheated will smaller.
Thank you for your advice,it's helpful.

---

