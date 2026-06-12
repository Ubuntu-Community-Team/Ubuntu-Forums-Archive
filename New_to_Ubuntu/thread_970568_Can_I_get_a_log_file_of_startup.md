---
title: "Can I get a log file of startup?"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by SpinningAround on 2008-11-04
I'm would like to get a log file or similar on what is happening during start-up, you know all that text you see while the system is loading in recovery mode.

The problem is that due to a bug can't I access ubuntu since the start-up freezes during this time and only way to get out of it, is to use ctrl + alt + del. Is there a boot argument that you can add that make the linux print out what is happening during start up?

I would simply like the information shown in the pictures in this thread [http://ubuntuforums.org/showpost.php?p=6102240&postcount=21](http://ubuntuforums.org/showpost.php?p=6102240&postcount=21) printed to a log file or similar

---

### Post by wizard10000 on 2008-11-04
You'll find what you're looking for in /var/log/messages.

good luck -

---

### Post by fornix on 2008-11-04
Press Alt + F1 while you see the ubuntu splash.
It will show you whats happening in the background.
Hope that helps

---

### Post by philinux on 2008-11-04
Also System>Admin>System log and type in dmesg in the terminal.

---

### Post by SpinningAround on 2008-11-04
Thanks for the answers but it didn't help :( I wasn't able to gain access to the right dmsg log with LiveCD, guess that the dmsg message is from the the install since that was the only successful startup so far.

---

### Post by hyper_ch on 2008-11-04
if you run the live cd and want to get access to the log on your harddisk you first have to mount it.

---

