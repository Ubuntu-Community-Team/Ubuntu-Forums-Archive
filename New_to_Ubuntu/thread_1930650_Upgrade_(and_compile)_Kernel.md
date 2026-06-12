---
title: "Upgrade (and compile?) Kernel"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by AOlives on 2012-02-24
Running stock Ubuntu 11.10, fully updated. Kernel 3.0.0-16-generic-pae
I would like to upgrade to kernel 3.2.5.
If what I have found googling is correct, I have to compile 3.2.5 myself.
I have tried this multiple times following many different "how to's" and tutorials online, but have continued to fail at it.
The closest I have gotten was through following the instructions found here: [http://vanilja.org/kernel/](http://vanilja.org/kernel/)
However afterwards I cannot boot.

Can someone please tell me what I am doing wrong?
Maybe step me through it?

---

### Post by mastablasta on 2012-02-24
> **AOlives said:**
> I would like to upgrade to kernel 3.2.5.

 
 
Why?
 
and if you are a beginner then be prepared to do some reading unless there is a PPA for 3.2.5 kernel.
 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.5-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.5-precise/)
 
download and 
 
sudo dpkg -i *.deb

---

### Post by HeroOfCanton on 2012-02-24
Unlike some versions of linux it really isn't recommended (or generally necessary) to compile your own kernel on ubuntu. Is there a reason you need to do this?

---

### Post by Paqman on 2012-02-24
> **AOlives said:**
> 
I would like to upgrade to kernel 3.2.5.


That's a pretty new kernel, even the next version of Ubuntu isn't shipping with that. That kernel (or a later one) would probably land in the version that comes out in October. Unless you've got a serious hardware problem that you know is fixed in that version I would just sit back, relax and let it come to you in a few months.

---

### Post by AOlives on 2012-02-25
I was looking into it more to get acquainted with the process. I would eventually like to run MOSIX on a very simple cluster.
Though I realize I have a long way to go.

---

### Post by andrew.46 on 2012-02-25
> **AOlives said:**
> I would like to upgrade to kernel 3.2.5.

I am a little curious at this choice of kernels, as 3.2.7 is out now?

---

### Post by kevdog on 2012-02-25
Compiling a kernel is really fun, however it does take many times to get it just right.  The reason for this is because there are so many options you can chose to compile into the kernel.  You really have to know your hardware.

---

### Post by JosephC on 2012-05-25
Sorry to bump this, but 3.2.5 is supposed to come with the power regression fix (one small patch) that will be absolutely necessary to many people. Therefore,the question is whether the LTS kernel will have this patch at some point or if it already does, as the patch has been around much longer than its implementation in mainline 3.2.5. in the Fedora universe.

For this reason, perhaps, there was inquiry as to the availability of 3.2.5 in 12.04.

---

