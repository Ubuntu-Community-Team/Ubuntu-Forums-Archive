---
title: "Windows 8 hardware control??"
date: 2012-10-13
forum: Recurring Discussions
---

### Post by alan tam on 2012-10-13
I read an article about the upcoming windows 8, this is frightening. 
According to the article, all future computer hardware manufacturers are required to comply to rules set by Microsoft(MS) if they would make hardware for W8 compatible. The same goes to other OS as well. Anyone wish to boot up a new computer designed for W8 would have to pay MS certification fees in order for their OS to boot. Fedora is going to pay MS USD99 for their users to boot up the computers.
No OS other then W8 will allow to boot if they fail to get MS certified or pay license fees for approval, this including Ubuntu. Is it true?
What is the countermeasures Ubuntu have to deal with such actions from MS?
Do we need to pay MS? If this is true, I do not see the future for Ubuntu or the linux communities in general.

---

### Post by coffeecat on 2012-10-13
Not true. Microsoft [requires the ability to disable secure boot](http://download.microsoft.com/download/A/D/F/ADF5BEDE-C0FB-4CC0-A3E1-B38093F50BA1/windows8-hardware-cert-requirements-system.pdf) via firmware setup on non-ARM systems (page 121, #18).

This has been discussed many times before here.

*Thread moved to **Recurring Discussions**.*

---

### Post by KiwiNZ on 2012-10-13
You should read this

[http://www.linuxfoundation.org/news-media/blogs/browse/2012/10/linux-foundation-uefi-secure-boot-system-open-source](http://www.linuxfoundation.org/news-media/blogs/browse/2012/10/linux-foundation-uefi-secure-boot-system-open-source)

---

### Post by grahammechanical on 2012-10-13
That linuxfoundation.org post has a link to this Ubuntu statement, which has now been changed.

[https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035445.html]("https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035445.html")

to this

[http://www.omgubuntu.co.uk/2012/09/ubuntu-to-use-signed-grub2-bootloader-for-secure-boot]("http://www.omgubuntu.co.uk/2012/09/ubuntu-to-use-signed-grub2-bootloader-for-secure-boot")

Indeed Grub 2.0 is now present in 12.10 instead of Grub 1.99

Regards.

---

