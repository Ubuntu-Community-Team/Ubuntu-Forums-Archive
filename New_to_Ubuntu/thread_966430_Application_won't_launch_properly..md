---
title: "Application won't launch properly."
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Aspras on 2008-11-01
Hello I am having a problem with an application listed in the Applications>Wine menu called Browse C:\ Drive, when I run it through that menu it doesnt do anything, though when I execute its command through the terminal it works normally. Any suggestions?

---

### Post by cozmicharlie on 2008-11-01
Check the menu item.  Go to the Applications menu and right click>Edit menus>on the Application item, right click>properties and under Type there is a scroll down menu that gives you the option to "run the application in terminal" then close out.  Now your app should start in the terminal.

Enjoy

---

### Post by Aspras on 2008-11-01
I tried that already, when i do that and run it I see a window that opens up and then closes in an instant.

---

### Post by Bodsda on 2008-11-01
That behavior is when a command has run and finished successfully, check the command is exactly the same as the one your typing into the terminal

---

### Post by Aspras on 2008-11-01
Thats where I got the command from , i drag n dropped the application into my desktop , right clicked and went into properties.

---

### Post by Aspras on 2008-11-01
Problem solved. The launcher was using the command nautilus ~/.wine/drive_c , I changed the ~/ into /home/paul/.wine/drive_c which now works.

(I noticed that when the launcher was executing the command with "~/", it put a "/home/paul/" in front of  "~/" by itself so it ended up executing "nautilus /home/paul/~/.wine/drive_c" and I really have no idea why that is happening)

---

