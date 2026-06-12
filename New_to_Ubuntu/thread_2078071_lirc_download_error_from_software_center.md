---
title: "lirc download error from software center"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by Old Jimma on 2012-10-30
Hi Community:

I'm struggling to install infared to help MythTV work.

I'm running 12.04.1.

I went to the software center to install lirc and got the message:

CD/DVD 'Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)' is required

Please insert the above CD/DVD into the drive '/media/cdrom/' to install software packages from it.

What should I do now?

Old Jimma from the dreary Old Country

---

### Post by newb85 on 2012-10-30
Please provide the output of

```
cat /etc/apt/sources.list
```

---

### Post by jerrrys on 2012-10-30
Uncheck CDrom

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by Old Jimma on 2012-11-01
Hi Jerrys:

All of the checkboxes are checked. However, I upgraded to Precise using the automatic upgrade path... I didn't use a CD.

I'll burn an ISO of 12.04.1, put it in the reader, and try again.

Thanks!
Old Jimma

---

### Post by newb85 on 2012-11-01
If you have a good internet connection, there's really no need to use a CD as your source.  Just make sure you have the CD source *un-checked*.

---

### Post by Old Jimma on 2013-02-08
I uncheck "CD" on synaptic and it worked!

---

