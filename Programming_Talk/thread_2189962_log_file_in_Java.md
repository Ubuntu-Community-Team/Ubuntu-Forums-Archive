---
title: "log file in Java"
date: 2013-11-25
forum: Programming Talk
---

### Post by chuchi on 2013-11-25
Hi everyone!
 

 I am developing a socket server in Java that will run in a remote machine.  
 

 Now I am testing in my local machine so when my Java program crashes I can see the log error in Eclipse. But in the remote machine I will not be able see the log.
 

 Can I configure in Java a log file?? so when my program crashes the log file contains a description of the error. That way, I can see that log file in the remote machine.
 

 Thank you very much!!

---

### Post by ofnuts on 2013-11-25
The usually way to log things in Java (especially in servers) is to use the log4J toolbox from Apache. You can even have it catch stdout/stderr, see [http://stackoverflow.com/questions/8489551/logging-error-to-stderr-and-debug-info-to-stdout-with-log4j](http://stackoverflow.com/questions/8489551/logging-error-to-stderr-and-debug-info-to-stdout-with-log4j)

Normally, you code should be running inside a try/catch block so you catch errors and display relevant info in case of errors...

---

