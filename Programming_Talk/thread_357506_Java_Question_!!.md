---
title: "Java Question !!"
date: 2007-02-09
forum: Programming Talk
---

### Post by Mba7eth on 2007-02-09
Hi all , I need some help in the following !! 

I'm designing an applet i'm done with it but the problem is i cant open the applet from a browser becuase this applet is trying to open a file and the broswer doesn't give the premission to open the file .... So anyone any help ... How to get around this problem ?

---

### Post by Engnome on 2007-02-09
Applets cannot read/write files on the computer it's running on. Security reasons. They should be able to read from the server though. Exactly what are you trying to do? You are being very vague...

---

### Post by laxmanb on 2007-02-09
there's a program called "policytool" which comes with the JDK...

type **policytool** @ the command prompt/terminal...

you have to make a new policyfile that allows the applet access to files...

---

### Post by Mba7eth on 2007-02-09
Engnome , Sorry for my bad english 8-[ .
I want the following : 
what i want is how to open a file thru an applet ? 


I going to try policytool laxmanb :-k

---

### Post by David Mulligan on 2007-02-10
If it is read-only why don't you host the file on the server?

The problem with altering the security policy on the client machine is that everyone who wants to run the applet will have to do that.  I for one am glad that applets cannot access or modify files on my computer.

---

### Post by Mba7eth on 2007-02-10
hmmmmm .... Yes it is a read only. I guess what you mention is going to be the solution. 
One more Question : 
          If i added this file to the jar file can i open it on my local box. I have tried but I really couldn't.

---

