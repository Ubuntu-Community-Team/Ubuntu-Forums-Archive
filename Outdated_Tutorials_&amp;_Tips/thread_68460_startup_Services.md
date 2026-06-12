---
title: "startup Services"
date: 2005-09-23
forum: Outdated Tutorials &amp; Tips
---

### Post by markr on 2005-09-23
When I was using Fedora, they had a very useful utility that allowed you to see all the services that were started at boot, and allow you to disable them if required (like scheduling, or Network clock sync for example).

Does Ubuntu have a similar feature?

Mark.

---

### Post by jamesford on 2005-09-23
install boot-up manager (BUM)

---

### Post by frodon on 2005-09-23
It's not the good place for questions  [-X 
However what you need is [BUM](http://ubuntuforums.org/showthread.php?t=42129).

---

### Post by ronin69hof on 2005-09-23
You can also cd to /etc/init.d and do:

update-rc.d -f "servicename" remove

but be sure what you are removing before you kill your system


ronin

---

