---
title: "Minimal installation...with a difference."
date: 2008-08-25
forum: New to Ubuntu
---

### Post by ProgramErgoSum on 2008-08-25
Hi,
[LIST=1]
[*]How do I do an installation of Linux where the "computer" is only a CPU ?
[*]Alternatively, is it possible to check/un-check options so as to install only those components which is desired ?
[/LIST]

Suppose I want to host a web server. Then, ideally, this server can be monitored and deployed onto remotely (FTP, ssh, etc). In other words, there isn't really a requirement for a keyboard, mouse, USB, CD/DVD drives, audio/video, etc. Just enough OS to run/support a network and run/support a web server.

---

### Post by kpkeerthi on 2008-08-25
This is your best bet: [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

Most server distributions like Ubuntu Server, Debian Server come with just the components required for a server. The installation wizard lets you choose the components you require.

---

### Post by tangibleorange on 2008-08-25
> **ProgramErgoSum said:**
> Hi,
[LIST=1]
[*]How do I do an installation of Linux where the "computer" is only a CPU ?
[*]Alternatively, is it possible to check/un-check options so as to install only those components which is desired ?
[/LIST]

Suppose I want to host a web server. Then, ideally, this server can be monitored and deployed onto remotely (FTP, ssh, etc). In other words, there isn't really a requirement for a keyboard, mouse, USB, CD/DVD drives, audio/video, etc. Just enough OS to run/support a network and run/support a web server.

I think you're referring to a command-line system install. there is an option to do this on the alternate CD - press F4 at the startup screen and select "Install a Command Line System". this will install only the very basics to get your computer running, and from there you can proceed to install packages.

alternatively, the server install CD has many options for selecting the best packages for that server's purpose. for example, you might want a samba server, and so the server CD will install all packages necessary for a samba server.

---

### Post by eggdeng on 2008-08-25
```
where the "computer" is only a CPU
```
You will at least need some memory and, unless you plan to run everything from a live CD, a hard drive. If you just want a headless server with no GUI & no peripherals, the LTS Server Edition will suit your purposes.
[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

---

### Post by ProgramErgoSum on 2008-08-25
kpkeerthi,
LTS sounds a good option as I can learn about building too.

tangibleorange,
Does Ubuntu/Canonical ship the alternate CD as well ? Yes, I am interested in the command line version only.

eggdeng,
Let me check out the LTS Server edition.

Thanks all !

---

