---
title: "[SOLVED] Problem with sl-modem"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by cmas on 2008-05-11
I need help asking this question. I do not know what data to furnish. Please let me know the details I need to include in order for my question to be answered.

I have been running Ubuntu for 2 years now and have had a very smooth time. I am running Hardy (Ubuntu 8.0.4) and linux kernel 2.6.24-17-generic on a T40 laptop. Everything was working fine until one day after a routine upgrade my laptop would no longer boot. It would always get stuck at "Unloading modem driver from kernel ...". I had to press Alt+F1 to open the terminal prompt, log in and then start gdm manually. But obviously there was no internet. 

1. I also did some searching online and found out that I could change the name of the start up script corresponding to the sl-modem driver (change start letter from S to K) in /etc/ rc2.d/ after which  at least my system would start up. 

2. I am now stuck with a system that cannot connect to the internet. I also found out that my USB flash drive is not being recognized (actually nothing happens when I insert it) and that sound does not work. 

3. I also get an error that says "Could not initialize HAL!" when I login. 

4. As an aside, but may be related to this problem, previously my system used to take about a minute to start up and now it takes about 5 minutes to start up. I unfortunately do not have bootchart to post what is going on.

How do I start solving these problems? My guess is that there is something disagreeable in the kernel version. I checked that I do not have any other kernel versions. 

I have some MySQL data and some user data that I would like to salvage. Apart from that I am willing to trash the current install and move on to a fresh install. Given that this is all I need from the system, what are my options? Can I have a fresh install that accesses the system files of the older install? Would a live CD suffice?

Thanks in advance for your time and patience in reading this question!

---

### Post by annda on 2008-05-11
you can access and backup all your data using the liveCD (specifically mysqldump for the databases). i have never tried to downgrade in ubuntu, but theoretically it should be possible to look up older kernels in synaptic and install those to get HAL working, which may solve some of your hardware problems.

---

### Post by cmas on 2008-05-11
Thanks a lot! I will try to download the live CD tomorrow and then update this post.

---

### Post by cmas on 2008-05-13
I managed to salvage my data and get a fresh install of Hardy on my laptop. Thanks!:KS

---

