---
title: "Problem installing a program"
date: 2015-04-01
forum: New to Ubuntu
---

### Post by cobalt2 on 2015-04-01
I want to install Java on Linux Ubuntu 14.10. I attempted to create the folder Java in directory /usr and wasn't given the new folder option. When I attempted to transfer the tar.gz file to this directory I received the error, "Error moving file: permission denied." According to the acess permissions for this directory, "You are not the owner so you cannot change these permissions." This doesn't make any sense. I'm signed in as an Administrator.

---

### Post by Geoffrey_Arndt on 2015-04-01
Actually, it makes perfect sense.  There is no sign-in as admin in Ubuntu (only use of sudo (super user do) for temporary access to do systems & files modifications.     This is to prevent new users from nuking their systems via unneeded actions .

The recommended way to install java is via the ubuntu software center (just install the "ubuntu-essentials" package in the USC).

---

### Post by cobalt2 on 2015-04-01
What is the USC?

---

### Post by cobalt2 on 2015-04-01
Now I understand what the USC is, nevermind.

---

### Post by Geoffrey_Arndt on 2015-04-01
Ok, the essentials package is not really what I wanted to say . . . the proper package is "ubuntu-restricted-extras" . . . if you just search and use the term "restricted" you should see it.   Install it and then see if the java program you want to run will start.   Normally it should.    Just post back if any other issues.   (by the way, the other package (build-essential) is needed if you want to build programs and do a few other more specific development actions.

---

### Post by sandyd on 2015-04-02
See: [http://www.webupd8.org/2014/03/oracle-java-8-stable-released-install.html](http://www.webupd8.org/2014/03/oracle-java-8-stable-released-install.html) if you want a non-openJDK official version of java.

By default, due to liscencing, the Ubuntu repos carry OpenJDK instead of the official Oracle Java

---

### Post by cobalt2 on 2015-04-02
Thank you for you help. I found what I needed, and learned how to login as a sudo!

---

