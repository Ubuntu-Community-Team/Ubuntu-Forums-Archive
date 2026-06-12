---
title: "Java image path problem"
date: 2013-04-27
forum: Packaging and Compiling Programs
---

### Post by HalilEE on 2013-04-27
Hi,I am not familiar to ubuntu. I need desktop path or hdd path like windows c:users..... or d: foldername(d is a second hard drive)
Can any one please help me? 
I found this but it does not work;

java code get the image from this path and put it to a variable;
a=new ImageIcon("/usr/share/applications/kde4/imagea.desktop").getImage();

---

### Post by Leuchten on 2013-05-01
/ is the top folder in linux. All harddrives and other data is contained within it. The path to a typical user's desktop is /home/<username>/Desktop, where <username> is the name of the current user.

---

