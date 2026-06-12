---
title: "I can't create a .pdf with &quot;Project management&quot;"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by naomibrown on 2012-03-21
Hi, 

I've been learning how to use Project Management to create a Gantt chart. I want to print it as a .pdf but when I do this by going to File - Print and choosing to print to file it responds with this error message:

Error opening file '/home/naomi/Documents/Masters in Teaching and Learning/Phase 3/gantt chart.pdf': Permission denied

Any ideas how to fix this? 

Thanks,
Naomi

---

### Post by mraandtux on 2012-03-21
Try gksu nautilus and change the permission of the file.

---

### Post by naomibrown on 2012-03-21
Okay, so I tried to install gksu nautilus using the information at: 

[http://www.ubuntugeek.com/nautilus-gksu-gksu-extension-for-nautilus-allows-you-to-open-files-with-administration-privileges.html]("http://www.ubuntugeek.com/nautilus-gksu-gksu-extension-for-nautilus-allows-you-to-open-files-with-administration-privileges.html")

I found that when I had installed this I could create the file I wanted to. 

Thanks :)

Is nautilus what I use to browse my files and folders? And does gksu  basically mean allow me to be an administrator? I thought I was an administrator all the time?

---

### Post by philinux on 2012-03-21
> **naomibrown said:**
> 
Is nautilus what I use to browse my files and folders? And does gksu  basically mean allow me to be an administrator? I thought I was an administrator all the time?

Nautilus is the file browser used when you click on Home or a folder etc.

```
gksu nautilus
```

Is the root file browser and must be used with care as you can inadvertently delete system files. (Borked system results.)

Effectively you run like a limited user but with easy to access admin rights.

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Scroll down.

---

### Post by naomibrown on 2012-03-21
Thanks!

---

