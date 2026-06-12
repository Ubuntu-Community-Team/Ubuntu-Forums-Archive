---
title: "QtSerialPort and QtSerialPortInfo"
date: 2017-12-10
forum: Programming Talk
---

### Post by vidar-vidnes on 2017-12-10
NOTE: Thread header should have been "QtSerialPort and QtSerialPort**Info**" dont know what happend there


Hi

Qt Serial Port is said to be officially part of Qt but I cant find it on my system, xubuntu 17.04. when install qt5-default i get info that 5.7.1 in installed already, so serialport support should really be there.

Do I have to build it from scratch as before in the ol days?

---

### Post by norobro on 2017-12-10
Hello.

The library: [https://packages.ubuntu.com/zesty/libqt5serialport5](https://packages.ubuntu.com/zesty/libqt5serialport5)
The library and headers: [https://packages.ubuntu.com/zesty/libqt5serialport5-dev](https://packages.ubuntu.com/zesty/libqt5serialport5-dev)

Edit: added the non-dev package.

---

### Post by vidar-vidnes on 2017-12-11
Thanks, it seems that it was the headers I was missing.

Thanks a lot

---

