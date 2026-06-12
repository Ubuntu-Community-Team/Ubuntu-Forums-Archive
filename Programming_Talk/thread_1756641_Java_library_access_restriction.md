---
title: "Java library access restriction"
date: 2011-05-12
forum: Programming Talk
---

### Post by Z.K. on 2011-05-12
I am getting this error when I try to use the rxtx library in eclipse.

> 
Access restriction: The type CommPortIdentifier is not accessible due to restriction on required library /usr/lib/jvm/java-6-openjdk/jre/lib/ext/RXTXcomm.jar


How do I fix this, do I have to change the permissions?

:confused:

---

### Post by r-senior on 2011-05-12
Do these help?

[http://www.eclipsezone.com/eclipse/forums/t97259.html](http://www.eclipsezone.com/eclipse/forums/t97259.html)
[http://lkamal.blogspot.com/2008/09/eclipse-access-restriction-on-library.html](http://lkamal.blogspot.com/2008/09/eclipse-access-restriction-on-library.html)

---

### Post by anadikumar on 2012-09-01
:p
1. Go to the Build Path settings in the project properties.
		2. Remove the JRE System Library
		3. Add it back; Select "Add Library" and select the JRE System Library. 
		The default has worked for my friends as well.
		It works because we have multiple classes in different jar files. Removing and re-adding the jre lib will make the right classes be first. 
		
**Regards**,
**[COLOR="Blue"]Anadi Kumar[/COLOR]**
Patna, Bihar (INDIA)
Have 4.75 years of IT (Java-Development & Design) experience.
Worked @ 
	1. Persistent System Ltd.
	2. HSBC Global Tech. (India) Ltd.
	3. TechMahindra Ltd.
Email-ID:[COLOR="blue"]anadikumar@gmail.com[/COLOR]
Cell/Mobile No.: +91-8055992543.

---

