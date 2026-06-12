---
title: "How to set netbeans to use SUN jdk instead of open Jdk??"
date: 2009-12-23
forum: Programming Talk
---

### Post by pepe machine on 2009-12-23
hello there, 

i want to set my netbeans to use sun jdk instead of open jdk. 
i have sun jdk and jre installed but when i type java -version in the terminal

it displays 

```
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu1)
OpenJDK Server VM (build 14.0-b16, mixed mode)
```

---

### Post by no1wantdthisname on 2009-12-24
```

update-java-alternatives -l

```

Then
```

update-java-alternatives -s (From above)

```

---

### Post by pepe machine on 2009-12-24
wow, thanks.. 

but i receive this message

```
update-alternatives: error: no alternatives for mozilla-javaplugin.so.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.

```

but i have successfully change it to sun java

java -version
```

java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)
```

---

### Post by pepe machine on 2009-12-25
hello everyone, i think netbeans still uses openjdk.. hmmm any idea guys..??

---

### Post by pepe machine on 2009-12-25
this thread is done. i have my netbeans set to sun java.. i manually installed netbeans.. hehe thats the easiest way.

---

