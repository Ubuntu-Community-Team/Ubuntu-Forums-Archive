---
title: "Automount internal hard drive partition on boot up (Hardy)"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by shuttleworthwannabe on 2008-06-01
Hi There

I noticed the hardy does not automount my partitions at bootime. is there an GUI application I can use to check/uncheck if ubuntu could automount/not automount partitions at boot up? as an alternative to placing line in fstab?

If not ,then what do I out in fstab to force my data drive to be automounted at boot time?
it is currently mounted here: /media/MYDATA

any suggestions?
S

---

### Post by sayakb on 2008-06-01
```
sudo apt-get install mountapp
```

You can also use gparted to mount/unmount volumes.
```
sudo apt-get install gparted
```
Then goto System->Administration->Partition Editor

---

### Post by shuttleworthwannabe on 2008-06-02
Many thanks. Will try them both.
S

---

### Post by victorgreen on 2009-02-06
I just used the program mountmanager (run it from root from terminal) to mess with all things having to do with mounting my several M$ partitions on my main internal drive. (64bit Intrepid)

---

