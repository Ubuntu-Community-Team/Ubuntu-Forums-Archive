---
title: "[SOLVED] Which kernel comes with 8.04.1..."
date: 2008-10-06
forum: New to Ubuntu
---

### Post by two4two on 2008-10-06
It looks like 2.6.24-19-generic is what came with 8.04.1...
Is this true?  If so, how do I get the absolute latest and greatest and use it instead?  I'm figuring I can go to "The Linux Kernel Archives" and get the latest.  If I do, then which should I get and how do I make my Ubuntu 8.04 use it?  The reason I'm investigating this is because my TrendNet TEW-424UB doesn't seem to be picked up by Ubuntu and I've found some web forums that talk about various USB WLAN devices that use the RealTek chips and that there is a RealTek driver in 2.6.27.  Since I'm a newbie I thought that being current would be a good idea because it might help me avoid dealing with drivers right now.

---

### Post by hyper_ch on 2008-10-06
why not upgrading to 8.10 Beta?

---

### Post by two4two on 2008-10-06
I saw 8.04 was a LTS release (not that I know what that gives me).  What does 8.10 Beta provide over 8.04?  Remember, I am a Linux and Ubuntu newbie, and so maybe, since it is a Beta, it could give me problems I wouldn't know how to deal with.

---

### Post by two4two on 2008-10-06
I saw 8.04 was a LTS release (not that I know what that gives me).  What does 8.10 Beta provide over 8.04?  Remember, I am a Linux and Ubuntu newbie, and so maybe, since it is a Beta, it could give me problems I wouldn't know how to deal with.

---

### Post by philinux on 2008-10-06
> **two4two said:**
> I saw 8.04 was a LTS release (not that I know what that gives me).  What does 8.10 Beta provide over 8.04?  Remember, I am a Linux and Ubuntu newbie, and so maybe, since it is a Beta, it could give me problems I wouldn't know how to deal with.

Long term support means just that, for security updates. [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

8.1 due end of this month was focused to improve wireless.

I'd suggest downloading the livecd and see if it picks up you card. 
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by shifty_powers on 2008-10-06
well ibex uses the kernel you are after.

```
shifty@shifty-laptop:~$ uname -r
2.6.27-5-generic
```

---

### Post by smarks on 2008-10-06
I am trying out 8.10 Beta on one of my other machines. It seems to be alot better and have more support. i like it. I cant wait until they release the final 8.10 on oct 30th :)

---

### Post by two4two on 2008-10-07
True.  It is 2.6.24-19-generic that comes with 8.04.1, and true:  2.6.27-5-generic comes with 8.10 Beta.  I tested the beta and it does have the Realtek RTL8187 driver and after setting up the network I was able to connect to our familiy's Windows network.  I couldn't print a document on one of the printers because I don't have Linux drivers for the printers.  I was also able to get to the internet.  So other than waiting for the 8.10 final release it looks as though I could manually install and configure the RTL8187B linux driver as is mentioned in some web posts I've found.  Being a newbie I'll definitely be challenged!  Actually, I can predict that by the time I figure it out 8.10 will be released.  So now I'm focusing on HP printer drivers.  Darn if it isn't always something.

---

### Post by billgoldberg on 2008-10-07
> **two4two said:**
> True.  It is 2.6.24-19-generic that comes with 8.04.1, and true:  2.6.27-5-generic comes with 8.10 Beta.  I tested the beta and it does have the Realtek RTL8187 driver and after setting up the network I was able to connect to our familiy's Windows network.  I couldn't print a document on one of the printers because I don't have Linux drivers for the printers.  I was also able to get to the internet.  So other than waiting for the 8.10 final release it looks as though I could manually install and configure the RTL8187B linux driver as is mentioned in some web posts I've found.  Being a newbie I'll definitely be challenged!  Actually, I can predict that by the time I figure it out 8.10 will be released.  So now I'm focusing on HP printer drivers.  Darn if it isn't always something.

I don't see a reason as to why you should just use the beta.

It's pretty stable (meaning I haven't got any problems with it).

---

### Post by shifty_powers on 2008-10-07
i've been using kubuntu 8.10 for about 4 weeks and have absolutely loved it.

highly recommended :D

---

### Post by two4two on 2008-10-07
Thanks Bill, I guess I will use the Beta.  Now, on to figure out printer dirvers.

---

