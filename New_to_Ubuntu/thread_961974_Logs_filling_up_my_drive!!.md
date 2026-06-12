---
title: "Logs filling up my drive!!"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by porteclefs on 2008-10-28
Hello,

I'm not sure, but I think the amount of used space on my HDD is growing with each passing day ... I think that it is being filled by logs. I have a LAMP running on Ubuntu Server Edition (newest stable) and am also running gnump3d (which might be keeping logs too)

So, where do I start? How do I disable logging? Clean out the logs? Or, rather, what is the best-practice approach to preventing logs from taking over one's computer?

Thanks,
Porteclefs

---

### Post by Xiong Chiamiov on 2008-10-28
First make sure that your problem is indeed logs.  Most of them should be in /var/log, so check the size of that.

---

### Post by drs305 on 2008-10-28
You can search you entire system for large files with the following command. Very few files are larger than 500MB after an initial install. Note these won't identify situations in which many individual smaller files are generated.
```

sudo find / -name '*' -size +1G
sudo find / -name '*' -size +500M

```

---

### Post by Zimmer on 2008-10-28
I note you say Server edition , have you looked at the DISK Usage analyser to see if var/log is growing?
check the .thumbnails folder  apparently I have 134mb there compared to 12mb in var/log

messages seems to have the largest log files. The higher number the zipped archive the older it is. My guess (GUESS) is you could delete the highest numbered old zipped logs and things would carry on as normal...

any use?
[http://www.cyberciti.biz/faq/how-do-i-rotate-log-files/](http://www.cyberciti.biz/faq/how-do-i-rotate-log-files/)
[http://www.ducea.com/2006/06/06/rotating-linux-log-files/](http://www.ducea.com/2006/06/06/rotating-linux-log-files/)

---

### Post by porteclefs on 2008-10-28
Thanks for all of your posts... I'm not convinced it's logs now. I think I'm going to keep my eye on the disk and see if it keeps growing...

---

