---
title: "old kernel in ubuntu 12.04"
date: 2013-01-08
forum: New to Ubuntu
---

### Post by rrich1974 on 2013-01-08
i am running ubuntu 12.04 and it works great but i have an issue:
the s-video output is not working sometimes. so, i want to install the kernel from 10.04. (2.6.34) will it be a problem? 
i wouldn't like to destroy my current installation since is is the only one that i have right now. 
thanx!

---

### Post by Pjotr123 on 2013-01-08
That's not a good idea: expect frequent breakage and many unsolvable bugs, when using a kernel that's not a default part of a stable Ubuntu release.

In a sense, the kernel *is* the operating system. The rest is "just" a layer around it. This layer needs to be finely tuned and adjusted to the kernel, otherwise all kinds of things may go horribly wrong.

I suggest you try 12.10.

---

### Post by rrich1974 on 2013-01-08
thanx!
that is what i am afraid of. as i remember, in ubuntu 10.04, the s-video had worked well. but 10.04 had a poor video performance compared to 11.10 or 12.04. 
still, i have got two kernels, 3.4 for precise and 3.6.3 for quantal. 
i will try them later on.

---

### Post by JiuJitsu500 on 2013-01-08
Yeah, I would never, ever roll back a kernel to an older one meant for a previous release. 12.04 will always work well (minus natural bugs... kinda unavoidable) with 3.2 and the variants the ubuntu devs put into it.

It works very well for me with any newer kernel, though on my main machine I stick to the 3.2 versions. You can put in the PPA for the 3.6 kernel, which does work well... but I've *heard* a nasty rumor I kind of like.

As of 12.04.2, the kernel will be upgraded to 3.5 at the end of this month. So, IF this is true, you might have your problem solved in a few weeks... but, if it's not, then 3.2 may not be the best for you and you can experiment with a newer one, never an older kernel though.

An LTS never changes kernel versions though, I have only heard that rumor recently, and really have no idea if it's true so don't take my word for it. I find it very unlikely, but since the 3.4 and 3.6 kernels work very well for me, I guess it's in the realm of possibility. Either way, stck with 3.2 or newer and try other things before messing with the kernel - it's what tells your computer what resources to allocate to what process. Kind of the most important piece of the entire OS, everything else is built totally around it essentially, or at least talks to it directly for permission for things.

I also just realized how little I actually know about how that process works... I still hink CPU's mechanically run off magic.

---

### Post by sandyd on 2013-01-08
You can install alternate kernels for most Ubuntu releases, but first, a few caveats 

1. Be careful - ONLY install kernels for your release.
2. The kernels are avaliable at [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/).
3. If you are using the quantal releases, ONLY download the -quantal releases, and so forth. If you have precise, ONLY download the -precise releases
4. Some of the kernel releases in Mainline may not work properly with your Ubuntu release. In that case, just choose another kernel at the grub startup screen. The kernel releases can possibly not work because they are not patched with the Ubuntu modifications

---

### Post by rrich1974 on 2013-01-09
thanx a lot! 
i see that the latest kernel for precise is 3.4...so, this is only worth to try.

---

