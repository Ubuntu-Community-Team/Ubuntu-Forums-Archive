---
title: "Google gadgets sidebar?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-06-11
Whats the command to get Google gadgets to start with the sidebar?

---

### Post by aktiwers on 2008-06-11
Download it here:
[http://www.getdeb.net/app/Google+Gadgets](http://www.getdeb.net/app/Google+Gadgets)

It will be installed in Applications => Accessories => Google Gadgets

---

### Post by kamitsukai on 2008-06-11
> **aktiwers said:**
> Download it here:
[http://www.getdeb.net/app/Google+Gadgets](http://www.getdeb.net/app/Google+Gadgets)

It will be installed in Applications => Accessories => Google Gadgets

lol i know where to get it from but i want it to start _with_ the sidebar when i login

---

### Post by Inxsible on 2008-06-11
> **kamitsukai said:**
> lol i know where to get it from but i want it to start _with_ the sidebar when i loginYou need to add it to your Startup Programs

I have not used Ubuntu in quite a while, but IIRC, its under System>>Preferences>>Sessions.

If you don't know the command to start it, it would most likely be under /usr/bin. But you can do this to find out. 
1) Drag and drop the menu item for Google Gadgets from Applications>>Accessories to the Desktop. 
2) You will get a launcher on the desktop. Now right click the desktop launcher and select properties. 
3) One of the items will tell you the command. 
4) You can use the same command when putting it under Sessions>>startup.

---

### Post by aktiwers on 2008-06-11
Heh sorry..  yeah then add a it to your sessions like Inxsible said.

The command to run it is:```
ggl-gtk
```

---

### Post by kamitsukai on 2008-06-11
so how do i start with the sidebar?

---

### Post by Inxsible on 2008-06-11
> **kamitsukai said:**
> yes i know that but i want to start it [SIZE=5]_WITH_ THE SIDEBAR[/SIZE] i just want to know the command that i needThere is really no need to shout...give someone time to type the damn answer in. Patience is a virtue. Read my above post to get your command

---

### Post by kamitsukai on 2008-06-11
> **Inxsible said:**
> There is really no need to shout...give someone time to type the damn answer in. Patience is a virtue. Read my above post to get your command

i changed it after i realized that "aktiwers" had posted the answer and i wasn't shouting i was emphasizing the "with" because no one seemed to read my post thoroughly but no worrys i've worked out that the command is 

```
ggl-gtk -s
```

Thank you aktiwers for you post:KS

---

