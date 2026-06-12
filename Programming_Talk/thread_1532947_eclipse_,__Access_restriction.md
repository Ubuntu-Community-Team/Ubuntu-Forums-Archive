---
title: "eclipse ,  Access restriction"
date: 2010-07-17
forum: Programming Talk
---

### Post by miko5054 on 2010-07-17
im trying a java code that will send mail from the code

i cant run it because im receiving this error and cant import  method`s  
 
```

import com.sun.corba.se.impl.protocol.giopmsgheaders.Message;
import com.sun.xml.internal.fastinfoset.sax.Properties;
import com.sun.xml.internal.messaging.saaj.packaging.mime.MessagingException; 
```

```
  Access restriction: The type Message is not accessible due to restriction on required library /usr/lib/jvm/java-6-openjdk/jre/lib/rt 
```

thanks 
miki

---

### Post by lykeion on 2010-07-17
It sounds like you need to use Sun Java instead of OpenJDK. 

Link: [Eclipse and Sun Java (Sun JVM System Wide)]("https://help.ubuntu.com/community/EclipseIDE#Sun%20JVM%20System%20Wide")

1. Enable partner repo:```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```2. Install Sun Java 6 JDK```
sudo aptitude install sun-java6-jdk
```3. Setup to use it as default (as described in above link)

---

### Post by miko5054 on 2010-07-17
i installed java-6 set it to defult ,removed the openjdk but same result...

```
 Access restriction: The type Message is not accessible due to restriction on required library /usr/lib/jvm/java-6-sun-1.6.0.20/jre/
```

---

### Post by miko5054 on 2010-07-17
those import aren't in the original java Api so i dont to use them anyway 

thanks for the support

---

