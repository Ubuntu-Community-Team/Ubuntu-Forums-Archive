---
title: "Error after new installation on Mac"
date: 2023-02-19
forum: New to Ubuntu
---

### Post by ehp64 on 2023-02-19
Gave up waiting for root device. Common problems:
  — Boot args (cat /proc/cmdline)
    — Check rootdelay= (did the system wait long enough?)
    — Check root= (did the system wait for the right device?)
  — Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda2 does not exist.   
Dropping to a shell

---

### Post by Impavidus on 2023-02-20
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Don't try the recommended repair yet, just create a summary and show us the link. We need quite a bit more information to handle this.

---

### Post by MAFoElffen on 2023-02-20
I thought I posted to this before I went to bed last night, but don't see it. Hmmm. LOL. No matters.

+1 to Impavidus...

Also what version of Ubuntu did you try to install? What model of MAC? Did it run okay on the LiveCD when "try' was used? And if you ran the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") and posted the URL to where the report uploads to a pastebin, it will other the information on the hardware and settings... (I made sure the script worked on Mac hardware.)

---

