---
title: "[SOLVED] The Comprehensive Debian Menu"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Alan Coleman on 2008-07-05
Sometimes we install software and it dose not automatically appear in the applications menu. I installed the software but where did it go? The answer to this is apparently to install The Debian menu. Unfortunately the name is somewhat obscure and it is not so well documented. Dose anyone know the name of this package? many thanks for reading.
ac

---

### Post by bumanie on 2008-07-05
Is this what you mean? 
generates programs menu for all menu-aware applications
Debian menu keeps transparently the menus in the different
window-managers in sync with the list of installed programs.

Debian menu relies on a list of menu entries provided by programs
and a list of menu-methods provided by window-managers and other
menu-aware applications.

It should be installed by default I think.Look under synaptic package manager. I typed in 'debian menu' and this is what appeared about half-way down.

---

### Post by alienexplorers on 2008-07-05
For the Debian Menu you need to install:
> menu
menu-xdg

---

### Post by Anzan on 2008-07-05
Yes, and then enable it in Edit Menus.

---

### Post by Alan Coleman on 2008-07-05
Thanks alienexplorers. That worked a treat. I love it when it works!
Now if I new how I would mark this thread as closed. Is that what you are ment to do and how do you do it.

---

### Post by Alan Coleman on 2008-07-06
Ok so I ran into some trouble where I found my computer would only boot to a command prompt (like the terminal) Xwindows would start if I logged in and typed startx, however this wasnt good enough so I reinstalled.
 Several hours later I tried to install my new found menu-xdg (debian menu) and while it appears in the 'edit menu' section that you can pull up by right clicking on the menu's at the top and selecting edit menu,  when I tick the box it will not work! got that?

So why is this? my only feeling is that it could be conflicting with something I have installed today. 

as far fixing it goes -im a bit stuck.

thanks for reading.

---

### Post by Vivaldi Gloria on 2008-07-06
> **Alan Coleman said:**
>  and while it appears in the 'edit menu' section that you can pull up by right clicking on the menu's at the top and selecting edit menu,  when I tick the box it will not work! got that?

If a menu is empty then it won't appear even if you tick the box.

---

### Post by Alan Coleman on 2008-07-07
Thanks for replying. I think the idea of this menu is that it shows you what you have. So any ideas why the programs are not appearing in it automatically like I would expect? That is what is supposed to happen.

thanks 
ac

---

### Post by Vivaldi Gloria on 2008-07-07
> **Alan Coleman said:**
> Thanks for replying. I think the idea of this menu is that it shows you what you have. So any ideas why the programs are not appearing in it automatically like I would expect? That is what is supposed to happen.

thanks 
ac

I don't know about the debian menu but I think the debian menu is no different than the others. 

Still, even if it worked like the way you wanted then it may not show all the applications because it's the packages which decide if there'll be a menu item. If the writer of the package has not included itself to be included in

```
/usr/share/applications
```

and/or

```
/usr/share/menu
```

then how can the system know what to add to the menu? If a package does not add itself then you'll have to add it by hand.

Start synaptic, right click a package (say abiword-common) and select the properties. For abiword-common the following lines are included:

```
...
/usr/share/application-registry
/usr/share/application-registry/abiword.applications
/usr/share/applications
/usr/share/applications/abiword.desktop
...
/usr/share/icons
...
/usr/share/menu
/usr/share/menu/abiword-common
...
```

So you see that the abiword-common package adds itself to menu. Some packages don't. To sum it up, it's package creator's choice whether an icon is added or not.

---

### Post by zvacet on 2008-07-07
```
sudo apt-get install menu menu-xdg
```
```
sudo dpkg-reconfigure menu  
```
```
sudo dpkg-reconfigure menu-xdg
```

---

### Post by kansasnoob on 2008-07-07
"I installed it, but where did my program go?"

[http://monkeyblog.org/ubuntu/installing/#where_did_it_go](http://monkeyblog.org/ubuntu/installing/#where_did_it_go)

Or be specific when asking here.

There are usually at least two ways of doing everything in Ubuntu.

---

### Post by kansasnoob on 2008-07-07
"Unfortunately the name is somewhat obscure and it is not so well documented. Dose anyone know the name of this package? many thanks for reading."

Actually how could we know what package we're looking for with that description?

Did I miss something?

---

### Post by Vivaldi Gloria on 2008-07-07
> **zvacet said:**
> ```
sudo apt-get install menu menu-xdg
```
```
sudo dpkg-reconfigure menu  
```
```
sudo dpkg-reconfigure menu-xdg
```

Does these commands preserve the menu items I added myself?

---

### Post by Alan Coleman on 2008-07-08
Thanks all.

 Didn't understand the answers, but that didn't matter because they worked! Its fortunate you don't have to understand code very well to use it. The answer by zvacet did the trick and I now have a menu listing the applications I have installed. I also know how to enable it if it doesn't confiner itself when installing.

Is it up to us to mark a thread closed or dose the forum do this automatically?

---

### Post by sydbat on 2008-07-08
You have to mark it closed. It's under "Thread Tools" at the top of the page.

---

