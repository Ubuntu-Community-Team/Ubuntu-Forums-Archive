---
title: "Reducing CPU speed for developing for old machines"
date: 2010-06-25
forum: Programming Talk
---

### Post by outofsync on 2010-06-25
Hi!

I know all of us always want to get the best performance as possible in our systems, but I sometimes write code which will be used in older computers, and I'd like my machine to slow down when testing such code, so that I get an approximate "feeling" of how the user will feel the application.

Is there some way for reducing the speed of Linux in a safe way? (btw, I know there're settings like that for energy saving in laptops, but I feel that's not I want... I wish more control: I'd like to tune the speed until for example the performance of povray is similar to the target machine).

Thanks!

---

### Post by cgroza on 2010-06-25
You could run some heavy duty app in background to slow it down.

---

### Post by nitstorm on 2010-06-25
Have you tried using a Virtual Machine like VirtualBox? It should be available in the Software Centre.

---

### Post by juancarlospaco on 2010-06-25
*"Reducing CPU speed for developing"* ---> I have no Windows developing experience, sorry 

[CPUBurn]("apt:/cpuburn")
:D

---

### Post by StephenF on 2010-06-25
There's a program called stress that may be able to help.

---

### Post by DanielWaterworth on 2010-06-25
sudo cpufreq-set -g powersave

Will turn the cpu down to the lowest frequency it supports.

---

### Post by Hellkeepa on 2010-06-28
HELLo!

You might take a look into the DOSbox source, as they have some functionality that allows you to simulate the CPU speed of older processors.

Happy codin'!

---

### Post by Zugzwang on 2010-06-28
> **Hellkeepa said:**
> 
You might take a look into the DOSbox source, as they have some functionality that allows you to simulate the CPU speed of older processors.


For completeness, I must add that this advice is unfortunately not helpful. Dosbox is an emulator and as such the programmers have been able to use totally different techniques which are not applicable to the task of slowing down Linux programs.

---

### Post by Hellkeepa on 2010-06-28
HELLo!

Ah, ok. Thanks for the notice, too bad my advice wasn't useful. Thought the OP might be able to use their ideas, to create his own CPU-slower code. (Never looked at their source, btw.)
Oh well, live and learn. :-) Good luck on your project, **outofsync**!

Happy codin'!

---

### Post by lukeiamyourfather on 2010-06-28
This is not a very good practice. Clock speed isn't the only difference between newer and older computers. Best thing to do is get an older machine and test with it. Here's just one example.

[http://cgi.ebay.com/Dell-Optiplex-GX110-Tower-P3-667-Mhz-512-MB-40-GB-/370401278657?cmd=ViewItem&pt=Desktop_PCs&hash=item563da2fac1#ht_2016wt_1137](http://cgi.ebay.com/Dell-Optiplex-GX110-Tower-P3-667-Mhz-512-MB-40-GB-/370401278657?cmd=ViewItem&pt=Desktop_PCs&hash=item563da2fac1#ht_2016wt_1137)

There are literally millions of old computers floating around that can be had for very little or nothing at all. That will be the true test of the application since all factors will be accounted for. Cheers!

---

