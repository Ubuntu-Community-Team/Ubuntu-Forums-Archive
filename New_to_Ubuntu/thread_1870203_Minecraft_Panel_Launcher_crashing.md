---
title: "Minecraft Panel Launcher crashing"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by DaimyoKirby on 2011-10-26
I downloaded the minecraft.jar from minecraft.net, I installed Java 6u29 and uninstalled OpenJDK; when I manually ran *java -jar ~/.minecraft/minecraft.jar* in terminal, it opened and ran fine. But then when I made a launcher in my panel, and pasted the same command into the options, it didn't work. I checked the option to have it run in terminal, and terminal popped up, then disappeared right away.

Should I be doing something different?

---

### Post by Toz on 2011-10-26
This is a weird little annoyance, but try replacing ~ with the full path. eg.
:```
java -jar [COLOR="Red"]/home/user[/COLOR]/.minecraft/minecraft.jar
```

---

### Post by DaimyoKirby on 2011-10-26
Worked like a charm! Thank you very much!

---

