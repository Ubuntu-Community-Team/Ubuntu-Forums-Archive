---
title: "How to be sure that ./file_path.jar will open the application with java?"
date: 2011-06-15
forum: Programming Talk
---

### Post by leon.vitanos on 2011-06-15
So as you know .jar files can open with archive manager and OpenJDK Java.. 
With the command ./file_path.jar , the jar file will open with the default one that you have selected..
But how to be sure that it will open with OpenJDK Java?

---

### Post by slavik on 2011-06-15
> **Bong.Da.City said:**
> So as you know .jar files can open with archive manager and OpenJDK Java.. 
With the command ./file_path.jar , the jar file will open with the default one that you have selected..
But how to be sure that it will open with OpenJDK Java?
you can't know.

---

### Post by leon.vitanos on 2011-06-15
Somehow change all .jar files at your system to open with Java? :(

Probably then ./file_path.jar will open with java

---

### Post by PaulM1985 on 2011-06-15
Your best bet would be to include a script in the folder which contained

java -jar myJar.jar

Then you could just click on the script.

Paul

---

### Post by hakermania on 2011-06-15
right click on the file, properties, open with OpenJDK Java 6 Runtime or anything else

---

### Post by leon.vitanos on 2011-06-15
> **PaulM1985 said:**
> Your best bet would be to include a script in the folder which contained

java -jar myJar.jar

Then you could just click on the script.

Paul

Thanks! ;)

---

