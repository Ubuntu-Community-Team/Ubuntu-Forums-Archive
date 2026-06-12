---
title: "Recover Time machine backup from corrupt MyBook network drive"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by MArkpQ on 2013-10-20
Hello,

i have a WD network drive ( MyBookWorld 1TB )  , i was using it as Time machin backup on the defult backup folder ( Wd_Backup ) , i did a mistake by giving a delete command on mac then i disconnect the dive and the result i could not access the drive on mac or windows. i have removed the drive from its case and connected it to usb case so i check it. i found out that i have corrupt the data in it, i installed Ubuntu so i can access the drive and it was successful ,  and i found the hidden folder by using Ctrl+H on the drive but i dont have permission to copy data. is there a way i can do that?

[http://img199.imageshack.us/img199/9626/3x9w.png](http://img199.imageshack.us/img199/9626/3x9w.png)

[http://img820.imageshack.us/img820/5082/dq3.png](http://img820.imageshack.us/img820/5082/dq3.png)

[http://img197.imageshack.us/img197/9774/3ogy.png](http://img197.imageshack.us/img197/9774/3ogy.png)


Regards.

---

### Post by MArkpQ on 2013-10-24
waw 130 views and one replied? 

just sharing coz i care


[FONT=Helvetica]apt-get install fuseext2[/FONT]
[FONT=Helvetica]apt-get install lvm2[/FONT]
[FONT=Helvetica]apt-get install mdadm

then mount the raid drive

[/FONT]
[FONT=Helvetica]mdadm --assemble --scan

finally 

[/FONT]
[FONT=Helvetica]gksu nautilus

Regards.[/FONT]

---

