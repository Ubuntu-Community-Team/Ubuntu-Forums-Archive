---
title: "Unablet to Update Ubuntu Server 11.10 installed in VMware server 2.02"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by rebeller on 2012-04-08
Hi,

I am a newbie here. I have installed Ubuntu Server 11.10(oneiric ocelot) 32-bit in the VMWare server 2.02 on my home desktop(Windows 7 professional 64-bit). After running the setup I ran "sudo aptitude update && sudo aptitude dist-upgrade" and got an error message(attached screenshot).Also I have attached(screenshot) of my sources.list. (sorry don't know how to copy the text from the ubuntu server to my windows desktop.)
I would really appreciate any help on this.

Thanks,

Sam

---

### Post by lechien73 on 2012-04-08
Hi & welcome to the forums,

This error could indicate a network error. Can you ping the us.archive.ubuntu.com server from the Ubuntu VM?

```
ping us.archive.ubuntu.com
```

If not, then try pinging archive.ubuntu.com instead. If that works, then change the references to us.archive.ubuntu.com to archive.ubuntu.com in your /etc/apt/sources.list file.

Save the file, then type:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by rebeller on 2012-04-09
> **lechien73 said:**
> Hi & welcome to the forums,

This error could indicate a network error. Can you ping the us.archive.ubuntu.com server from the Ubuntu VM?

```
ping us.archive.ubuntu.com
```

If not, then try pinging archive.ubuntu.com instead. If that works, then change the references to us.archive.ubuntu.com to archive.ubuntu.com in your /etc/apt/sources.list file.

Save the file, then type:

```
sudo apt-get update && sudo apt-get upgrade
```

Thanks Matt! I was able to ping both us.archive.ubuntu.com and archive.ubuntu.com from the ubuntu vm.

---

