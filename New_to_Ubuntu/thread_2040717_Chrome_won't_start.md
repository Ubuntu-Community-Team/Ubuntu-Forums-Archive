---
title: "Chrome won't start"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by KeremE on 2012-08-11
When I tried to open google-chrome, I received the following error: 

[28228:28251:6555757260:ERROR:shared_memory_posix.c c(171)] Creating shared memory in /dev/shm/.com.google.Chrome.x4LJvf failed: No such file or directory
[28228:28251:6555757388:ERROR:shared_memory_posix.c c(174)] Unable to access(W_OK|X_OK) /dev/shm: No such file or directory
[28228:28251:6555757422:FATAL:shared_memory_posix.c c(176)] This is frequently caused by incorrect permissions on /dev/shm. Try 'sudo chmod 1777 /dev/shm' to fix.


I soon found out that /dev/shm did not exist on my system. I am not sure what's wrong? This happened soon after a system freeze that resulted in me forcing a hard reboot.

Thanks!
KeremE

---

### Post by cwsnyder on 2012-08-11
It looks like you left a Google Document open or the Google Drive open when you rebooted.  Did you try re-logging into Google to fix it there?

---

### Post by KeremE on 2012-08-12
Thanks for your reply! It is very likely that I was using Google Docs when I rebooted, but I'm not sure how to fix this by logging into Google? How would an open google doc affect the way Chrome starts? 

Thank you,
KeremE

---

### Post by johnathansmith on 2012-08-12
Go in in terminal and type:

```
sudo ln -s /run/shm /dev/shm

```

[source is askubuntu ]("http://askubuntu.com/questions/167353/missing-dev-shm")

---

