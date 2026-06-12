---
title: "Netbeans 5 install problem"
date: 2006-09-01
forum: Programming Talk
---

### Post by sarikan on 2006-09-01
Hi there, 
I have java 5 in my system, and eclipse works without any problems. However, netbeans 5 install does not work. When I execute the installer from terminal, all I get is  
Initializing InstallShield 
Extracting Installation Archive.
and it silently gets back to prompt. I have JAVA_Home setup correctly. This is drapper by the way, any ideas about this ?
Regards
Seref Arikan

---

### Post by muzzamo on 2007-03-05
Try:

```
./netbeans-5_5-linux.bin -is:log a.log
```

In my case it gave

```
Extracted Installer JAR archive file size incorrect. archive may be corrupt. Fai
led to launch the application.
```

From which I concluded it was a corrupt download.

---

