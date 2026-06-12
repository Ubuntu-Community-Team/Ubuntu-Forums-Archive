---
title: "[SOLVED] choose application file"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by lepban on 2008-10-14
Hey i was just wondering, does ubuntu have an application executable sort of thing?  Windows has .exe and apple has .app.  How do you choose an application in the AWN custom launcher for example?

---

### Post by iaculallad on 2008-10-14
> **lepban said:**
> Hey i was just wondering, does ubuntu have an application executable sort of thing?  Windows has .exe and apple has .app.  How do you choose an application in the AWN custom launcher for example?

You can create a launcher and point it to the application/script name you want to launch when clicked.

---

### Post by ajmorris on 2008-10-14
> **lepban said:**
> Hey i was just wondering, does ubuntu have an application executable sort of thing? Windows has .exe and apple has .app. How do you choose an application in the AWN custom launcher for example?
 
 
Linux does not use application extensions for executables. Instead it uses either binary files, or scripts (bash and sh are the most common) which contain an "execute flag" for execution. For custom launchers in AWN, you can add the target of the launcher to one of these executable (most applications will have a launcher in one of /usr/bin, /sbin or /usr/sbin) You can also find out how your menu launches applications, by looking at the relevant .desktop files in /usr/share/applications.
 
 
AJ

---

### Post by lepban on 2008-10-14
It would be really convenient if all installed programs made a link to an application folder, i think it would be alot easier than making a ton of links yourself.  Especially for migrating mac and pc users.

---

### Post by ajmorris on 2008-10-14
> **lepban said:**
> It would be really convenient if all installed programs made a link to an application folder, i think it would be alot easier than making a ton of links yourself. Especially for migrating mac and pc users.
 
They do, [quote=ajmorris]most applications will have a launcher in one of /usr/bin, /sbin or /usr/sbin[/quote]
apt will automatically install the binary/script to one of these locations, which are in your Ubuntu PATH environment variable by default. As well as these, a .desktop file is placed in /usr/share/applications for the application to be automagically added to your menus.
 
If you compile and application by source, most upstream developers will have created a binary/script for these also, it depends where they are installed however, by your --prefix paramater on the ./configure step/
 
AJ

---

### Post by lepban on 2008-10-15
Thank you very much that's really helpful.

---

