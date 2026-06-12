---
title: "LTS for Lubuntu versions"
date: 2013-11-30
forum: New to Ubuntu
---

### Post by wjbmd48 on 2013-11-30
Hi:

Sorry to ask such a dumb question: I'm confused about which Lubuntu versions are LTS. The terminal lsb_release -a tells me that I'm currently running "Ubuntu 12.04.3 LTS." I assume that what it means is that I'm running "LXDE Ubuntu," but I don't see anywhere that Lubuntu 12.04 is LTS.

Next question: I'm running several Thinkpad X40s: I can get version 13.10, and the daily build of 14.04 to run on my 1.6GHz machine, but not on the 1.5 GHz or below machines.  I assume this is because versions 13 and above require PAE processors (whatever that means!), and only the 1.6GHz machines meet this requirement, and that I'll only be able to run the stable, final version of 14.04 on these?

Thanks!

Bill

---

### Post by deadflowr on 2013-11-30
There is no LTS for Lubuntu yet.
Maybe 14.04, I'm not sure what state it is in.
If not, then possibly 16.04.

---

### Post by howefield on 2013-11-30
> **wjbmd48 said:**
> Sorry to ask such a dumb question: I'm confused about which Lubuntu versions are LTS. The terminal lsb_release -a tells me that I'm currently running "Ubuntu 12.04.3 LTS." I assume that what it means is that I'm running "LXDE Ubuntu," but I don't see anywhere that Lubuntu 12.04 is LTS.

It isn't an LTS, it is (or was) supported for 18 months meaning it went end of life October 2013. 14.04 should be an LTS with 5 years of support. I am sure that the components that are shared with Ubuntu will get updates as long as 12.04 is around though.

---

### Post by wjbmd48 on 2013-11-30
Thanks so very much for the replies, very helpful!

Bill

---

### Post by DuckHook on 2013-11-30
> **howefield said:**
> ...14.04 should be an LTS with 5 years of support.Didn't know that. Good news. 'bout time.

---

### Post by mörgæs on 2013-11-30
> **wjbmd48 said:**
> ... I assume this is because versions 13 and above require PAE processors...

Yes and no, PAE was also required for Lubuntu 12.10. 

If PAE is the problem you should get an explicit error message stating this. The failing boot can also be due to lack of RAM.

---

