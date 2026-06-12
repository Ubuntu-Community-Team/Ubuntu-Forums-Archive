---
title: "How to distinguish between a generic kernel and low latency kernel in linux pub"
date: 2016-01-04
forum: New to Ubuntu
---

### Post by latha2 on 2016-01-04
Dear all, 
I'm new to ubuntu and doing a project on patching a kernel with rt kernel and before that I'm not able to get how to distinguish whether the kernel is the low latency kernelor not  from linux kernel pub ..
Please help me out 
Thank you.

---

### Post by grahammechanical on 2016-01-04
This is not really a new to Linux/Ubuntu subject. Is it? 

I do not think that you can distinguish between a stable kernel and an rt kernel at kernel.org because kernel.org does not provide rt kernels. We take a stable kernel and then patch it to create an rt or low latency or pre-empt kernel. In other words we build it ourselves.

This is how rc kernels come about. But in the case of rc kernels in Ubuntu they are built by the Ubuntu kernel team on a Ubuntu branch of the stable Linux kernel. I do not think that the Ubuntu kernel team builds rt kernel for us.

[http://www.alsa-project.org/main/index.php/Low_latency_howto](http://www.alsa-project.org/main/index.php/Low_latency_howto)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

[https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel](https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel)

Regards.

---

### Post by latha2 on 2016-01-05
thank you

---

