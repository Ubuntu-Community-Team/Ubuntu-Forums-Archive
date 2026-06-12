---
title: "Programming with Linux for Mac OS platform"
date: 2011-09-23
forum: Programming Talk
---

### Post by puzzleryu on 2011-09-23
Hi All,
I'm new on this forum, and I really hope that you can help me.

I have a question about how programming for Mac OS using Linux as developing platform. In particular, I need to write some C/C++ components that have to use digital acquiring devices such as cameras, scanners, and so on. I have to do this for Mac OS platform, but since I don't have a Mac, I wonder if there is a possibility to use Linux as developing platform and, more in particular, I have to know if, once programmed such devices with C/C++ on Linux, it will run safely on Mac OS.

I hope I had been clear on my explanation.

---

### Post by slavik on 2011-09-23
> **puzzleryu said:**
> Hi All,
I'm new on this forum, and I really hope that you can help me.

I have a question about how programming for Mac OS using Linux as developing platform. In particular, I need to write some C/C++ components that have to use digital acquiring devices such as cameras, scanners, and so on. I have to do this for Mac OS platform, but since I don't have a Mac, I wonder if there is a possibility to use Linux as developing platform and, more in particular, I have to know if, once programmed such devices with C/C++ on Linux, it will run safely on Mac OS.

I hope I had been clear on my explanation.
Won't work. It's like writing the same software but for Windows. OSX is a different OS, no matter how similar in methodology it is. You won't know how something runs on OSX until you run it on OSX.

---

### Post by puzzleryu on 2011-09-23
Thank you for your response.

I understand, so I need to buy a Mac and then start to develop directly to it, isn't it?
If so, which compiler I need for developing on it and, more in particular, which library should I use in order to use image acquisition? I heard something about XCode as editor and compiler, but I don't know if it fit my needs (I'm new to Mac developing).

---

### Post by akand074 on 2011-09-23
> **puzzleryu said:**
> Thank you for your response.

I understand, so I need to buy a Mac and then start to develop directly to it, isn't it?
If so, which compiler I need for developing on it and, more in particular, which library should I use in order to use image acquisition? I heard something about XCode as editor and compiler, but I don't know if it fit my needs (I'm new to Mac developing).

It used to be illegal to code for a Mac unless you're on a Mac (because you weren't allowed to virtualize Mac). Though I hear Apple now allows you to virtualize Lion. So, an alternative (if only temporary) is to install Lion in a virtual machine to test your application.

---

### Post by conundrumx on 2011-09-23
> **akand074 said:**
> It used to be illegal to code for a Mac unless you're on a Mac (because you weren't allowed to virtualize Mac). Though I hear Apple now allows you to virtualize Lion. So, an alternative (if only temporary) is to install Lion in a virtual machine to test your application.

Apple started allowing virtualization of the server OS a few versions back, and the restriction that has carried over is the host machine must be a Mac.  

As for the OP's questions, you'll want to get familiar with XCode.  You could write the code elsewhere, but you're going to end up wanting to use at least some functions of Xcode.  Buy a Mac, get Xcode (which is free as in beer).

---

### Post by akand074 on 2011-09-23
> **conundrumx said:**
> Apple started allowing virtualization of the server OS a few versions back, and the restriction that has carried over is the host machine must be a Mac.

Thank you for clarifying!

---

### Post by puzzleryu on 2011-09-24
Thank you all for the explanations. Anyway, since I understand that I can't develop for Mac in any case unless I have a Mac, I think my thread starts to be off-topic, so I have to ask to the relative thread in other sites.

---

