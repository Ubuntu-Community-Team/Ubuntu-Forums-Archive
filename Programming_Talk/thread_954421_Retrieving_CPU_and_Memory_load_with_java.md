---
title: "Retrieving CPU and Memory load with java"
date: 2008-10-21
forum: Programming Talk
---

### Post by anonym0us on 2008-10-21
Hi everyone,
   The title pretty much describe my problem. I am creating a swing application that could display CPU and memory load using java in Ubuntu environment. I suspect that I need to use JNI to communicate with native library in Ubuntu but I don't which and after some googling, do not really find any articles that could help. I thought of running top and parsing the output every second but I don't that is an elegant approach.

Could anyone shed some light on this?

forgot to mention: I am using java 6.

---

### Post by cl333r on 2008-10-21
Read about the /proc dir, for instance the files "meminfo", "uptime" and alike, some quick googling:
[http://www.howtogeek.com/howto/ubuntu/get-cpu-system-load-average-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/get-cpu-system-load-average-on-ubuntu-linux/)

---

### Post by anonym0us on 2008-10-22
Thanks for the reply. Is there some kind of library which i can call the function directly to retrieve the data though? Similar to windows with a call to getsysteminfo() from WinAPI.. I am not experienced at native system call and such. I need something similar to work with in Ubuntu or *nix based system in general. Or any other better suggestion is accepted.

---

