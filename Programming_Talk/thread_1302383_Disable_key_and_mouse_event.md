---
title: "Disable key and mouse event"
date: 2009-10-27
forum: Programming Talk
---

### Post by phillip_linux on 2009-10-27
Hi All
I'm newbie to Linux. I have a doubt. in my programming i need to lock a remote system. is there any system call to disable the keyboard and mouse of remotely taken system.
Ur kind help will be appreciated.
Warm regards,
Phiilip

---

### Post by Zugzwang on 2009-10-27
I'm by no means sure why you want to so this.

As you are a newbie, I'd like to mention that Linux has a huge number of components and depending on the context of your question, there are different ways to accomplish what you ask for. In fact, I would try to avoid what you are doing and just lock the X-server screen of the local user of that machine out and prevent her from logging in again by changing the password or so. This would allow local administrative access which might be useful for example when the network failed and you cannot open a remote connection anymore.

Anyway, you might also want to consider (if possible, I don't really know, please google it up) unloading the linux kernel modules responsible for keyboard and mouse access. You will need to make sure that they are actually compiled into the kernel as custom modules. In this case, you will need root access.

---

### Post by phillip_linux on 2009-10-27
> **Zugzwang said:**
> I'm by no means sure why you want to so this.

As you are a newbie, I'd like to mention that Linux has a huge number of components and depending on the context of your question, there are different ways to accomplish what you ask for. In fact, I would try to avoid what you are doing and just lock the X-server screen of the local user of that machine out and prevent her from logging in again by changing the password or so. This would allow local administrative access which might be useful for example when the network failed and you cannot open a remote connection anymore.

Anyway, you might also want to consider (if possible, I don't really know, please google it up) unloading the linux kernel modules responsible for keyboard and mouse access. You will need to make sure that they are actually compiled into the kernel as custom modules. In this case, you will need root access.

Thank you very much for reply.

I'm writing an application, to connect 2 system. one will be working as master and another as client. I wanna disable the client stsyem's keyboard and mouse from master pc . Is there any way in ubuntu to do so. I mean ny system call? i could not found much on net.

---

### Post by Zugzwang on 2009-10-27
In Linux, you often don't do system calls directly to achieve such effects unless you are writing a kernel driver or something like that. Rather, you use a plethora of command line programs that do such tasks for you. An example is the "rmmod psmod" command which will remove PS/2 mouse support at runtime (and probably more, I don't actually know). Additionally, there's the virtual filesystem "/proc" where some virtual files reside into which you can write for controlling behaviour of the system. This "system call" idea is very windowsish.

BTW, why don't you just start a VNC server on the second computer or allow remote logins? That appears to be far simpler. VNC sessions can also be shared between users, it desired.

---

