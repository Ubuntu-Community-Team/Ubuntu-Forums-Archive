---
title: "Network Locations"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by JTG2003 on 2008-09-18
Hey .. like the forum says, I'm an absolute beginner. I installed it alongside with Windows XP.

In windows, I can press start >> run, and then type \\[Computer name or IP] to access another computer.

Is there any way to accomplish them same thing?

Thank you, Jeremy

---

### Post by Nxion on 2008-09-18
Ok so If I remember correctly all your would have to do is this in a terminal:

```
sudo apt-get install samba
```

Then, when that finishes, hit "ALT+F2" and you should get a run dialog. When that appears enter something like this:

```
smb://1.2.3.4/
```

And change the 1.2.3.4 to what ever IP address of the computer you want to access. let me know if that works for you :)

---

### Post by JTG2003 on 2008-09-18
Worked perfectly, Thank you!

---

### Post by Nxion on 2008-09-18
> **JTG2003 said:**
> Worked perfectly, Thank you!


No problem :) Glad I could assist. Remember to make this topic complete :)

---

