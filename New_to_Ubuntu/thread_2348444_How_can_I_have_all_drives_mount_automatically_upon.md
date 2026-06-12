---
title: "How can I have all drives mount automatically upon boot-up?"
date: 2017-01-03
forum: New to Ubuntu
---

### Post by steve169 on 2017-01-03
I'm running Ubuntu 16.04.1.

I have several drives: partitions on two hard drives, one solid-state drive and a flash drive.

These drives are not mounted until I call them up in file manager.

Is there a way to automatically mount all drives while booting up?

---

### Post by Autodave on 2017-01-03
There used to be a program named *disks *that will allow you (simply) to have them mount at boot up.

---

### Post by SeijiSensei on 2017-01-03
Add them to /etc/fstab.   Read this: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Impavidus on 2017-01-04
> **SeijiSensei said:**
> Add them to /etc/fstab.   Read this: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

+1

Note that the things you want to mount are the partitions, which exist on drives but are quite distinct. Of course, Windows has gone through great efforts to make people who are new to Ubuntu confused.

---

### Post by steve169 on 2017-01-04
Got it. Many thanks to all of you.

---

