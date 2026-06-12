---
title: "How to start emerald theme manager?"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by kramer65 on 2008-07-21
Hello,


I want to use an emerald theme and therefore I need to install the emerald theme manager. I must say that the [Emerald website]("http://wiki.opencompositing.org/EmeraldThemeManager") is quite unclear.

It says that I need to install the "Window Decorations plugin (via CCSM)", but how?

It also says I need to start up the Emerald theme manager. Again... How?


I did search around on the merald website and on google, but I really can't find anything. Can anybody help me a little with this?

---

### Post by Ryadt on 2008-07-21
Enter 
```
sudo apt-get install emerald
```
in terminal.

---

### Post by iaculallad on 2008-07-21
> **kramer65 said:**
> Hello,


I want to use an emerald theme and therefore I need to install the emerald theme manager. I must say that the [Emerald website]("http://wiki.opencompositing.org/EmeraldThemeManager") is quite unclear.

It says that I need to install the "Window Decorations plugin (via CCSM)", but how?

It also says I need to start up the Emerald theme manager. Again... How?


I did search around on the merald website and on google, but I really can't find anything. Can anybody help me a little with this?

Press Alt+F2 and input **emerald --replace** then press Enter key. 

To make it load on startup:
Navigate to System->Preferences->Sessions, Press Add, Name the session as **Emerald** and the command equivalent to **emerald --replace**.

---

### Post by kramer65 on 2008-07-21
Allrighty! That already helps a lot!

And how do I open the emerald theme manager?

---

### Post by Ryadt on 2008-07-21
It should be in System > Preferences.

---

### Post by kramer65 on 2008-07-21
Grrrrrrrreat!

Now I see it. I just inserted a [nice theme]("http://www.gnome-look.org/content/show.php/Mac4Lin+ver.0.4+Emerald+Theme?content=71995"), and it affects the window borders. It doesn't affect the top menu bar though..
in fact, none of the themes affects my top bar and bottom bar (of gnome).

Maybe you happen to know this as well?




ps. How can I file a bug in Emerald? When you click "import" it goes to the page /home/username/Desktop. This doesn't work for localised versions like mine which actually says /home/username/Bureaublad...

---

### Post by kramer65 on 2008-07-21
Nobody?

---

### Post by anubis3000bc on 2009-03-19
Im having the same problem in Ubuntu 8.10 i use the terminal to open emerald because it will not open when i bootup into ubuntu so i have to force it.

---

