---
title: "this probably happened because there are too many primary partitions in the partition"
date: 2015-09-17
forum: New to Ubuntu
---

### Post by kushal5 on 2015-09-17
Hi.

I am new to ubuntu. Upon installation ubuntu i am getting error message "this probably happened because there are too many primary partitions in the partition table".
I am not sure how to deal with it.

I am trying to install ubuntu 15.01 for desktop. I have pre installed OS - Windows 7.

Can you please help me out in resolving this isssue.

---

### Post by v3.xx on 2015-09-17
You can have only four primary partitions.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=4+four+primary+partitions&as_qdr=all&sa=Google+Search&lang=en&siteurl=](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=4+four+primary+partitions&as_qdr=all&sa=Google+Search&lang=en&siteurl=)

---

### Post by yancek on 2015-09-17
Boot the Ubuntu installation medium and open a terminal then run this command:  sudo fdisk -l(Lower Case Letter L in the command).  Post the output here as it will give some specific information on your drives/partitions and someone should be able to give you a specific suggestion on what to do.

---

### Post by kushal5 on 2015-09-17
> **v3.xx said:**
> You can have only four primary partitions.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=4+four+primary+partitions&as_qdr=all&sa=Google+Search&lang=en&siteurl=](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=4+four+primary+partitions&as_qdr=all&sa=Google+Search&lang=en&siteurl=)


But I have only 3 primary partitions.

---

### Post by kushal5 on 2015-09-17
I don't know how to open terminal without installing ubuntu. I am installing ubuntu from a ISO image.
PLease help me out.

---

### Post by grahammechanical on 2015-09-17
Boot from the ISO image and select Try Ubuntu. That will get you to a working Ubuntu desktop. Open the Dash and search for terminal. Click the top icon on the Launcher (left side panel).

You must have already done this to the extent that you were able to select Install Ubuntu. How do you know that you only have 3 primary partitions? We cannot give accurate advice unless we see for ourselves the partition layout.

As an alternative, you can load Windows and use a Windows utility to display the drive partitions. Then take a screenshot and post the results in this thread.

---

