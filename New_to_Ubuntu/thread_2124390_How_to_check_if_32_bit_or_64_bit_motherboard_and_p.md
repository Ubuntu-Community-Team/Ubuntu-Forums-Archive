---
title: "How to check if 32 bit or 64 bit motherboard and processor?"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by WhiteHatGuy on 2013-03-10
Hi

Sorry for my english, is not my native language.

I am very noob on this topic.

I was wondering how can I check in lubuntu, my motherboard and processor architecture, 32 bit or 64 bit.

Its very important that show this information about motherboard not only processor or cpu.

Or if there is any tool like cpu-z for linux.

What shoud I look for?

Thing is I think I have a processor capable of 32 bits and 64 bits, but my mother board is 32 bits architecture only.

When I try to install Lubuntu 64 bits, sais this system does not support 64 bit enviroment.

Thanks

---

### Post by pinballwizard on 2013-03-10
```

dmidecode | more
```

If it moans, run it as sudo... 
(as a habit, I remove "sudo" when posting code...)
For more go here:
[http://diznix.com/2012/01/07/linux-equivalent-of-cpu-z/](http://diznix.com/2012/01/07/linux-equivalent-of-cpu-z/)

---

### Post by mikewhatever on 2013-03-10
Why not browse to the vendor website and read the specs? ...both for the board and CPU.

---

### Post by gifford on 2013-03-10
To answer your question, there is CPU-G and i-Nex available. Here is a link on how to download both.
[http://www.noobslab.com/2013/03/cpu-g-and-i-nex-hardware-info-utilities.html](http://www.noobslab.com/2013/03/cpu-g-and-i-nex-hardware-info-utilities.html)

---

### Post by Cheesemill on 2013-03-11
Copy and paste the following into a terminal...
```
grep -q "^flags.*\blm\b" /proc/cpuinfo && echo "Your machine is 64-bit capable" || echo "No 64-bit for you"
```

If you post the make and model of your CPU and motherboard we can give a definite answer.

---

### Post by schragge on 2013-03-11
Another terminal command that gives you infos on your processor is
```
lscpu
``` Basically, it evaluates contents of */proc/cpuinfo* and presents them to you in a nice, human-readable form.

---

