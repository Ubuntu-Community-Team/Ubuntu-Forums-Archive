---
title: "Shrinking boot partition."
date: 2016-01-27
forum: New to Ubuntu
---

### Post by matthewmate on 2016-01-27
Hello, im using Ubuntu 15.10 and.. my main boot partition is 1.81 TB size. and i've got around 1.6TB unused. I want to shrink it into 500gb because rest of my hard drive i want to use for getting windows 10 to play games. (don't want to lose any data atm...)

Anyone can help?
Im really new to Linux.

---

### Post by grahammechanical on 2016-01-27
A general principle. Use Windows utilities to resize/move Windows  partitions and use Linux utilities to resize/move Linux partitions.

In Ubuntu we use a utility called GParted from a Ubuntu live session. Instructions how to use GParted are here.

[URL="https://help.ubuntu.com/community/HowtoPartition"]https://help.ubuntu.com/community/HowtoPartition

[/URL]We  cannot work on Linux partitions that are mounted/active. That is why we  use a live session. The partitioner (GParted) will show a list of  partitions. Any partitions with a key icon against it will still be  mounted and cannot be resized.

Regards.

---

### Post by oldfred on 2016-01-27
Be sure to back all your /home and/or data, list of installed applications, and perhaps some system wide configurations, if you manually edited config files.

Is Ubuntu installed in BIOS or UEFI boot mode? 
You want to be sure to install Windows in same boot mode as Ubuntu. And how you boot install media is how it then installs for both Ubuntu & Windows.

Windows only boots in UEFI mode from gpt partitioned drives. Boot flag is only on ESP -  efi system partition.
Windows only boots in BIOS mode from MBR(msdos) partitioned drives, and must boot from a primary NTFS partition with the boot flag.

---

