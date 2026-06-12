---
title: "motherboard max RAM"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by Primus1 on 2012-10-19
Hi, my motherboard will take 8gb or RAM maximum. Is there a downside to installing this 8gb maximum? I run Lucid 10.04 now but will update to 12.10. Will run ok with 8gb RAM?

---

### Post by Cheesemill on 2012-10-19
No downside at all, the more RAM the better.

Just make sure you install the 64-bit version of Ubuntu if your CPU supports it. You can find this out by pasting the following into a terminal:
```
grep -q "^flags.*\blm\b" /proc/cpuinfo && echo "Yes you have a 64 bit CPU." || echo "No 64 bit for you."
```

---

### Post by SlugSlug on 2012-10-19
If you have a 64bit CPU and use a 64bit OS then your fine

```
cat /proc/cpuinfo
```look for flags and 64bit CPU has lm flag


and 
```
uname -a 
```will show if you have 32 / 64 installed 

(i386  or x86_64)

---

### Post by Primus1 on 2012-10-19
> **Cheesemill said:**
> No downside at all, the more RAM the better.

Just make sure you install the 64-bit version of Ubuntu (or any OS).

Ah, I have always used  the 32-bit 'recommended' OS. I tried once to find out which was best but the answers were confusing, some said yes and some no, both views supported with evidence.

8gb is not supported using 32-bit RAM then?

---

### Post by Primus1 on 2012-10-19
> **Cheesemill said:**
> No downside at all, the more RAM the better.

Just make sure you install the 64-bit version of Ubuntu if your CPU supports it. You can find this out by pasting the following into a terminal:
```
grep -q "^flags.*\blm\b" /proc/cpuinfo && echo "Yes you have a 64 bit CPU." || echo "No 64 bit for you."
```

Thank you, your code gave the answer - "yes you have a 64bit cpu"

---

### Post by jerrrys on 2012-10-19
You can run either 32 or 64bit with 8gig of ram.

---

### Post by Cheesemill on 2012-10-19
> **jerrrys said:**
> You can run either 32 or 64bit with 8gig of ram.
But there is no good reason whatsoever to choose 32-bit.

---

### Post by Primus1 on 2012-10-19
> **Cheesemill said:**
> But there is no good reason whatsoever to choose 32-bit.

When you go to download Ubuntu iso it says 32bit 'recommended'

I wish there was clarity about 32 or 64bit, very confusing for users like me (not experts)

---

### Post by Cheesemill on 2012-10-19
This was meant to be changed several releases ago, but for some reason the devs changed their mind.

For a full bug-report and discussion see:
[https://bugs.launchpad.net/ubuntu-website-content/+bug/585940/+index?comments=all](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940/+index?comments=all)

---

### Post by jerrrys on 2012-10-19
> **Cheesemill said:**
> But there is no good reason whatsoever to choose 32-bit.

Its a preference, not a major decision.  They both work just fine. And Im not saying any more so this thread will not end up in recurring discussions  :)

---

### Post by Primus1 on 2012-10-19
Maybe it recurs because there is no clear answer. I'm not being funny, just wish to know if 32bit will accept and utilise 8gb of RAM effectively. 

Please if an Ubuntu big brain will let me know?

Thanks for all the answers here.

---

### Post by SlugSlug on 2012-10-19
If you want to use more that 4GB RAM (well 3.75 I think) then you should use a 64bit OS

---

### Post by Cheesemill on 2012-10-19
32-bit will show all of you memory as available because the 32-bit kernel has something called [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension").

However, take a read at what Linus Torvalds (the guy who created Linux) has to say about it:
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

---

### Post by SlugSlug on 2012-10-19
TBH you should use a 64bit OS if you have a 64bit CPU - never mind the RAM :)

---

### Post by SlugSlug on 2012-10-19
I'd stay away from PAE

---

### Post by Axxon95 on 2012-10-19
If you have a 64-bit CPU, and have that much RAM, **I say go 64-bit**, the performance is far superior to 32-bit.
Since 12.04, you can install 32-bit programs onto a 64-bit OS, so if you have a program that absolutely needs to have 32-bit you won't have an issue.
I personally have 8GB of RAM, and I had to run 10.04 32-bit because I needed 32-bit support for an emulator I use, and at the time Ubuntu 12.04 64-bit didn't want to install on my computer. I wasn't nearly using my machine to it's full potential.

Though if you choose 32-bit.
Most likely if a mobo supports 8GB of ram, the processors it can have installed have "PAE", an extention to 32-bit that allows over 3.2GB ram(though I believe once you go past, the ram access slows down).

---

### Post by Axxon95 on 2012-10-19
> **Primus1 said:**
> Maybe it recurs because there is no clear answer. I'm not being funny, just wish to know if 32bit will accept and utilise 8gb of RAM effectively. 

Please if an Ubuntu big brain will let me know?

Thanks for all the answers here.

32-bit(with PAE) will accept, but not utilize at full potential.

---

### Post by Primus1 on 2012-10-19
> **Cheesemill said:**
> 32-bit will show all of you memory as available because the 32-bit kernel has something called [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension").

However, take a read at what Linus Torvalds (the guy who created Linux) has to say about it:
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)


He's a bit angry isn't he? Well if 64gb is what he recommends then I must take his advice. How do I increase the virtual memory he mentioned?

---

### Post by Primus1 on 2012-10-19
> **SlugSlug said:**
> I'd stay away from PAE

How do I avoid it? Is it on my computer now? Can I stop it?

---

### Post by drmrgd on 2012-10-19
> **Cheesemill said:**
> This was meant to be changed several releases ago, but for some reason the devs changed their mind.

For a full bug-report and discussion see:
[https://bugs.launchpad.net/ubuntu-website-content/+bug/585940/+index?comments=all](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940/+index?comments=all)

They need to change their minds back and re-open this bug report (or fix it).  I can't count the number of times a user has downloaded the 32-bit version because it's 'recommended' and only after wasting hours trying figure out why UEFI wouldn't work or worse spending a lot of time setting up their system only to find out that their total amount of memory wasn't supported.  I'm going to chime in on there too; maybe if they hear enough volume on this, they'll make the -extremely simple!- change to the website.

---

### Post by pqwoerituytrueiwoq on 2012-10-19
> **SlugSlug said:**
> TBH you should use a 64bit OS if you have a 64bit CPU - never mind the RAM :)
+1
if you are already using a 32bit OS and don't want to reinstall switching to PAE is a nice option if you upgrade your ram

---

