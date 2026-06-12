---
title: "Java Error on Dapper 64-bit"
date: 2006-02-28
forum: Programming Talk
---

### Post by tman_ubuntu on 2006-02-28
2 part question:

1 - I have this weird error I can't resolve.  

Background:
     
I have a java program that uses java's Mail.jar for emailing.  Currently it able to compile and run on Ubuntu Breezy 32-bit, Slackware 10.1, and W2k.  On these previously mentioned platforms, I have jdk-1.5 installed.  I have recently switched my Slackware 10.1 server over to Ubuntu Dapper 64-bit.  I have installed Sun's JDK-1.5 on Dapper 64-bit successfully (so it seems).

Problem:

The exact Mail.jar file being successfully used on these other platforms, is causing a compile error on Dapper 64-bit that it does not cause on the other platforms and distrobutions.  The error message that it gives: "Symbol not found: at method: message.setSendDate(java.util.Date)"  In my code I have a reference to a Message object called "message".  It compiles fine if I comment this one line out that sets the "setSendDate()" property, so it is finding the Mail.jar file in the classpath.  For whatever odd reason it doesn't see the method in the Message class.

excerpt:
```

...
message.setRecipient(Message.RecipientType.TO, toAddr);
message.setSubject("IRHFIP");
**message.setSentDate(new Date());**
message.setContent(msg,"text/plain");
Transport.send(message);
...

```

2 - I would like to uninstall the gcj java compiler that is the default in Dapper or any version of Ubuntu.  Does anyone know how to uninstall GCJ or not make it the default run-time or compiler without boogering up the rest of the system?

---

### Post by tman_ubuntu on 2006-02-28
HOLY CRAP.  Nevermind.  Figured it out.  Typo.  BIG Typo.  Sorry to waste all of your time. I guess it just takes to write out a long winded post to figure it out.  Mods, please feel free to delete.  :oops: :oops:

---

### Post by hod139 on 2006-02-28
To answer part 2 of your question, 

To make Sun the default, see my post [here]("http://ubuntuforums.org/showpost.php?p=759370&postcount=2") skipping step 1 which is how to install Sun's SDK.

 To remove the gcj runtime if desired,
 ```
   
sudo apt-get remove --purge java-gcj-compat
 
```

---

