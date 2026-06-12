---
title: "How to interpret strange values for steal time in top command on an EC2 instance"
date: 2018-03-08
forum: New to Ubuntu
---

### Post by sriram2105 on 2018-03-08
Hi,


top command and other system utilities provide strange output for idle time , steal time in amazon instances.


When i looked on the internet got to know about this : [https://serverfault.com/questions/888133/steal-time-how-to-interpret-strange-values-for-st-in-top-on-an-ec2-instance](https://serverfault.com/questions/888133/steal-time-how-to-interpret-strange-values-for-st-in-top-on-an-ec2-instance)


Is there any solution for this scenario ? Can any one suggest without upgrading the kernel version how can we get the accurate cpu utilization of the instance ?


Any help would be greatly appreciated.




Thanks,
Sriram

---

### Post by mörgæs on 2018-03-09
Hi, welcome to the fora.

If it's fixed in kernel 4.11 why not upgrade? I'm running 4.13 and everything works fine.

---

