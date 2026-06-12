---
title: "mucked up my grub"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by quarkhirad on 2008-08-06
Hello 

Ok i was running ubuntu 8.04 fine i had in mind of have a virtual version for windows. Sonmehow i never got to doing it and hence i booted into a live cd deleted the partion i had created for the virtual windows and expanded my root partion of ubuntu. I got a grub error no 17. Then i tried the following ion terminal of a live cd 

```
sudo grub 

find /boot/grub/stage1


```

i got 

(hd0,7)

hence i did 

```
root (hd0,7)
setup (hd0)
quit 
```

It said successfully done. But when i rebooted it gave me my grub menu but when i selected ubuntu it said 

error 22 no such partition 

please press any key to continue 


please help

---

### Post by rEbyTer on 2008-08-06
You have selected a wrong partition. When your grub is popping up press 'e' to edit your partition.

try **hd0,0** ,**hd0,1** , **hd0,2** ... **hd0,6**

if you find the match, post again to help you make forever that change , ok ?

---

### Post by Dedoimedo on 2008-08-06
Hello,

Please see my grub tutorial, I think it will help you:
[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

Furthermore, great software for GRUB recovery:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Dedoimedo

---

### Post by quarkhirad on 2008-08-07
Dear rEbyTer

Thanks hope these snaps should help you. 

This is a snap of my partition table 

[http://www.badongo.com/pic/4164598](http://www.badongo.com/pic/4164598)

this is an print screen of the terminals showing each detail of the comands

[http://www.badongo.com/pic/4164603](http://www.badongo.com/pic/4164603)


[http://www.badongo.com/pic/4164611](http://www.badongo.com/pic/4164611)


hope this helps

---

