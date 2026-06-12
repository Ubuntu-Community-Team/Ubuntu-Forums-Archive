---
title: "root folder in root folder - Confused"
date: 2015-02-16
forum: New to Ubuntu
---

### Post by karmic2 on 2015-02-16
I found an interesting topic on ubuntu directory structure : [http://ubuntuforums.org/showthread.php?t=2037324](http://ubuntuforums.org/showthread.php?t=2037324) 

But when I checked my own Ubuntu -14 (which is running in VM Virtual box ) I found that root folder (/) has another root folder ?? What is it and why nobody mentions it in any directory structure tutorials ??

Thanks in advance...

---

### Post by Holger_Gehrke on 2015-02-16
Are you talking about the directory '/root' ? That's the home directory for the system's administrator. It has to be directly in '/' because the admin might have to log in to a damaged system which can't or won't mount other partitions or disks.

---

### Post by karmic2 on 2015-02-16
yes , i am talking about /root. Thanks i got it now.

---

### Post by slickymaster on 2015-02-16
Here is a good asset you might want to have a read at:

[http://refspecs.linuxfoundation.org/FHS_2.3/fhs-2.3.html](http://refspecs.linuxfoundation.org/FHS_2.3/fhs-2.3.html)

---

