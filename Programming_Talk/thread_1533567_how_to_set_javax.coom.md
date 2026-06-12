---
title: "how to set javax.coom?"
date: 2010-07-18
forum: Programming Talk
---

### Post by miko5054 on 2010-07-18
i want to use those  classes 
```
 
import javax.	mail.Address;
import javax.mail.Message;
import javax.mail.MessagingException;
import javax.mail.SendFailedException;
import javax.mail.Session;
import javax.mail.Transport;
import javax.mail.event.ConnectionEvent;
import javax.mail.event.ConnectionListener;
import javax.mail.event.TransportEvent;
import javax.mail.event.TransportListener;
import javax.mail.internet.AddressException;
import javax.mail.internet.InternetAddress;
import javax.mail.internet.MimeMessage;

```

what should i do?

---

### Post by PaulM1985 on 2010-07-18
I would start by downloading the files for this from here:
[http://java.sun.com/products/javamail/downloads/index.html](http://java.sun.com/products/javamail/downloads/index.html)

Unzip the file and follow the readme to get it setup.  You need to add the .jar file to your classpath.

There is also example code in the zip file for you to test.

Hopefully this is enough to get you started.

Paul

---

### Post by miko5054 on 2010-07-18
i create a class-path and i manually  put the jar into lib folder and bulid path ,but im receiving this again

```
 Access restriction: The type MimeMessage is not accessible due to restriction on required library /usr/lib/jvm/java-6-openjdk/jre/lib/ext/mailapi.jar
```

thanks
miki

---

### Post by miko5054 on 2010-07-18
i think that will solve it///
[HTML] http://lkamal.blogspot.com/2008/09/eclipse-access-restriction-on-library.html[/HTML]

---

