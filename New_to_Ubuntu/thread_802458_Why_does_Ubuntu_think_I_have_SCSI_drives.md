---
title: "Why does Ubuntu think I have SCSI drives?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by brijam on 2008-05-21
On two different boxes (a Thinkpad T41 and a Dell PowerEdge 400SC), my hdd is installed as /dev/sda1 and listed as SCSI.  In both cases it's plain old IDE.

Does this matter at all, or is it indicative of some deep Ubuntu issue or anything?

---

### Post by rbc on 2008-05-21
Can't answer your question about "Why?" but I've tried at least a dozen different Linux distros on many different computers. Sometimes the IDEs are seen as such, sometimes they are seen as SCSI. I have never had it cause a single problem, as long as I knew which way it was being recognized

---

### Post by MaindotC on 2008-05-21
It doesn't really matter.  I use 7.10 on a T60 and it identifies the sata drives as scsi (which in a sense they are) but I've never had any problems.

---

### Post by mcduck on 2008-05-21
That's absolutely normal. Some time ago developers discovered that the SATA/SCSI driver handled IDE drives better than the actual IDE driver did.. So now the same drivers are used for all IDE, SATA and SCSI disks.

---

### Post by brijam on 2008-05-21
Thanks!

---

### Post by MaindotC on 2008-05-21
You can thank people by clicking the stars ^_^

---

### Post by brijam on 2008-05-21
I'm wondering about this.

```
brian@400sc:~$ sudo hdparm /dev/sda

/dev/sda
 IO_support    =  0 (default)
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     =  256 (on)
 geometry      =  4863/255/63, sectors = 78125000, start = 0
```

Am I mixing up two separate issues?

---

