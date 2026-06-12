---
title: "In Eclipse links in openjdk-6-doc documentation do not work"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by bademeister on 2008-10-13
Dear all,

I would like to use a local java api documentation with eclipse (I work with it offline a lot, therefore the need for a locally installed documentation). 

I have installed the openjdk-6-doc package. In eclipse, in the "package explorer" under "JRE System Library" I right-click "rt.jar", select "Properties" from the context menu and under "Javadoc Location" I specify the "Javadoc URL"->"Javadoc location path" as "file:/usr/share/doc/openjdk-6-jre/api/".

It looks like it is all there in this directory but Eclipse complains that the "Location does not contain file 'package-list'." even though there is a file "package-list.gz". If I ignore the warning and go ahead, help windows will appear if I hover over some command, but the links in this window will  not work. So for example, if I hover over the command

System.out.println("...");

then a help window explaining this output stream will appear, but links in the "Javadoc" window (e.g. PrintStream, String, Object etc.) will not work and a msgbox saying 
"The file /util/Formatter.html#syntax cannot be found. Please check the location and try again." 
appears. 
However, if I hit "Shift + F2" to open the help in a browser (Firefox), then links will work again. 

While this is not a huge issue, it is somewhat puzzling / annoying. What am I missing here? Any help is highly appreciated.
Thanks Paul

---

### Post by jamesstansell on 2008-10-17
I'm not sure, but it seems like I remember eclipse expecting the javadoc to be in a jar file.

Just curious - are you using openjdk-6 as your "JRE System Library"?

---

### Post by bademeister on 2008-10-18
Hi James,

thanks for your reply. I´m not with my computer right now, so I can´t check, but I will try it as soon as I get home. 

Actually no, I am using Sun´s JDK in Eclipse.
best
Paul

---

### Post by aasdfasdfg on 2010-05-29
The issue bademeister is describing is just the default configuration, with the documentation linking to a URL. I described how I got eclipse configured on my computer in the post: [http://ubuntuforums.org/showthread.php?p=9380862#post938086](http://ubuntuforums.org/showthread.php?p=9380862#post938086)

---

