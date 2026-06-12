---
title: "Can run  unetbootin"
date: 2014-03-26
forum: New to Ubuntu
---

### Post by lou7 on 2014-03-26
My main goal is to create a USB boot drive from an image.



lubuntu@lubuntu:~$ unetbootin
The program 'unetbootin' is currently not installed. You can install it by typing:
sudo apt-get install unetbootin
lubuntu@lubuntu:~$ ^C
lubuntu@lubuntu:~$ sudo apt-get install unetbootin
[B]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
lubuntu@lubuntu:~$[/B]

I'm not sure what to do next:

Just learning how to navigate with this OS, trying to learn it before the WIndows XP April 8th shut down date.

Thanks

---

### Post by oldos2er on 2014-03-26
First thing to try is do what it says: ```
sudo dpkg --configure -a
```

---

