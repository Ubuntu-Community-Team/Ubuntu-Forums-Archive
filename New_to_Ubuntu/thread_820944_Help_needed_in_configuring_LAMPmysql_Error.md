---
title: "Help needed in configuring LAMP/mysql Error"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by hollow_cc on 2008-06-06
Hello guys, 

  I'm new to the community and new to Ubuntu and the whole idea of Linux. I'm running Hardy Heron and I want to configure a LAMP on my computer. As I don't know much, from Google I've started with [this]("http://doc.ubuntu-fr.org/lamp"). Unfortunately, I've stumbled right at the end, in the section in which you relocate the directory containing your site (alias). After I made the  modifications to my.cnf, the browser gave me the error: "Forbidden. You don't have permission to access /mon_site/ on this server.". So I ran into [this]("http://forum.ubuntu-fr.org/viewtopic.php?id=224589"). After tampering with my.cnf, it gave me a strange error which I don't remember now. So I decided I should redo the whole process in the first link. Only that I encountered troubles with mysql this time, when reinstalling it. To this error messages 
*************************
"E: mysql-server-5.0: subprocess post-installation script returned error exit status 1"
"E: mysql-server: dependency problems - leaving unconfigured"
*************************
I tried to answer with [this]("http://ubuntuforums.org/showthread.php?t=676283"). As the command which entirely removes mysql, from the last post, in the previous link, didn't work I used synaptic to completely remove the mysql packages. It still won't install mysql after, giving me the same error. At this time I decided I should delete the etc/mysql folder, which turned out to be very uninspired. After reinstalling mysql, it led me to the same error. It generated the folder mysql for me, but no my.cnf. I really don't want to mess up things more then they already are, so is there an immediate solution? Can I start all over again with a clean instalation? I hope this wasn't a hard to follow post and the links in French are okay for you to get the steps I've been through. Million times thank you for your help.

---

### Post by hollow_cc on 2008-06-07
I found a solution, in cleaning all that I've installed before. This cleaned all dependencies:
```

sudo apt-get autoremove --purge mysql* 

```

I then continued more carefully with [this]("http://doc.ubuntu-fr.org/lamp") tutorial (which in fact started all this) and carried it through. It's been a long day, but it worthed. 
Lesson (scope: global): don't rush things, take a time to think it over, it will come to you eventually.

---

