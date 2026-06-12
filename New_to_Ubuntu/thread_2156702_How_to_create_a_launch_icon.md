---
title: "How to create a launch icon ?"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by Innernet on 2013-06-22
Hi.
Running 12.04 with Gnome.
I did it on a previous version, now cannot.

At Applications -> System tools -> **System Monitor**.

How to put its launch icon at the very top of the screen ?

---

### Post by monkeybrain2012 on 2013-06-22
Copy the .desktop file from  /usr/share/applications to the desktop.

```
cd /usr/share/applications
sudo cp xxxx.desktop  Desktop
sudo chown username Desktop/xxxx.desktop
```

It should already be executable, but if not, just right click and change the permission.

But why would you want to clutter the desktop with icons like in Windows? If you use gnome shell you can display all the icons at once or your most commonly use applications by just going to the "applications" corner (in 12.04 or the applications tab in later gnome shell) It is kind of like having ALL icons on your desktop when you need them but out of the way when you don't. That seems to be the whole point of the design. :)

---

### Post by Innernet on 2013-06-22
Thanks.
Perhaps I was not clear...  I prefer the 'System Monitor' launch icon at the very top; on the same line where 'Applications' and 'Places' is, whatever that 'bar' is called.

Edited:  Solved by futzing around.
At Applications -> System tools -> Grabbed the 'System monitor' icon and dragged to where I wanted.  Done.

---

### Post by BNZBKK on 2013-06-22
> **Innernet said:**
>  .....
Edited:  Solved by futzing around.
At Applications -> System tools -> **Grabbed the** 'System monitor'** icon and dragged to where I wanted.  Done**.



 AHA ! done -  Thanks Innernet you genius 





And 'monkeybrain2012' you're correct that's why like Gnome 'Applications' - everything is there, much easier than Unity but I only need one frequently used icon up there for 'one click' convenience

---

### Post by monkeybrain2012 on 2013-06-22
> **BNZBKK said:**
> 





And 'monkeybrain2012' you're correct that's why like Gnome 'Applications' - everything is there, much easier than Unity but I only need one frequently used icon up there for 'one click' convenience

You can do the same with Unity by bringing up the dash (press the 'super' key)

---

### Post by BNZBKK on 2013-06-22
Ahhh  ...now, how to remove an icon from the titlebar ?

---

