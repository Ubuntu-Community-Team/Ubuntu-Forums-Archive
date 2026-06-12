---
title: "PF_ring testing fail"
date: 2023-10-15
forum: New to Ubuntu
---

### Post by ahmex03 on 2023-10-15
I am trying to install PF_Ring on my Ubuntu 22.04. I downloaded the  sources and followed steps in read me file. All steps are successful went successful but  when I try to test PF_Ring with following command, I am getting error. 

[B]# sudo su
# insmod ./kernel/pf_ring.ko

insmod: ERROR: could not load module ./kernel/pf_ring.ko: No such file or directory[/B]

But **#ls -a **shows that there is a file with name **pf_ring.ko** in current directory. 

Can someone guide me how to fix that.

---

