---
title: "Problem burning iso CD with Nautilus"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by panorack on 2008-05-02
I have downloaded the iso for Ubuntu 8.04 with a view to doing a complete install but I cannot get Nautilus to burn the CD. 

The help page from Ubuntu Home site advises to set the write speed as low as possible and the error message I get when attempting to burn the CD also advises trying a lower write speed. 

However, the 'write speed' box is greyed out and I cannot find any way of editing the settings. Can anyone help me in this? :(

Many thanks in anticipation,:)

Panorack

---

### Post by wolfen69 on 2008-05-02
download K3B and try that. much better for burning.
```
sudo apt-get install k3b
```

---

### Post by panorack on 2008-05-02
Thanks for the tip. Installed K3b and it looks more promising but still failed with the following error message:

System
-----------------------
K3b Version: 1.0.3

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
/usr/bin/wodim: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.

It was the last line that got me. Any ideas what is wrong?

Panorack

---

### Post by jonaphant on 2008-05-02
install gnomebaker
i had the same problem and after installing it i could burn an image with the lowest speed (4x) and it worked perfect:)

EDIT:look for it at synaptic

---

### Post by Biggy on 2008-05-02
install Brasero

---

### Post by jonaphant on 2008-05-02
> **Biggy said:**
> install Brasero

yeah that's a good idea too

---

