---
title: "rubbish bin problem"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by s1wood on 2012-09-22
My netbook (Lubuntu 12.04)has recently run out of disc space due to downloading a lot of photos from dropbox. I have deleted most of the photos now and emptied the rubbish bin but I still only have 0.2% space left in home so I deleted a few more large folders I don't really need. When I then opened the Rubbish bin the folders weren't there,it seems to be empty - I emptied it anyway and got this message:

>Error while getting peer-to-peer dbus connection: The name :1.49 was not provided by any .service files<

The disc space has still not been freed,I have restarted the computer butit hasn't helped.

How do I find these unwanted files and get rid of them?

Susan

---

### Post by hakermania on 2012-09-22
Have you tried the pre-installed Disk Usage Analyzer program?
It can help you scan your home folder and see which folders are the larger and why.

---

### Post by s1wood on 2012-09-22
I haven't got Disk Usage Analyser on this system.I'm just looking at System Profiler for the Disk Usage.

---

### Post by jerrrys on 2012-09-22
Manually check your trash just to be sure

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=empty+trash+in+terminal&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=empty+trash+in+terminal&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by s1wood on 2012-09-22
I had no luck with the command line suggestions but I eventually found the trash files (using Puppy) and deleted everything. Now I am back on Lubuntu and the files have gone and the rubbish bin is working normally. 
Presumably I could have done the delete from the trash folder(.local/share) in Lubuntu but there must have been some reason why it was playing up to begin with.

Thanks for advice,

Susan

---

