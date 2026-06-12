---
title: "Eclipse not starting"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by kobras on 2008-07-23
I have install eclipse(version 3.2), but when i want to start it i have error massage:
An error has occurred. See the log file
/home/maryan/.eclipse/org.eclipse.platform_3.2.0/configuration/1216805076263.log.
i have attached also log file.

---

### Post by timo_01 on 2008-07-23
> **kobras said:**
> I have install eclipse(version 3.2), but when i want to start it i have error massage:
An error has occurred. See the log file
/home/maryan/.eclipse/org.eclipse.platform_3.2.0/configuration/1216805076263.log.
i have attached also log file.

maybe you need to install java if not installed.try it

---

### Post by kpkeerthi on 2008-07-23
Install [Sun Java and choose it as the default]("https://help.ubuntu.com/community/Java"). Now try eclipse

---

### Post by kobras on 2008-07-23
i have install everything, and choose java 6 like a default, but it still the same mistake.
i think i should change /etc/eclipse/java_home
# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.

#/usr/lib/jvm/java-7-icedtea
/usr/lib/jvm/java-gcj
/usr/lib/kaffe/pthreads
/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-1.5.0-sun
/usr/lib/j2se/1.5
/usr/lib/j2se/1.4
/usr/lib/j2sdk1.5-ibm
/usr/lib/j2sdk1.4-ibm
/usr/lib/j2sdk1.6-sun
/usr/lib/j2sdk1.5-sun
/usr/lib/j2sdk1.4-sun

maybe if i will put java-6-sun at the start its will work?
and question how i can change it and save using terminal? because in normal way i dont have permission

---

### Post by kobras on 2008-07-23
maybe a new log file can help

---

