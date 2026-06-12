---
title: "How to set up Ubuntu Server with a RAID"
date: 2021-02-15
forum: New to Ubuntu
---

### Post by rocketman7k on 2021-02-15
Hello,
I am setting up an Ubuntu Server as an FTP file server using VSFTPd. I am using a Raspberry Pi 4 and want to store the files on an external hard drive. I will be using two identical usb hard drives and want them to be mirrored. Can someone please point me in the right direction to set this up properly?

Thanks in advance!

---

### Post by ActionParsnip on 2021-02-15
[https://www.linuxbabe.com/linux-server/linux-software-raid-1-setup/amp](https://www.linuxbabe.com/linux-server/linux-software-raid-1-setup/amp)

---

### Post by DuckHook on 2021-02-15
> **rocketman7k said:**
> Hello,
I am setting up an Ubuntu Server as an FTP file server using VSFTPd. I am using a Raspberry Pi 4 and want to store the files on an external hard drive. I will be using two identical usb hard drives and want them to be mirrored. Can someone please point me in the right direction to set this up properly?

Thanks in advance!

> **ActionParsnip said:**
> [https://www.linuxbabe.com/linux-server/linux-software-raid-1-setup/amp](https://www.linuxbabe.com/linux-server/linux-software-raid-1-setup/amp)
This link is to mdadm which is, shall we say, highly brittle and therefore dangerous when running through the unreliable USB interface, especially when combined with an RPi.

Perhaps we should start by asking OP for the larger picture:

@rocketman7k

[LIST=1]
[*]Why do you want to set up something as insecure as an FTP file server?
[*]What do you hope to achieve with mirroring? What do you think that mirroring is for?
[*]Are you aware of how fragile and untrustworthy your planned setup is?
[/LIST]

---

### Post by MartyBuntu on 2021-02-16
I would look into a RAID-capable external enclosure where you can physically set dip switches to your RAID preference (...assuming you're looking for RAID 1...)
They're not very expensive.

---

### Post by rocketman7k on 2021-02-16
This is very helpful. Do you know of a tutorial that I can use to set up the FTP server?

---

### Post by DuckHook on 2021-02-16
> **rocketman7k said:**
> This is very helpful. Do you know of a tutorial that I can use to set up the FTP server?
There are many and a quick web search returns dozens of good ones. But consider answering my three questions first.

---

