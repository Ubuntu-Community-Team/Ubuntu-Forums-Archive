---
title: "how to edit xorg.conf to enable openchrome"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by jack903 on 2013-02-01
Hi All,

This is my display driver.

lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

Very old VIA's K8M800 chip. I am trying to enable "openchrome" as my default display driver for X. When I searched around how to do it, I found [this]("http://ubuntuforums.org/showthread.php?t=1749564") .. 

But the thing I don't understand is where do I find the xorg.conf file. If I have to create it, what values do I fill in?!

I am using Lubuntu 12.10 i386 (LXDE). Please help me out here!

Thanks,
Jack

---

### Post by Locus Kiesselbachi on 2013-02-10
Hello!
Did you follow carefully first two guidelines in [thread link]("http://ubuntuforums.org/showthread.php?t=1749564") you gave?

1.Check if openchrome is installed in your system by using synaptic packet manager
2.Check the xorg.conf file (as I understand, need to be checked also in Synaptic).

Good luck!

---

### Post by sharke on 2013-02-10
> **jack903 said:**
> Hi All,

This is my display driver.

lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

Very old VIA's K8M800 chip. I am trying to enable "openchrome" as my default display driver for X. When I searched around how to do it, I found [this]("http://ubuntuforums.org/showthread.php?t=1749564") .. 

But the thing I don't understand is where do I find the xorg.conf file. If I have to create it, what values do I fill in?!

I am using Lubuntu 12.10 i386 (LXDE). Please help me out here!

Thanks,
Jack

Hello Jack
You can find the config file in /etc/X11/xorg.conf.
do not alter this file unless you know what your doing.
Cheers
Sharke

---

