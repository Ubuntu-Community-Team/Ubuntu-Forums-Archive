---
title: "[SOLVED] Problems With Shut Down In 8.04"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by pdlethbridge on 2008-06-04
I noticed a change between 7.10 and 8.04. When I shut down, and sometimes when I start up, I have command lines showing up. How can I eliminate this and just have the Ubuntu screen and radio bar?

---

### Post by kaibob on 2008-06-04
> **pdlethbridge said:**
> I noticed a change between 7.10 and 8.04. When I shut down, and sometimes when I start up, I have command lines showing up. How can I eliminate this and just have the Ubuntu screen and radio bar?

That is a somewhat common problem, although it appears to have multiple causes. You might want to try the fix detailed in post 13 of the following thread:

[http://ubuntuforums.org/showthread.php?t=772733](http://ubuntuforums.org/showthread.php?t=772733)

---

### Post by iaculallad on 2008-06-04
*For Graphical Shutdown
-Navigate to System->Administration->Login Window
-Select "General" tab, click on "Edit commands ... button,
-"Command type" should be "Halt command"

+Copy and Paste the bold text below (Do not Remove anything)

-"Path" should be **/sbin/shutdown -h now "Shut Down via gdm."**

*For Graphical Reboot
-Navigate to System->Administration->Login Window
-Select "General" tab, click on "Edit commands ... button,
-"Command type" should be "Reboot command"

+Copy and Paste the bold text below (Do not Remove anything)

-"Path" should be **/sbin/shutdown -r now "Shut Down via gdm."**

Do NOT forget to click on the "Apply Command Changes" button and click on close.

---

### Post by pdlethbridge on 2008-06-05
tried your suggestions and it is fixed. Thanks Paul

---

