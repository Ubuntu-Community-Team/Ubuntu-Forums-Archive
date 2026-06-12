---
title: "How installing gcc"
date: 2004-12-08
forum: Programming Talk
---

### Post by pas71 on 2004-12-08
Hi,

I'm newbie with Ubuntu and Linux. I download iso file from ubunto web site and put it on CD. Install is ok. 
Now I would like to install Apache. I download package from apache.org web site, and when I want to install it, there is an error msg "can't find gcc or cc or...". How install gcc ?
Thanks for all

---

### Post by p!=f on 2004-12-08
[QUOTE=pas71]Hi,

I'm newbie with Ubuntu and Linux. I download iso file from ubunto web site and put it on CD. Install is ok. 
Now I would like to install Apache. I download package from apache.org web site, and when I want to install it, there is an error msg "can't find gcc or cc or...". How install gcc ?
Thanks for all[/QUOTE]
Do you want to compile Apache yourself instead of installing it from APT repositories?

To get development tools run
```

sudo apt-get install build-essential

```
To install Apache2 run
```

sudo apt-get install apache2-mpm-worker 

```

---

### Post by pas71 on 2004-12-08
Thank you very much,

That's what I want, that means no compiling but installing applications. 
And I just find another way by using "Synaptic Packet Manager".

---

