---
title: "Installing huawei e173 modem"
date: 2011-12-27
forum: New to Ubuntu
---

### Post by lamzaks on 2011-12-27
Hello,
I have problem with mobile modem.. I wan`t to add huawei e173 modem to send SMS from web application.

I can not install using 
> 
root@serv:/var# lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 013: ID 12d1:1436 Huawei Technologies Co., Ltd.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

> 
modprobe usbserial vendor=0x12d1 product=0X1436

when I had huawei E220 then is solved this problem with that string

---

### Post by wolfen69 on 2011-12-27
In the third last post in [this]("http://frontlinesms.ning.com/forum/topics/ubuntu-linux-driver-for-huawei") thread, Domingo Liotta offers an answer.

---

### Post by lamzaks on 2011-12-28
nop... still no effect... The linux is on terminal only...

Any other ideas?

---

### Post by cepraksanta on 2012-05-10
Try using wine...

---

