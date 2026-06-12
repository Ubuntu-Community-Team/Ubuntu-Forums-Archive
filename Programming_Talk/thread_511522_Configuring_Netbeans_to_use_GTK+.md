---
title: "Configuring Netbeans to use GTK+"
date: 2007-07-27
forum: Programming Talk
---

### Post by ladida on 2007-07-27
Hey guys... newbie here.

I'm trying to get Netbeans 5.5 to work with GTK+. When I use "#include <gtk/gtk.h>" it couldn't find gtk.h.

I realise that I have to configure my include paths, so I tried adding the path "/usr/include/gtk-2.0" but it didn't work either. The weird thing is, when I use "#include <gtk-2.0/gtk/gtk.h>" it DID find gtk.h, but it couldn't find everything else because gtk.h lists the rest of the header files.

Oh and btw, I think I also need to include library files, but I have no idea how.

Does anyone know how I should configure this? Thanks a lot.

---

### Post by leinuz.basher on 2007-07-29
Hello,

   Why do you want to Make a GTK+ Netbeans? 
   
   It works in Java why need GTK+?

---

### Post by kknd on 2007-07-29
> **ladida said:**
> Hey guys... newbie here.

I'm trying to get Netbeans 5.5 to work with GTK+. When I use "#include <gtk/gtk.h>" it couldn't find gtk.h.

I realise that I have to configure my include paths, so I tried adding the path "/usr/include/gtk-2.0" but it didn't work either. The weird thing is, when I use "#include <gtk-2.0/gtk/gtk.h>" it DID find gtk.h, but it couldn't find everything else because gtk.h lists the rest of the header files.

Oh and btw, I think I also need to include library files, but I have no idea how.

Does anyone know how I should configure this? Thanks a lot.

Do you have libgtk-dev installed? You need to add both the includes and the compiled libraries in the project optioins (I presume that you are using Netbeans with Cpp pack).

---

### Post by Frankie6502 on 2008-02-28
Hi! I had the same problem and after lots of digging around I found this excellent guide as to using GTK+ with NetBeans.

[http://zetcode.com/articles/netbeanscdevelopment/]("http://zetcode.com/articles/netbeanscdevelopment/")

Hope this helps you and anyone else having the same problem.

;)

---

### Post by newbiezz on 2009-04-12
I also found [http://pitchover.wordpress.com/2009/04/10/building-gtk-apps-under-windows-with-mingw-part-3/]("http://pitchover.wordpress.com/2009/04/10/building-gtk-apps-under-windows-with-mingw-part-3/") should work with either Windows and Linux. ;)

---

### Post by faical117 on 2009-12-25
thanks :-)

---

### Post by arnie001 on 2010-07-08
Thank you [Frankie6502]("http://ubuntuforums.org/member.php?u=170372"). It works.

---

### Post by Fabioamd87 on 2010-11-09
I have this error:

---

### Post by Fabioamd87 on 2010-11-10
I've included every single directory and now I have this:

---

### Post by wkhasintha on 2010-11-11
thanx frankie , that was helpful for me too

---

