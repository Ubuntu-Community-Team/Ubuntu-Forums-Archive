---
title: "how to install application/programs"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by seal308 on 2012-04-10
How do you install applications/programs not in software center.
I went to the program's website and download the linux verison.
I get a .jar folder/package 
i know both programs use java
so i right click and open with jdk java 6
i get this message
"the file *filepath* is not marked as executable. It may be dangerous to run.
I am able to open it using the archive manger and look at the package contents. I see .class files etc, so i'm assuming those are the java components of the package. 
Can anyone help?
Thanks
Oh and the 2 applications i'm trying to download are tomighty and dr java
Thanks again

---

### Post by PhantomTurtle on 2012-04-10
Make it executable. Right click on the file and click properties. Under the permissions tab check Allow executing file as a program. Now your file is executable.

---

### Post by seal308 on 2012-04-10
that works i can now run it.
however it's not like the other native applicaitons.
I don't have it's own icon or anything, it's just a jar file.
Is there a way for it to have it own icon.
Now it's sort of a hassle b/c i have to right click it and click open with jdk.
If i can't make it to an icon is there a way to make the priority to open with jdk java6 instead of archive manager.
Thanks

---

### Post by PhantomTurtle on 2012-04-10
> **seal308 said:**
> that works i can now run it.
however it's not like the other native applicaitons.
I don't have it's own icon or anything, it's just a jar file.
Is there a way for it to have it own icon.
Now it's sort of a hassle b/c i have to right click it and click open with jdk.
If i can't make it to an icon is there a way to make the priority to open with jdk java6 instead of archive manager.
Thanks

Right click on the jar file. Click open with other application. Then just select java6. This will make it the default for that file type.

---

### Post by seal308 on 2012-04-11
I do right click and open with java6 but it doesn't set it to default.
It still open to archive manager without right clicking
any suggestions?

---

### Post by PhantomTurtle on 2012-04-11
> **seal308 said:**
> I do right click and open with java6 but it doesn't set it to default.
It still open to archive manager without right clicking
any suggestions?

No, no. You want to click on "open with other application...". This will give you a list of programs to choose from, choose java from that.

---

### Post by JoshuaRL on 2012-04-11
Also in the Properties Dialog box you can click on the not-really-an-icon and change it to whatever icon you have laying around (or have downloaded off of the web).

I did this exact same series of steps to get Minecraft working on my Linux box.

---

### Post by seal308 on 2012-04-11
I right clicked "open with other application" saw the list of applicatioions.
selected java6 it opened fine.
quit dr java.
Double clicked on the icon and it went to archive manager.
Right clicked "open with other applications" again and right clicked archive manager and clicked "forget association"
double clicked the jar file and it still opened with archive manger.
And thanks Josh your advice worked on changing the icon

---

### Post by dniMretsaM on 2012-04-11
You might try writing a .desktop file for it. You can read some info on how to write one [here]("http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/") (it's really easy).

---

### Post by JoshuaRL on 2012-04-13
> **seal308 said:**
> I right clicked "open with other application" saw the list of applicatioions.
selected java6 it opened fine.
quit dr java.
Double clicked on the icon and it went to archive manager.
Right clicked "open with other applications" again and right clicked archive manager and clicked "forget association"
double clicked the jar file and it still opened with archive manger.
And thanks Josh your advice worked on changing the icon

Did you right-click it, go to properties, go to the "Open With" tab, and make Sun Java 6 the default?  That's the way to keep it being opened that way.  Otherwise you'll have to redo it every time.

---

### Post by rpupa on 2012-04-13
right click the file,
click the open with other applications area,
select the java6 or whatever program you would like such extension file to open with in default,
click the checkbox which says make this program default or some similar message,
click ok
and you are done, try double clicking the file and it should open with that application

---

