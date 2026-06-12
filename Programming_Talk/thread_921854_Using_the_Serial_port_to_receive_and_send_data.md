---
title: "Using the Serial port to receive and send data"
date: 2008-09-16
forum: Programming Talk
---

### Post by grüner pfirsich on 2008-09-16
Hi,

Im working on a project which needs to send and receive data using the serial port. 

I have found a helpful code and it works. To check the communication, I've been using my HP calcuator and it works but only in one side.. I mean I can send data HP calculator->Laptop but not Laptop-Hp calculator.

The code I use is this one

res=read(fd,buf,255);
buf[res]=0;
printf(":%s:%d", buf, res);


There is only read() and that is (I think) the reason it works one side.. but If Im wrong please let me know.


Thanx a lot

---

### Post by dribeas on 2008-09-16
> **grüner pfirsich said:**
> 
The code I use is this one

res=read(fd,buf,255);
buf[res]=0;
printf(":%s:%d", buf, res);


There is only read() and that is (I think) the reason it works one side.. but If Im wrong please let me know.

write is used to write/send data to the port. Read the manpages.

---

### Post by grüner pfirsich on 2008-09-16
thanx

Im total beginner and I had no idea about the manpages

---

