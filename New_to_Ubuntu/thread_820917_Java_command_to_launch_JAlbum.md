---
title: "Java command to launch JAlbum??"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by bagrol1 on 2008-06-06
I added a new item to main menu to launch JAlbum but the link/command does not work.

A link on the desktop as follows:

file:///home/bartek/Karina/JAlbum/JAlbum.jar

works fine.

However, the Menu does not let me insert Location(file) item only Application(command).

What command should I used to launch JAlbum?

Thanks!

---

### Post by Inxsible on 2008-06-06
Provided you have installed the appropriate JRE version required by that jar file and have it in the PATH environment variable, the command would be```
java /home/bartek/Karina/JAlbum/JAlbum.jar
```

---

### Post by bagrol1 on 2008-06-06
> **Inxsible said:**
> Provided you have installed the appropriate JRE version required by that jar file and have it in the PATH environment variable, the command would be```
java /home/bartek/Karina/JAlbum/JAlbum.jar
```

This does not do anything. I have Java installed but not sure how to change any variables. When I click on JAlbum.jar or use desktop link JAlbum launches. But the Menu link with the above command does not do anything.

---

### Post by bagrol1 on 2008-06-12
Bump... Nobody knows how to launch java programs from the menu?

---

### Post by txcrackers on 2008-06-13
Try
```
java -jar /home/bartek/Karina/JAlbum/JAlbum.jar
```

---

### Post by NovaAesa on 2008-06-13
Or if the above works, but then crashes or runs out of memory, you might want to try something more like this:

```
java -Xmx500m -Xms500m -jar /home/bartek/Karina/JAlbum/JAlbum.jar
```

---

