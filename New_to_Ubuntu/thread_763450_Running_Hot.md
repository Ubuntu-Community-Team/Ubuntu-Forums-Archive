---
title: "Running Hot"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by deez on 2008-04-23
hello...Today some funny things happened with my Ubuntu.  I'm running 7.10.  Where to begin?  

I was trying to alter my trip points so that my fans wouldn't be on all the time. My temp. was 44, but still the fan was on.  I couldn't change the points, but somehow managed to alter the CPU scaling frequency.  I would choose one setting and half a minute later it would revert to maximum power (1.7Ghz).  It didn't work at all.  After some tweaking, I got it to work again, but this time with different values.  Before it was 600Mhz to 1.7Ghz, and now it's 215Mhz to 1.7Ghz.  There's a lot more values, which I guess is a good thing.  Here's my problem...now my laptop (compaq nc4010 Pentium M 1.7 1GB Ram) is running hot.  With the CPU at 215MHz the temperature will not get lower than 52.  This means that the fan is running in 2nd gear as opposed to 1st gear when the temp was 44.  Before, at idle, there was rarely a big discrepancy between M/B temp and CPU temp, but now it's nearly 10 degrees.    

Is there a way to go back to the beginning, aside from a reinstall?  Any ideas how or why the machine is running hotter, even though it's not doing as much?  

Thanks in advance

Deez

---

### Post by antipax on 2008-04-25
Hello, sorry to piggyback on this thread but didn't want to clutter with a new one when I have a similar problem. I installed Hardy Heron (8.04) yesterday and I immediately noticed a HUGE increase of temperature in my laptop (Toshiba Satellite A100-749 1GB RAM, Intel(R) Core(TM)2 CPU T5200 @ 1.60 GHz and graphics card NVIDIA GeForce Go 7300); I have compiz running with Extra visual effects (although not over the top!)

I noticed after a while that the fans were running and the keyboard was getting warmer. When I touched the bottom it was scalding (uncomfortable to keep in my lap).

If you can believe it, as soon as I restarted and booted into Vista Home Premium, the laptop immediately cooled off in a couple of minutes. 

Any explanation? The machine really gets hot.

---

### Post by davidsrsb on 2008-04-25
You need to run top to see if you have a run away process, this has been an issue with Hardy during beta.
8.04 does seem to make a PC work a bit harder though

---

### Post by norman_h on 2008-04-25
The kernel requires manual patching for pentium-m CPUs to take advantage of throttling.

For some reason it hasn't been fully merged into the kernel source.

Older versions of ubuntu had the patches applied, the new 8.04 doesn't appear to have them this time.

I had a similar problem when using gentoo.  I had to manually patch the kernel.

[http://ubuntuforums.org/archive/index.php/t-471634.html](http://ubuntuforums.org/archive/index.php/t-471634.html)
[http://www.thinkwiki.org/wiki/Pentium_M_undervolting_and_underclocking](http://www.thinkwiki.org/wiki/Pentium_M_undervolting_and_underclocking)
[http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU](http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU)
[http://doc.gwos.org/index.php/CPUFreq](http://doc.gwos.org/index.php/CPUFreq)

Time to write a bug report into launchpad...  if only I had time :(

---

### Post by cmnorton on 2008-04-28
> **norman_h said:**
> The kernel requires manual patching for pentium-m CPUs to take advantage of throttling.

For some reason it hasn't been fully merged into the kernel source.

Older versions of ubuntu had the patches applied, the new 8.04 doesn't appear to have them this time.

I had a similar problem when using gentoo.  I had to manually patch the kernel.

[http://ubuntuforums.org/archive/index.php/t-471634.html](http://ubuntuforums.org/archive/index.php/t-471634.html)
[http://www.thinkwiki.org/wiki/Pentium_M_undervolting_and_underclocking](http://www.thinkwiki.org/wiki/Pentium_M_undervolting_and_underclocking)
[http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU](http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU)
[http://doc.gwos.org/index.php/CPUFreq](http://doc.gwos.org/index.php/CPUFreq)

Time to write a bug report into launchpad...  if only I had time :(

I added the information in this post to an existing bug:

[https://bugs.launchpad.net/ubuntu/+bug/210300](https://bugs.launchpad.net/ubuntu/+bug/210300)

---

### Post by antipax on 2008-04-28
sorry, removed.

---

### Post by TimKraemer on 2008-05-01
Same for me.

I updated yesterday from 7.10 to 8.04. While my Laptop (Samsung R50, 1,7 Ghz) has already been quite hot under ubuntu 7.10 (~55C idle), the core temperature reaches now 70C idle and hits 85C easily under load. The situation became unbearable and I decided to reinstall ubuntu from scratch and I opted for XFCE without compiz. The Situation did not change. This Problem does not seem to be related with either the Window Manager or a particular application. Even when I kill the X System, my laptop won't cool down substantially.

---

### Post by TimKraemer on 2008-05-02
I found a solution:

The Problem seemed to be that my ram got incredibly hot, because the kernel was constantly reorganizing the memory and swapping to disk unused data. A quick google-search on "swappiness" gave me the solution: To stop the kernel from constantly optimizing my ram, I had to set the "swappiness" of my laptop from 60 down to 0. Now unused data is only moved to the swap partition if some application needs cache -> less usage of my ram ->  lower temperatur of my ram and of my CPU which sits just next to the ram.

You change it on-the-fly by changing the swappines:

sudo sysctl vm.swappiness=0

If it helps, add the line "vm.swappiness=0" to the end of /etc/sysctl.conf

---

### Post by maximilianhauser on 2008-06-10
I have a similiar Problem. But I think the higher temperature causes the powerstates. 

For more details: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188739](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188739)

---

