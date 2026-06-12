---
title: "Questions from a first time Ubuntu User"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by JoyceBabu on 2008-05-02
I was a windows user who decided to switch to Ubuntu. Can someone plz clarify the following doubts for me?
1. Which is the Ubuntu Counter part of Windows Task Manager and what is the Hot key combination for that?
2. Which is the best file manager program for Linux? I am not comfortable with Nautilus. I want a program with a editable address/location bar.
3. Which is the best FTP client for Ubuntu?
4. I have installed Cairo Dock. Is it possible to hide/remove the default task bar?
5. Is it possible to set a hot key for Gnome Do? Currently I have to launch it from the Applications > Accessories menu, every time I need it. And I can't find any preference/settings/options page.

---

### Post by Michael.Godawski on 2008-05-02
as a side note: there is no best, there is only a best for you
1. the terminal command ```
top
```
and the System Monitor
3. gftp is not bad

---

### Post by monkeymoo on 2008-05-02
> **JoyceBabu said:**
> 
2. Which is the best file manager program for Linux? I am not comfortable with Nautilus. I want a program with a editable address/location bar.

Nautilus does have an editable address/location bar. If you don't see it you can go to View -> Location Bar to turn it on. If you are seeing a row of boxes with folder names on instead of the address line, click the button on the far left of the location bar to change it to the address line.

---

### Post by billgoldberg on 2008-05-02
> **JoyceBabu said:**
> I was a windows user who decided to switch to Ubuntu. Can someone plz clarify the following doubts for me?
1. Which is the Ubuntu Counter part of Windows Task Manager and what is the Hot key combination for that?
2. Which is the best file manager program for Linux? I am not comfortable with Nautilus. I want a program with a editable address/location bar.
3. Which is the best FTP client for Ubuntu?
4. I have installed Cairo Dock. Is it possible to hide/remove the default task bar?
5. Is it possible to set a hot key for Gnome Do? Currently I have to launch it from the Applications > Accessories menu, every time I need it. And I can't find any preference/settings/options page.

1. "system monitor" I don't know what the short cut is, but it's under "system -> administration.

2. Nautilus has a editable address bar. You'll need to press the little icon on the top left under the "back" key to open it. If you opened it once, it will always remain open, unless you close it.

But there are other file manager: thunar, pcman, ...

3. Don't know, I used to use fireftp in firefox, but that's some months ago. There is gftp, filezilla, you can use nautilus, and offcourse the terminal. There are loads of others (look through add/remove).

4. Don't use docks.

5. ?

---

### Post by JoyceBabu on 2008-05-02
```
top
```
I prefer GUI :)
Can you plz tell me whether there is any hotkey combination for System Monitor or not? Can I set one myself?

---

### Post by meindian523 on 2008-05-02
> **JoyceBabu said:**
> I was a windows user who decided to switch to Ubuntu. Can someone plz clarify the following doubts for me?
1. Which is the Ubuntu Counter part of Windows Task Manager and what is the Hot key combination for that?
System Monitor
> 2. Which is the best file manager program for Linux? I am not comfortable with Nautilus. I want a program with a editable address/location bar.
You can do that in Nautilus itself.Just click the page+pencil icon next to the <current folder> icon.
> 4. I have installed Cairo Dock. Is it possible to hide/remove the default task bar?
Right click the panel,select delete panel.
> 5. Is it possible to set a hot key for Gnome Do? Currently I have to launch it from the Applications > Accessories menu, every time I need it. And I can't find any preference/settings/options page.
Try adding it to a drawer on your panel.Right click your panel,select Add panel and then drawer.Add whatever apps you use most frequently.

EDIT:You can add system monitor to your drawer too.

---

### Post by JoyceBabu on 2008-05-02
> **monkeymoo said:**
> Nautilus does have an editable address/location bar. If you don't see it you can go to View -> Location Bar to turn it on. If you are seeing a row of boxes with folder names on instead of the address line, click the button on the far left of the location bar to change it to the address line.
Thanks. I found that. 

> **billgoldberg said:**
> 
4. Don't use docks.
Can you plz tell me why?

---

### Post by meindian523 on 2008-05-02
bill probably thinks they're unnecessary eyecandy which chew up resources.:)

---

### Post by sujoy on 2008-05-02
i mostly use gftp for my transfers, its simple and good as for the rest, i couldn't find gnome do, so dont know what you are talking about, the default taskbar can be deleted, go to system-preference-sessions, go to current session, select gnome-panel and click on remove, now go to session options and click on remember and check automatically save.

---

### Post by linuxlizard on 2008-05-02
for ftp, I use gftp. (grab it from system-administration-synaptic package manager)

system-administration-system monitor = windows task manager

system-preferences-keyboard shortcuts lets you set hot keys for anything you want

---

### Post by eriqjaffe on 2008-05-02
Whatever Gnome Do is, you should be able to set up a keybinding for it:

[http://www.linuxformat.co.uk/wiki/index.php/Setting_Key_Bindings_in_GNOME](http://www.linuxformat.co.uk/wiki/index.php/Setting_Key_Bindings_in_GNOME)

---

### Post by JoyceBabu on 2008-05-02
Can someone plz tell me the terminal command for starting up System Monitor. I tried system-monitor, but it didnt' work

---

### Post by oldos2er on 2008-05-02
> **JoyceBabu said:**
> Can someone plz tell me the terminal command for starting up System Monitor. I tried system-monitor, but it didnt' work

 It's gnome-system-monitor (found this in the Help file).

---

### Post by jken146 on 2008-05-02
GnomeDo: [https://wiki.ubuntu.com/GnomeDo/Use](https://wiki.ubuntu.com/GnomeDo/Use)

---

### Post by JoyceBabu on 2008-05-03
Thanks to all.

I added gnome-do to startup using Preferences > Session
and changed the Key binding to Ctrl + Space. Previously it was Super + Space, and I was trying Ctrl + Space, that was why it wasn't working.

---

