---
title: "How do I Program a GUI"
date: 2011-02-05
forum: Programming Talk
---

### Post by Lord_Flick on 2011-02-05
I'm using Ubuntu Netbook Remix on an asus AT5IONT-I with a 500gb hd 

I'm a networking student who only knows about programing routers

What would I do if i wanted to create a simple interface that has the following options with basic icons

-Web
-Tools
-Media
-Games 
-Trash 
-log off (so I can log on as administrator and use the standard gnome gui)

Sort of like this

Thanks you for whatever help you can give :guitar:

---

### Post by lisati on 2011-02-05
*Thread moved to **Programming Talk**.*

---

### Post by MrStill on 2011-02-06
The answer to this question would change depending on the context in which you will be using your GUI. 

For UNR/GNOME, most programming languages have GTK packages that you could use. I am unaware of any drag and drop style IDEs that would help you design a GUI with these packages. But, Python is easy enough and there are plenty of GTK examples on the web.

Java swing is almost easy and Netbeans has a drag and drop style design editor.

---

### Post by Tony Flury on 2011-02-06
> **Lord_Flick said:**
> I'm using Ubuntu Netbook Remix on an asus AT5IONT-I with a 500gb hd 

I'm a networking student who only knows about programing routers

What would I do if i wanted to create a simple interface that has the following options with basic icons

-Web
-Tools
-Media
-Games o
-Trash 
-log off (so I can log on as administrator and use the standard gnome gui)

Sort of like this

Thanks you for whatever help you can give :guitar:

what do you mean - "Log on as administrator" ?

---

### Post by Ferrat on 2011-02-06
> **Tony Flury said:**
> what do you mean - "Log on as administrator" ?

I'm guessing he wants to make a basic GUI layer on-top of X or Gnome or something like that for other users, so they can only access the programs via the icons his GUI provides but want one button that lets you start a "normal" gnome desktop as "admin" for easier maintenance etc.

Just a guess that this is what he means.

---

### Post by forrestcupp on 2011-02-06
Sounds like you want to try to program your own light weight Desktop Environment or shell without having any programming experience.

---

### Post by cgroza on 2011-02-06
You need to learn a GUI toolkit, like wxWidgets, GTK, Qt and others.

---

### Post by juancarlospaco on 2011-02-06
You have to do:

```
enable
configure terminal
erase startup-config
reload
```

:D Just kidding, your best bet is to** learn Python**, 
dont stay too much on cli apps and use a simple gui toolkit/framework.

Try with Tkinter and WxWidgets for Desktop, and Web2Py and FrontWeb for Web.

Dont waste time with dinosaurs that say you need to learn assembly and C and use QT 8.3 or higher, those are complex tools for complex apps.
*Im CCNA, too*

---

### Post by Lord_Flick on 2011-02-08
Looks like I have some interesting work to get to!

Thank you all for your help: Lord_Flick

---

