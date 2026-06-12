---
title: "[SOLVED] Java, Firefox and Airport Monitor"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-10-09
I'm trying to run:

[http://www4.passur.com/lax.html](http://www4.passur.com/lax.html)

When I surf there, I get a message "You are using Netscape" and No JRE is installed.

I emailed the company: 

[http://www4.passur.com](http://www4.passur.com)

and their tech support emailed back and said "We use Firefox on Windows XP.  You may want to update Java, clear your cache and then restart the application."

What is the latest Java for Ubuntu? Is a cleared cache as good as a clear conscience?

and

I got this from the terminal but don't understand it:

mark@Lexington-19:~$ java showversion
Exception in thread "main" java.lang.NoClassDefFoundError: showversion
Caused by: java.lang.ClassNotFoundException: showversion
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: showversion. Program will exit.

---

### Post by baizon on 2008-10-09
Hi, you have to run the "java Airport.class" file. Do you got the sun-java6-jre package (the latest Version of Java is 1.6.07)?
You just run a part of the Program and the Error msg is that he is missing the Main Part of the Program.

---

### Post by Mark_in_Hollywood on 2008-10-10
> **baizon said:**
> Hi, you have to run the "java Airport.class" file. Do you got the sun-java6-jre package (the latest Version of Java is 1.6.07)?
You just run a part of the Program and the Error msg is that he is missing the Main Part of the Program.

Is "java Airport.class" part of the java jre package? Is it something the website installs while using their webpage? 

Yes, I have the latest JRE package. A google search of "java Airport.class" has no information on the 'net.

---

