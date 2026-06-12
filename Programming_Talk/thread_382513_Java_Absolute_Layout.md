---
title: "Java Absolute Layout"
date: 2007-03-12
forum: Programming Talk
---

### Post by derby007 on 2007-03-12
If my Java application is using depended classes like 
	"org.netbeans.lib.awtextra.AbsoluteLayout" 
and not swing classes (e.g. java.awt.BorderLayout), 
how can I get my app to run in standalone mode 
eg. 'java -jar myApp.jar' from command line ??

---

### Post by laxmanb on 2007-03-12
I thought that netbeans makes a jar file anyway, and that jar file includes the AbsoluteLayout file... let me check...

---

### Post by derby007 on 2007-03-12
While you are checking......pls note i'm using SunJavaEnterpriseEdition8.........note: I can't get my apps to run in 'Standalone' mode......in either Ubuntu or M$.......bummer !

Side note : it doesn't use the FREE DESIGN that Netbeans uses........& I can't get it to work with SunStudio8....bummer !

---

### Post by derby007 on 2007-03-13
Bump : anyone any ideas on my 1st Question ? tnx.

---

### Post by laxmanb on 2007-03-13
1. About absolute layout: I checked the created JAR file with a WinZip and it does not contain the custom Layout manager... but I'm using JDK6 and the NB5.5 layout manager is now included by default with Java 6... so, I guess it was quite useless... but open the JAR file created by your tool with Archive manager, and see if the AbsoluteLayout class file shows up or not... I think it should...


2. Running JAR files in GNOME easily (thanks to phossal) : > 
Make Your Jar Files Double-Clickable (optional)
In this example, I'm working with Java set up as outlined in my tutorial (which isn't necessary), and the soon-to-be executable hello.jar on my desktop.
* Your JAR file must be properly exported to include the manifest (with main method).

1. Right click hello.jar -> Open With -> Open With Other Application -> Use a custom command

Code:

'java' -java

2. Rick click hello.jar -> Properties -> Open With -> java
(I'm selecting java, which is the command we just created, and have deselected Archive Manager as a result)

3. Double-click and run the file.



3. So, why don't you migrate to Netbeans?? just install the Enterprise Web Pack, and you'll have more functionality than what you're using now... plus, since what you're using now is based on NB4, the interface is quite similar too...

4. Which IDE you using?? Sun Java EE 8 is not an IDE...

---

### Post by derby007 on 2007-03-14
1. I'll give it a go.
2. Cheers.
3. I'm using SunStudio as I need it for UML.
4. I'm not sure what u mean !! I'm using Sun Java Enterprise 8 alright, and it has alot of functionality, UML, GOF patterns. (but i'm only a beginner really!)

---

### Post by laxmanb on 2007-03-14
Anyway, what are using is based on an older version of Netbeans... Sun has migrated a lot of that functionality to netbeans as packs... One pack supports UML... for more info: [www.netbeans.org](www.netbeans.org)

GUI creation is really a lot better with NB 5.0 & above...

---

### Post by derby007 on 2007-03-14
I'm a little bit into my project but i suppose i could change and redo it all again. I might even learn something new. 
If i port accross to Netbeans, it uses the FREE DESIGN GUI creation, with drag'n'drop, ie. uses the SwingLayout-1.0.jar.........so if I use this, what do i need to do to get it to run in 'standalone' ? 
Or quite simply: have you used it ?

---

### Post by Ragazzo on 2007-03-14
In Sun Java Studio Enterprise 8, as in Netbeans, when you build the project, the jar file is created in the directory project/dist. In that directory there is also README.TXT that should explain how to run and distribute it. Hope that helps.

---

### Post by laxmanb on 2007-03-15
> **derby007 said:**
> I'm a little bit into my project but i suppose i could change and redo it all again. I might even learn something new. 
If i port accross to Netbeans, it uses the FREE DESIGN GUI creation, with drag'n'drop, ie. uses the SwingLayout-1.0.jar.........so if I use this, what do i need to do to get it to run in 'standalone' ? 
Or quite simply: have you used it ?

Yes, I have used it... and it is quite cool... The best (free) way to make cross platform GUIs...

and yes, it does run in 'standalone' mode... it would be stupid for an IDE to make a jar file that doesn't run on most computers... In fact, netbeans 5.5 uses GroupLayout, which is included with Java SE 6

---

