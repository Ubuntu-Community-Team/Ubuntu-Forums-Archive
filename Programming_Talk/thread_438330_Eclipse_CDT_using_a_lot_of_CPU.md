---
title: "Eclipse CDT using a lot of CPU"
date: 2007-05-09
forum: Programming Talk
---

### Post by Mirrorball on 2007-05-09
Eclipse CDT was using a lot of CPU for code completion. I have turned it off but when I typed the ">" in std::set<AClass>, CPU usage went up again. What could the problem be? It's running on Sun Java 6 64bits. I love this IDE but it's too slow. I don't think it was this slow on Edgy.

---

### Post by darreng on 2007-05-10
I'm having the same problem... every few minutes Eclipse just goes away for about 30-40 seconds and top shows java using 100% of the CPU.  No indication from Eclipse about what it might be doing.

---

### Post by Mirrorball on 2007-05-10
> **darreng said:**
> I'm having the same problem... every few minutes Eclipse just goes away for about 30-40 seconds and top shows java using 100% of the CPU.  No indication from Eclipse about what it might be doing.
Exactly what is happening here. I think it's trying to do code completion, although I turned it off.

---

### Post by HP-X on 2007-05-17
This one helped me. Hopefully it can be helpful to you too.

[http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

---

### Post by Mirrorball on 2007-05-17
Thanks, but I'm already using Sun's Java.

---

### Post by olejorgen on 2007-05-17
You're sure *eclipse* is using java-sun? I think you need to edit some config files. I't s not enough to do update-java-alternatives or install java-sun. 

Just to be sure. :)

---

### Post by PartickThistle on 2007-05-17
Try this from the command line to ensure you're using Sun's java.

```
JAVA_HOME="/path/to/sun-jre/" eclipse
```

I'm currently using 64bit jrockit for eclipse and it's speeding along.  I have also disabled/uninstalled every add-in I don't/won't use.

---

### Post by Mirrorball on 2007-05-17
> **olejorgen said:**
> You're sure *eclipse* is using java-sun? I think you need to edit some config files. I't s not enough to do update-java-alternatives or install java-sun.
Interesting, I didn't know that. I'm going to check tomorrow, thanks!

---

### Post by HP-X on 2007-05-18
Add /usr/lib/jvm/java-6-sun to your /etc/eclipse/java_home and it will probably work.

---

