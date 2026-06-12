---
title: "Forgot whether 32bit or 64bit is installed ..."
date: 2011-09-14
forum: New to Ubuntu
---

### Post by klytu on 2011-09-14
I installed Ubuntu 11.04 on a flash drive for testing and use on a netbook. I'm embarrassed to say that I forgot whether the version I installed is 32bit or 64bit. Is there a simple way to determine this? I've tried both 

```
cat /etc/lsb-release
``` for the Ubuntu version and 
```
uname -r
``` for the running kernal, but neither command tells me whether I'm running 32bit or 64bit.

---

### Post by howefield on 2011-09-14
Try 

```
uname -a
```

If you see x86_64 in the output, you have a 64 bit installation eg,

```
Linux natty-desktop 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by haqking on 2011-09-14
> **howefield said:**
> Try 

```
uname -a
```If you see x86_64 in the output, you have a 64 bit installation eg,

```
Linux natty-desktop 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

+1 also see:

```
uname -m
```

as it iis a little clearer as it is more specific

---

### Post by klytu on 2011-09-14
Thanks, howefield and haqking! Just what I needed.

---

