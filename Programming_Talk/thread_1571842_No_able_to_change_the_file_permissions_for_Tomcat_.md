---
title: "No able to change the file permissions for Tomcat Server"
date: 2010-09-10
forum: Programming Talk
---

### Post by MohanaRao on 2010-09-10
Hi friends, 

   I was installed tomcat on my machine i want to integrate tomcat with Eclipse before that i have to change the file permissions. But i'm unable to do that even as root. 

sudo chmod 777 -R apache-tomcat-6.0.20/*

it's not giving me any error message but it's not modifying file permissions.

---

### Post by dwhitney67 on 2010-09-10
Changing permissions to 777 is unwise, and more than likely unnecessary.

Rather than present your solution, please present what the actual issue is with your Tomcat/Eclipse integration, and why you need to do this.

---

### Post by r-senior on 2010-09-13
I don't know if you are checking back on this but the best way to install Tomcat to run under control of Eclipse and for debugging is by downloading the archive direct from Apache and unpacking into a directory under your home directory. 

Then add as a server in Eclipse and tell it where you unpacked your local copy.

The version in the Ubuntu repositories is really intended as a production server and doesn't like Eclipse interfering with it.

---

### Post by MohanaRao on 2010-09-14
My problem is I want write servlet and jsp that's why i want to integrate tomcat with eclipse, [COLOR=Red]it's done.[/COLOR] But i'm not able change the directory permissions of the tomcat recursively even as a root. My doubt why it's not accepting change file permissions.

---

