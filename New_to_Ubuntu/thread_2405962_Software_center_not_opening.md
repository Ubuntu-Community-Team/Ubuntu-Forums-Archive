---
title: "Software center not opening"
date: 2018-11-13
forum: New to Ubuntu
---

### Post by rosyjag on 2018-11-13
Glad to say that I finally installed 16.04 LTS. Opted for weekly updates of installed software which comes up once a week and works all right. But in the meanwhile if I try to open the software center (Red square on the left with "A" on it) in order to install a new software (like VLC), the process wheel spins a while and stops, nothing opens. How do I install new software?
Thanks

---

### Post by Frogs Hair on 2018-11-13
Copy, paste, and run the following command in the terminal and report any errors.  

```
sudo apt update && sudo apt upgrade
```

---

### Post by rosyjag on 2018-11-18
Thanks, Frog's Hair. Did as you have suggested and I am attaching the error log.

---

### Post by rosyjag on 2018-12-18
Can someone help me to get my software center to work?
I'd like to install VLC and also an equivalent of Bluestacks, a program to run android apps on PC.

---

### Post by howefield on 2018-12-19
It is a probably a better idea to copy and paste the terminal output into your post, enclosing it in [noparse]```

```[/noparse] brackets rather than forcing people to open your file. Try changing the download server.

---

### Post by Frogs Hair on 2018-12-19
> Try changing the download server. 

This is the next step I would take and can be done from software & updates . Make sure Canonical partners repository is enabled as well.

---

