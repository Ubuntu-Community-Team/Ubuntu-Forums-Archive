---
title: "netbeans gui designer"
date: 2008-11-11
forum: Programming Talk
---

### Post by Revvion on 2008-11-11
Oke so I am using netbeans to create a java applet. When i design the applet in netbeans with the gui desigener i see it with my system theme. However when running the applet you just see it with the default metal theme, now my question is how do i change the look in the netbeans gui designer so it also displays it with the metal theme.

---

### Post by loell on 2008-11-11
if i'm not mistaken java applets do not inherit desktop environment themes on any platform. it has always been that dull silver/grey look.

---

### Post by tinny on 2008-11-12
> **Revvion said:**
> Oke so I am using netbeans to create a java applet. When i design the applet in netbeans with the gui desigener i see it with my system theme. However when running the applet you just see it with the default metal theme, now my question is how do i change the look in the netbeans gui designer so it also displays it with the metal theme.

Java applets just leverage off Swing. I would suggest you look into swing look and feels.

To give your swing applications a "native" look and feel set the look and feel like so before initializing your UI (maybe in your main method)
[PHP]
UIManager.setLookAndFeel(UIManager.getSystemLookAndFeelClassName());
[/PHP]

---

