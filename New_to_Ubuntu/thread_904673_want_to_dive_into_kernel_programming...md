---
title: "want to dive into kernel programming.."
date: 2008-08-29
forum: New to Ubuntu
---

### Post by kcode on 2008-08-29
its been a year since i am using Linux. i am fair in programming.
now i want to go into linux kernel programming.
 
1. from where should i start?
2. do i need to know everything about the hardware stuff?
3. what sources to refer?

thanks

---

### Post by Sinkingships7 on 2008-08-29
> **kcode said:**
> its been a year since i am using Linux. i am fair in programming.
now i want to go into linux kernel programming.
 
1. from where should i start?
2. do i need to know everything about the hardware stuff?
3. what sources to refer?

thanks

1. [Go here]("www.kernel.org/"), download the latest kernel source, and spend LOTS of time studying. 

2. It would be essential that you know C, at the very least. Most all of the kernel is written in C. You don't *have* to know much about the hardware itself, but at least know how to interact with the hardware in the C language.

3. The link in answer 1, as well as the [Wikipedia page]("http://en.wikipedia.org/wiki/Kernel_(computer_science)") on the kernel.


This would probably be better off in the [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") section of the forum.

---

### Post by Crafty Kisses on 2008-08-29
The above post was nicely stated, I'd also suggest compile a few kernels on a older machine if you have access to one and just get the feel of the kernels and see how they kind of work, go to [http://kernel.org](http://kernel.org) to look at the source of the kernels and you know just look at them and try to get them down, I'd also suggest you watch the video "Revolution OS" great information in that documentary.

---

### Post by tamoneya on 2008-08-29
The above ideas sound good to me but I would like to suggest a couple other things to try.  These are things which I have been meaning to try myself but I can not personally confirm how effective the method works.  I have seen people recommend looking at some of the source of the original version of the kernel since they are smaller and a little easier to work with and you can get an understanding of how things are laid out.  Obviously things will be restructured if you compare 0.01 to 2.6.27 but many of the underlying ideas will be the same.
[ftp://ftp.kernel.org/pub/linux/kernel/Historic/linux-0.01.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/Historic/linux-0.01.tar.gz)

Also here is a nice link I found that lays out the kernel:
[http://www.makelinux.net/kernel_map](http://www.makelinux.net/kernel_map)

---

### Post by kcode on 2008-08-31
sinkingships7:

can you please refer a source for understanding the interaction 
with hardware devices using c language.

thanks

---

