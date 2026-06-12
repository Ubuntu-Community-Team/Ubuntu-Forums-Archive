---
title: "Continuous installation error on budgie."
date: 2019-03-31
forum: New to Ubuntu
---

### Post by xbccoffee on 2019-03-31
Hello again.
This is more of a second part of my previous thread, go read that one for more context.

So, I've decided to reinstall Ubuntu Budgie after the previous incident. I erased the disk and now formatting in ext4, but I always get this error when attempting to install:

"The hard disk is 3000 bytes (approx.) offset from the minimum area. This could lead to very poor performance." 

My partitions:

/swap=4500 MB (RAM is 4GB)
/ = rest of external HDD (area where i will install- boot and root merged)

So yeah, any help?

I'm installing on the dell inspiron 530. I'm a complete newbie and I have no experience neither ubuntu nor linux.

Thanks in advance.

---

### Post by Rubi1200 on 2019-04-01
I recommend booting from the liveUSB and following the instructions to create a boot repair summary. Note, please only create the report to paste here so we can take a closer look at what is going on with the partitions.

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Thanks.

---

### Post by xbccoffee on 2019-04-02
> **Rubi1200 said:**
> I recommend booting from the liveUSB and following the instructions to create a boot repair summary. Note, please only create the report to paste here so we can take a closer look at what is going on with the partitions.

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Thanks.

I solved this issue because i realized I did not use gparted. Thanks for the help.

---

### Post by xbccoffee on 2019-04-02
> **Rubi1200 said:**
> I recommend booting from the liveUSB and following the instructions to create a boot repair summary. Note, please only create the report to paste here so we can take a closer look at what is going on with the partitions.

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Thanks.

I solved this issue because i realized I did not use gparted. Thanks for the help :)

---

### Post by Rubi1200 on 2019-04-02
Glad to hear it all worked out in the end.

Please use the Thread Tools at top of the post to mark Solved.

Good luck!

---

