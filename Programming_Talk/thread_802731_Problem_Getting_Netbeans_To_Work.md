---
title: "Problem Getting Netbeans To Work"
date: 2008-05-21
forum: Programming Talk
---

### Post by mike_g on 2008-05-21
I just installed netbeans5.5 on a clean ubuntu install. When I first ran it it came up with some errors that i clicked away without reading. The problem is that basically it wont let me load, or create a new, project. I tried reinstalling it and I have the jdk, and jre installed. The problem stayed the same but I cant seem to reproduce the error message. [Heres ](http://i92.photobucket.com/albums/l15/mikegrundel/Screenshot-NewProject.png)a picture of what it looks like when creating a new project; theres no option to create a java application in the right pane. And I cant load a project folder; the browser just opens the folder instead. Does anyone know what could be causing this? I installed netbeans on ubuntu before and I never had this problem :/

---

### Post by SNYP40A1 on 2008-05-22
Probably not the advice that you are looking for, but have you tried Eclipse?

---

### Post by Zugzwang on 2008-05-22
[LIST]
[*]Make sure that you are really using the Sun JDK. Try running netbeans from the shell. ```

java -version
netbeans &

```
[*]Delete the ".netbeans" directory of your user account to kill all settings. Then the error message should appear again.
[/LIST]

---

### Post by mike_g on 2008-05-22
I deleted the .netbeans directory and fired it up. I got the licencing agreement again, but no errors. Seems to work now too; so I'm happy. Cheers.

---

