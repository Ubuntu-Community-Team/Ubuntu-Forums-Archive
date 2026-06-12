---
title: "How delay Service startup?"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by DrAlbert on 2012-06-11
Hi
I removed the splash and quiet from kernel parameters and I saw some service related to virtual box starts at startup. I don't use virtualbox every day so I want to be able to start the service when I need (like "services" application in windows) or atleast I could delay some services.

---

### Post by black veils on 2012-06-11
try installing **bum** (boot-up manager), and see if you can change what you want there, it is for managing services.

---

### Post by greenpeace on 2012-06-11
Firstly, try searching for "startup applications" in the Unity dash and check that the checkbox isn't selected for the application.

If you can't see it there... you can go to the commandline, and use the **chkconfig** command to check what is set to autostart, and then stop them:

[http://askubuntu.com/questions/25713/how-to-stop-postgres-from-autostarting-during-start-up](http://askubuntu.com/questions/25713/how-to-stop-postgres-from-autostarting-during-start-up)

That example is for postgresql, but the principle is the same for other applications that auto start on boot.

hope that helps!

---

### Post by DrAlbert on 2012-06-12
thank for reply!
i saw bum and chkconfig and I saw that we can enable or disable starting the services by those commands. but they cant delay a service like that we can do in windows. am I right?

---

