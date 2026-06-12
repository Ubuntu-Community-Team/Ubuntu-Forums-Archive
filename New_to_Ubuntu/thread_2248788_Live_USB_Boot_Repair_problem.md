---
title: "Live USB Boot Repair problem"
date: 2014-10-17
forum: New to Ubuntu
---

### Post by yegor2 on 2014-10-17
Howdy!

I'm trying to recover my Ubuntu boot using a live USB in "try Ubuntu" mode.
However, the recommended repair doesn't fix my problem, so I've been directed to this page to ask for an advice before continuing with an advanced repair.

Here is my BootInfo: [http://paste.ubuntu.com/8578219/](http://paste.ubuntu.com/8578219/) 

Thank you in advance.

---

### Post by davit2 on 2014-10-17
Hi, try it
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by stalkingwolf on 2014-10-17
+1

---

### Post by oldfred on 2014-10-17
You are showing RAID on sda & sdc, but sdb is now gpt partitioned. Was it part of your RAID before?
I do not know RAID so cannot help on RAID fixes.

You also have lots of kernels installed. You do need to do maintenance and uninstall kernels on a regular basis. I prefer to keep 2, let it grow to 3 or 4 and then houseclean back to two.

---

