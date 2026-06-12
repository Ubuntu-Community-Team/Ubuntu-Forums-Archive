---
title: "Some freezing"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by linux_newf on 2008-08-19
I have used Hardy now since its released and its been the best OS i ever used so far but the last 5 days or so i had to reboot a few times because my laptop pretty well froze - the first time(s) since i installed ubuntu - i have noticed a number of updates lately which i downloaded and wonder if anyone noticed the samething.

Is there a virus scanner for linux? I'm just using the out of the box hardy, security wise.

Thanks,
Brad

---

### Post by Sorivenul on 2008-08-19
Try clamav for antivirus.  Shouldn't be though, as the updates were universal and are a fairly common occurrence on Ubuntu.  As for the freezing, I'm at more of a loss.

---

### Post by meanburrito920 on 2008-08-19
Next time it freezes can you hit ctrl-alt-F1. login and run top and tell us what is using the cpu.

---

### Post by nicedude on 2008-08-19
There are currently zero viruses that can infect your Ubuntu machine. A virus has nothing to do with any freezes you are thinking like a windows user there :-). I would suggest if it starts freezing to run top or better yet the graphical version htop to see what is taking up all your CPU and resources. While that wont solve it, at least it could tell you what the offending program is.

Hope that helps and you can forget about viruses while in Ubuntu.

---

### Post by Mizutsuki on 2008-08-19
If this truly is a freeze, and not the CPU peaking, then I would say that phantom freezes are generally the word of faulty/dying ram.  Try this overnight and see what it says:
[www.memtest.org](www.memtest.org)

---

### Post by Sorivenul on 2008-08-20
Try the memtest option first, but I thought of this as well:
A "freeze" may be related to how the system is utilizing swap space.  I don't know your system specifications (RAM, etc), but adjusting swappiness may also help, though I wouldn't suggest this without at least 1G of RAM.
```
sudo nano /etc/sysctl.conf
```
Then add then line:
```
vm.swappiness=0
```

---

