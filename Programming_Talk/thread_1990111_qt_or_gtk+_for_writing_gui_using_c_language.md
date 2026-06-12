---
title: "qt or gtk+ for writing gui using c language?"
date: 2012-05-29
forum: Programming Talk
---

### Post by kkantnaik on 2012-05-29
I have wrote a simple client-server application for sharing files on a LAN network using TCP/IP sockets in C language. Now I want to add GUI to my program and after googling I was introduced to Qt and Gtk+. Since I am new to GUI I want to use any one which is simple and has good tutorials available. I also read somewhere that Qt is for KDE and Gtk+ is for Gnome, so is it possible to use Qt for developing great GUI on Ubuntu 12.04. Please give me some good advice.  :D

---

### Post by etdsbastar on 2012-05-29
My personal vote goes for GTK3, its awesome and you can design with glade interface designer.

Tutorials are also available for download, just google around. Search for text 'Programming with GTK filetype:pdf' and you will get lots of pdf files and book related to gtk programming.[]("https://www.google.co.in/#hl=en&biw=1231&bih=887&sclient=psy-ab&q=filetype:pdf+programming+with+gtk&oq=filetype:pdf+programming+with+gtk&aq=f&aqi=&aql=&gs_l=hp.3...535.17231.0.17410.41.39.2.0.0.8.618.7912.0j25j11j1j0j1.38.0...0.0.hnIflwt0_jc&pbx=1&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.,cf.osb&fp=a98ebc9bb6ce56ee")

---

### Post by PeterP24 on 2012-05-29
My guess is that you will find good tutorials online for both gtk and qt. Both of them are pretty well represented on the web. I only used gtk - I can only say that it is ok and that I can't make a comparison with qt. You've heard that qt is for kde and gtk is for gnome? Well, you can develop qt apps while you are on a gnome desktop environment and viceversa. The only minor stuff is that if you are on a gnome desktop environment and you want to install a kde based app then you will have to pull, besides the app itself, all sorts of kde related dependencies. This is true for the first kde app you install on that computer (which used Gnome desktop environment).

---

### Post by etdsbastar on 2012-05-29
> **PeterP24 said:**
> My guess is that you will find good tutorials online for both gtk and qt. Both of them are pretty well represented on the web. I only used gtk - I can only say that it is ok and that I can't make a comparison with qt. You've heard that qt is for kde and gtk is for gnome? Well, you can develop qt apps while you are on a gnome desktop environment and viceversa. The only minor stuff is that if you are on a gnome desktop environment and you want to install a kde based app then you will have to pull, besides the app itself, all sorts of kde related dependencies. This is true for the first kde app you install on that computer (which used Gnome desktop environment).


Very nice reply Peter.

---

### Post by kkantnaik on 2012-05-29
I will try gtk3 then. By the way are there any significant differences between KDE and Gnome??

---

### Post by kkantnaik on 2012-05-29
Thanks for replies :D

---

### Post by etdsbastar on 2012-05-29
> **kkantnaik said:**
> I will try gtk3 then. By the way are there any significant differences between KDE and Gnome??

Will you please explain, what do you mean by significant differences. GNOME is gnome and KDE is kde, both are different platforms, though base is same LINUX ...

---

### Post by ofnuts on 2012-05-29
> **kkantnaik said:**
> I also read somewhere that Qt is for KDE and Gtk+ is for GnomeNot really... Gnome uses Gtk and KDE uses Qt for their UI, but on most systems you will find both graphics libs used.

See also: [http://www.wikivs.com/wiki/GTK_vs_Qt](http://www.wikivs.com/wiki/GTK_vs_Qt)

---

