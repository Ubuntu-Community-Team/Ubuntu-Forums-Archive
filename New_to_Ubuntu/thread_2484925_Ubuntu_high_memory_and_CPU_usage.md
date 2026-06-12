---
title: "Ubuntu high memory and CPU usage"
date: 2023-03-14
forum: New to Ubuntu
---

### Post by sherlock01 on 2023-03-14
Hey everybody. I am already doing pentesting for firms.
My laptop is 8gb ram, 256 ssd, 3GHZ new huawei d15. So i wanted to know exactly I have so much CPU( 80-90%) even on Windows and Memory usage (50-60) while on activity with ubuntu with pentesting tools. 
I am using Ubuntu through VirtualBo.. While installing i made, Memory Base 4096 MB , Processors 3 of 4 and Video Memory is 128(max). My question is how to use ubuntu on Virtual machine with perfect settings or Using ubuntu with live usb ?
Anyone tell me if i am setting upped ubuntu storage wrong

---

### Post by TheFu on 2023-03-14
Old, but still valid: [https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)

---

### Post by sherlock01 on 2023-03-14
url not valid

---

### Post by TheFu on 2023-03-14
> **sherlock01 said:**
> url not valid

I don't know what to say. It works here and there are others visiting without issues according to the logs. You could use google's cache or the waybackmachine to view it if your subnet had some attackers and got blocked.

---

### Post by Autodave on 2023-03-14
URL works here.

---

### Post by ActionParsnip on 2023-03-14
Why 128Mb video RAM?

---

### Post by TheFu on 2023-03-14
> **ActionParsnip said:**
> Why 128Mb video RAM?

To support 2D and 3D virtualGPU. For a desktop, this is common.
For a server, 9MB is the default and shouldn't be touched.

---

