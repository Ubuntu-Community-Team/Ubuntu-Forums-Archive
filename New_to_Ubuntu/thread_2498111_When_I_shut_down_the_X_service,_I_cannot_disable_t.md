---
title: "When I shut down the X service, I cannot disable the system's automatic sleep mode."
date: 2024-05-30
forum: New to Ubuntu
---

### Post by louie77777 on 2024-05-30
I am using Ubuntu 20.04. I modified the path in the /usr/share/xsession/ubuntu.desktop file to point to my application's executable. After restarting Ubuntu, my application starts instead of the desktop environment. However, I noticed that if I don't use the keyboard or mouse for 10 minutes, the system automatically goes into sleep mode. I have tried several methods to resolve this issue but have not been successful. I am seeking help from anyone who can assist me.

---

### Post by currentshaft on 2024-05-31
It would help to know what are the methods you'd already tried.

How about running "gnome-control-center" from the terminal and checking the Power section?

---

### Post by louie77777 on 2024-05-31
gnome-control-center cannot be used because I currently do not have a graphical interface.

---

### Post by currentshaft on 2024-05-31
D1

---

### Post by &amp;KyT$0P# on 2024-05-31
> **louie77777 said:**
> I have tried several methods to resolve this issue but have not been successful. 

What "several methods" did you try?

> **louie77777 said:**
> I currently do not have a graphical interface.

Did you try setting [FONT=monospace]consoleblank=0[/FONT] boot parameter?

---

