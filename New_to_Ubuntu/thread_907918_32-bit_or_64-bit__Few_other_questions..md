---
title: "32-bit or 64-bit?  Few other questions."
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Dave88LX on 2008-09-02
I apologize in advance for what seems like a very basic question.  I mainly want to clear up some rumors.  I have an Acer 5004 WLMI laptop ([http://www.shopping.com/xPF-Acer-Acer-Aspire-5004WLMi-Turion64-ML34-1-8GHz-1GB-100GB-DVD-R-15-4-LX-A5105-328](http://www.shopping.com/xPF-Acer-Acer-Aspire-5004WLMi-Turion64-ML34-1-8GHz-1GB-100GB-DVD-R-15-4-LX-A5105-328)), which is running an AMD Turion 64 ML-34 processor.  One one hand, I've been told I need the 64-bit version, on the other hand, I've been told the 32-bit version will work just fine, and have better driver support.  So, which one do I need?

I was unable to get a fully functional boot CD, it always hung up once I made a choice when it booted from the CD (Yes I did use InfraRecorder to make the CD).  What I ended up doing was just opening the 64-bit ISO file with MagicISO, running WUBI from there, and was able to successfully install Ubuntu.

However, once inside, I did not have wireless support.  It shows up in Windows Device Manager as a "Broadcom 802.11g Network Adapter".  I don't know if there is something more specific that I need to do?

I have since uninstalled, with the thought I might need to run the 32-bit version instead...not sure what the correct next step is here?

Thanks for your help.

---

### Post by dRock1286 on 2008-09-02
How much memory are you running?  To my understanding, if you are running under 4gigs (3.3 to be exact I believe) a 32 bit will work and is suggested...

---

### Post by ~LoKe on 2008-09-02
32bit is the best way to go if you're not all too excited about dealing with a large array of problems.  Sure, 64bit could work out fine (like it did for me), but odds are it won't benefit you much.

---

### Post by Dave88LX on 2008-09-02
I only have 1 Gig of memory in this machine.

I wasn't sure if since I have what looks to be a 64-bit processor, if I HAD to run the 64-bit version.  I've been told that I don't though.

---

### Post by egalvan on 2008-09-02
> **dRock1286 said:**
> How much memory are you running?  To my understanding, if you are running under 4gigs (3.3 to be exact I believe) a 32 bit will work and is suggested...

32bits will run with more than 4gRAM.

> **Dave88LX said:**
> I only have 1 Gig of memory in this machine.

I wasn't sure if since I have what looks to be a 64-bit processor, if I HAD to run the 64-bit version.  I've been told that I don't though.

64bit Linux will only run on 64bit architecture,
32bit Linux will run on both.

As of Hardy (8.04), 32bit support is very good,
but 64bit is still spotty, your experience will vary.
Mine was not so good. Went back to 32.

The rumors are that Intrepid (8.10) will bring much better 64bit support. I for one cannot wait...

---

### Post by dRock1286 on 2008-09-02
Yes it will run with more than that, but it won't read or address more than that

---

### Post by Perfect Storm on 2008-09-02
My suggestion is you try both. As far as I know the only real problem is java in the browser but there's some good workaround on the forum (check our 64-bit forum).
When Sun java hits v1.7 it should be 64-bit compatible.

---

### Post by egalvan on 2008-09-02
> **dRock1286 said:**
> Yes it will run with more than that, but it won't read or address more than that

Sorry, it's just that the way you stated it...

> if you are running under 4gigs (3.3 to be exact I believe) a 32 bit will work and is suggested...

can give the impression that more memory would not let 32bit work.

A little lengthy quote, but an eye-opener for most folks, especially those coming from Windows.

n.b. this is from sept-07, a year old.
full article at:
[http://www.linux.com/feature/119287](http://www.linux.com/feature/119287)

[I]The problem exists because 32-bit Linux kernels are designed to access only 1GB of RAM by default. The workaround for this limitation is vaguely reminiscent of the virtual memory solution once used by DOS, with a high memory area of virtual memory being constantly mapped to physical addresses. This high memory can be enabled for** up to 4GB by one kernel parameter, or up to 64GB **on a Pentium Pro or higher processor with another parameter. However, since these parameters have not been needed on most machines until recently, the standard kernels in many distributions have not enabled them.

Increasingly, many distributions are enabling high memory for 4GB. **Ubuntu default kernels have been enabling this process at least since version 6.10,** and so have Fedora 7's. By contrast, Debian's default 486 kernels do not. **Few distros, if any, enable 64GB by default.**

To check whether your kernel is configured to use all your RAM, enter the command free -m. This command gives you the total amount of unused RAM on your system, as well as the size of your swap file, in megabytes. If the total memory is 885, then no high memory is enabled on your system (the rest of the first gigabyte is reserved by the kernel for its own purposes). Similarly, if the result shows over 1 gigabyte but less than 4GB when you know you have more, then the 4GB parameter is enabled, but not the 64GB one. In either case, you will need to add a new kernel to take full advantage of your RAM.

On some distributions, you can add a generic kernel that meets your requirement in a matter of moments. In Debian, for instance, use the apt-cache search command to locate a recent linux-image package for a kernel for a 686 processor if you want support for up to 4 gigabytes. If you want support for up to 64 gigabytes, look for a kernel that ends with 686-bigmem. These kernels will enable support for 64GB. Unfortunately, a generic kernel for only 4GB does not exist. Similarly, **in Ubuntu, look for a recent kernel image whose package name ends in smp;** these kernels are designed for dual core processors, but work on single core processors as well, although sometimes with a small performance hit.[/I]

---

### Post by hyper_ch on 2008-09-02
go for 64bit.... there's no real reason anymore to stick with 32bit.

Even java is not a problem anymore.

---

### Post by Dave88LX on 2008-09-07
Well, I've got the 32-bit up and going, so I'll keep it for now until I know Ubuntu better, then maybe switch it out with the 64-bit.  Thank you :)

---

### Post by Xiong Chiamiov on 2008-09-07
> **hyper_ch said:**
> go for 64bit.... there's no real reason anymore to stick with 32bit.

Even java is not a problem anymore.
It depends on what you're using.  This week I installed a 64-bit OS for the first time, and kept it for only a day, because I couldn't get several things to work quite right (Wine being one of them).

---

### Post by hyper_ch on 2008-09-08
wine works fine on 64bit

---

### Post by Perfect Storm on 2008-09-08
> **hyper_ch said:**
> wine works fine on 64bit

Same here.

+ all the other applications I use.

---

### Post by SunnyRabbiera on 2008-09-08
Yes but I still hear of reports with the 64 bit version, flash and java still seem to be a major issue.

---

### Post by Perfect Storm on 2008-09-08
> **SunnyRabbiera said:**
> Yes but I still hear of reports with the 64 bit version, flash and java still seem to be a major issue.

Yes, but there's a way to overcome these issues which can be found on our 64-bit forum. Have both flash and java working (32-bit browser).

---

### Post by hyper_ch on 2008-09-08
flash and java both work fine on 64bit...

---

### Post by Paqman on 2008-09-08
> **hyper_ch said:**
> flash and java both work fine on 64bit...

+1

Flash and Java *used to* be a problem, and required the use of the 32-bit version of Firefox. That was fixed a couple of versions back, and is no longer an issue. The user experience for 32-bit and 64-bit is now identical.

---

### Post by tribaal on 2008-09-08
> The user experience for 32-bit and 64-bit is now identical.

+1

I use only 64bits installs, and I can do absolutely anything just fine. The flash package for 64 bits pulls the 32bits version plus some adapter libraries, you should see absolutely no difference.

- Trib' (x64 fanboy)

---

### Post by starcannon on 2008-09-08
> **Paqman said:**
> +1

Flash and Java *used to* be a problem, and required the use of the 32-bit version of Firefox. That was fixed a couple of versions back, and is no longer an issue. The user experience for 32-bit and 64-bit is now identical.

I'll download it and try it out, wth, I got an extra hdd sitting here collecting digital dustmites anyway.

---

### Post by Efros on 2008-09-08
I have the 64 bit version of 8.04 installed on 3 dual cores and 1 quad core, with memories ranging from 1Gb to 8Gb. If I hadn't installed the systems myself I would barely be aware of the fact that they are 64 bit operating systems, apart from the memory utilization on the hgher end machines when I'm editing large graphics.

---

