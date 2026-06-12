---
title: "Installed on 7gb and got only capacity of 3.3gb"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by lylatwars2012 on 2012-09-25
When i came to first screen asking for hdd space,i choosed 7gb and when the os was fully installed capacity was 3.3gb and got free space of 916mb only,os used up 2.4gb.

Note: I installed 7gb and got capacity of 3.3gb only,that doesn't look right.

---

### Post by jerrrys on 2012-09-25
Check for [hidden]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=show+hidden+folder&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F") trash folder

And welcome to the forums :)

---

### Post by thatguruguy on 2012-09-25
It's difficult to understand the point you're trying to make.

---

### Post by lylatwars2012 on 2012-09-25
I wanted 7gb of space,of which i installed but when i checked capacity was only 3.3gb and also got the same capacity with 5gb installation to the hard drive.

---

### Post by Cheesemill on 2012-09-25
Can you open a terminal and post the output of:
```
sudo fdisk -l
df -h
```

---

### Post by critin on 2012-09-26
> **lylatwars2012 said:**
> I wanted 7gb of space,of which i installed but when i checked capacity was only 3.3gb and also got the same capacity with 5gb installation to the hard drive.

This sounds like you're installing Wubi into windows.  Did you create a 7gb partition first or did you 'choose' 7gb for Wubi?  

The system standard install requires over 4+ gb just to install os, so 7 won't leave much.    7 minus 4+ will leave approximately  3.

With wubi you can 'choose' the size, usually it's something like 15 gb minimum, but 10 will work.

---

