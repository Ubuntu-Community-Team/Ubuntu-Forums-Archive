---
title: "Join FLV Files Together"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by s.fox on 2008-10-23
Hi,

I have 3 FLV files that I would like to join together to make a single FLV file.  Does anybody know a good way of doing this?

Thanks for any help,  much appreciated.

-Ash R

---

### Post by sleepingdragon on 2008-10-23
Avidemux can import and join video files, and can use .flv. Just insert them in the right order. Load up the first one, then use the Append function to insert the second and repeat the same for the third. 

Avidemux also supports an excellent range of output files too.

Just use:

> sudo apt-get install avidemux

in a terminal, or you can find it in Synaptic. If you want the latest version, try the [Avidemux website.]("http://fixounet.free.fr/avidemux/")

---

### Post by aeiah on 2008-10-23
```
mencoder -forceidx -of lavf -oac copy -ovc copy -o output.flv clip1.flv clip2.flv clip3.flv
```

---

### Post by maka on 2008-10-24
> **aeiah said:**
> ```
mencoder -forceidx -of lavf -oac copy -ovc copy -o output.flv clip1.flv clip2.flv clip3.flv
```

worked great. thanks

---

### Post by Jimmmac1 on 2011-10-20
Good afternoon

Where do I get, or how do I install MEncoder? I looked around but any references I found were ambiguous.  Running Ubuntu 11.10.  Thanks.

Jim

---

### Post by bryncoles on 2011-10-20
Hi Jimmmac1.  

Unless I miss my guess, you should be able to get Mencoder from the Ubuntu Software Centre.  Luddite that I am, I'm not on Ubuntu 11:10 yet, or I'd check its availability.  

I believe you should also be able to simply type 

```
sudo apt-get install mencoder
``` into a terminal too.  

You have all the standard repositories -- such as medibuntu -- activated, right?

---

### Post by oldos2er on 2011-10-20
Back to sleep. If you have a problem or questions, please start a new thread.

---

