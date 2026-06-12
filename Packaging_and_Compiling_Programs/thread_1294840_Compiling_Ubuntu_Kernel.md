---
title: "Compiling Ubuntu Kernel"
date: 2009-10-18
forum: Packaging and Compiling Programs
---

### Post by squid_052 on 2009-10-18
Hi,

I am trying to recompile the kernel for Ubuntu Server.
$ uname -r
2.6.28-11-server

I found the following packages
linux-headers-2.6.28-13 
linux-headers-2.6.28-13-server
linux-source-2.6.28

But I did not find anything called:
linux-source-2.6.28-server

Can anyone please tell me what I need to recompile? Is the reason why I did not find any linux-source for server because its the same for server vs non-server? I was wondering why there was two packages for the headers (one with -server appended), but not the same for the linux-source.

Thanks,
squid

---

### Post by Bachstelze on 2009-10-19
> **squid_052 said:**
> 
Is the reason why I did not find any linux-source for server because its the same for server vs non-server?

Yes, only the compilation options differ. The reason there is two header packages is because the header install location must reflect the exact kernel version.

---

### Post by squid_052 on 2009-10-19
> **Bachstelze said:**
> Yes, only the compilation options differ. The reason there is two header packages is because the header install location must reflect the exact kernel version.
Thanks for the reply.

Just following up, when you mean differ, does the /boot/config-`uname -r` file contain/capture all of these compilation options?

For the second statement about the headers, I'm not sure what you mean exactly. Could you elaborate? For all the instructions that I've read, they all say to use the linux-source package, how do the headers come into play?

Thanks a bunch for the advice

---

### Post by Bachstelze on 2009-10-20
> **squid_052 said:**
> 
Just following up, when you mean differ, does the /boot/config-`uname -r` file contain/capture all of these compilation options?

Yes.

> **squid_052 said:**
> For the second statement about the headers, I'm not sure what you mean exactly. Could you elaborate? For all the instructions that I've read, they all say to use the linux-source package, how do the headers come into play?

The headers are a part of the kernel sources. They are not the entire source tree, but they should be sufficient if you want to build kernel-relate stuff (e.g. modules), but not the kernel itself. So basically,whether you need only the headers or the whole source depends on what you want to build.

---

