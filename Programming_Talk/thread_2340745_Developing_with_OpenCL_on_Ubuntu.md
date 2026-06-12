---
title: "Developing with OpenCL on Ubuntu"
date: 2016-10-21
forum: Programming Talk
---

### Post by Pietro_Monsurr on 2016-10-21
Last year I installed openCL on Ubuntu 14.04 (I have an AMD A10-7870K CPU and used the AMD OpenCL SDK). It worked.

Now Ubuntu has become incompatible with the proprietary AMD driver fglrx: I have 14.04 (5) and that driver is incompatible with libcheese and other packages, so that apt-get won't install it, and aptitude has corrupted my system when I forced installation*.

Without fglrx, however, I have no idea how to install AMD OpenCL SDK: I installed it, but of course it sees no OpenCL devices.

I need to find a driver to execute openCL code (with g++), and then install AMD OpenCL SDK or something similar (with clFFT, clRAND, clBLAS and as many libraries as possible).

I did my homework and some suggested Oibaf ([https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)), but it is not clear what I'm supposed to install from that repository. A library exists called mesa-opencl-icd but I can't find it on the repository, with or without update to the new repository for Oibaf.

Thank you,
PM

* I've been forced to reinstalled Ubuntu from scratch.

---

### Post by martin30002 on 2016-11-14
Do you have an Intel mainboard with an Intel HD graphic onboard?
Then you might use [https://software.intel.com/en-us/articles/opencl-drivers#latest_linux_driver](https://software.intel.com/en-us/articles/opencl-drivers#latest_linux_driver)
(I know that to have a AMD card, I'm talking about the onboard chip not used for the display)

---

### Post by mar0029 on 2016-11-16
So using the link you provided, you could use OpenCL on the integrated Intel chip but not the discrete AMD?

---

### Post by Pietro_Monsurr on 2016-11-17
I checked my MB. It is an Asus A88XM-PLUS for Ax AMD APUs, and it has no integrated graphics card because the graphics is handled by the APU, which has an on-chip Radeon R7.

So I don't think I can install the Intel drivers, as there is nothing by Intel in my system.

---

