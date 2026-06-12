---
title: "Add/Remove Applications gone"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by JohnTheMacGeek on 2008-07-08
There was a way to add or remove applications right off of the Applications menu but it is no longer there. Any ideas on how to get it back?

---

### Post by sydbat on 2008-07-08
Right click on the 'Applications' menu > Edit Menus > window pops up > make sure 'Add/Remove...' is checked. Should get it back for you.

---

### Post by ptn107 on 2008-07-08
Make sure the following packages are installed:

app-install-data
gnome-app-install

Now do the following...
1) Right click the gnome menu (up where it says Applications, Places, etc...)
2) Select 'Edit Menus'
3) Click 'Applications' at the top of the left box.
4) Add a new item to the right side by clicking 'New Item'.

Use the following information to fill out the Launcher properties box:
Type: Application
Name: Add/Remove...
Command: /usr/bin/gnome-app-install
Comment: Install and remove applications

You should also add a separator between 'System Tools' and 'Add/Remove...'

---

### Post by JohnTheMacGeek on 2008-07-08
It's there, alright. However, every time I check it, it unchecks it automatically. Also, it is in italics.

---

### Post by sydbat on 2008-07-08
Did you try installing the things ptn107 suggested?

app-install-data
gnome-app-install

After that, it should no longer be in italics.

---

### Post by JohnTheMacGeek on 2008-07-08
> **sydbat said:**
> Did you try installing the things ptn107 suggested?

app-install-data
gnome-app-install

After that, it should no longer be in italics.Yep, that worked! Thanks! Now onto the next issue I'm having.

---

### Post by ptn107 on 2008-07-08
> **JohnTheMacGeek said:**
> Yep, that worked! Thanks! Now onto the next issue I'm having.

...which is?

---

### Post by JohnTheMacGeek on 2008-07-08
> **ptn107 said:**
> ...which is?
[New thread]("http://ubuntuforums.org/showthread.php?t=853311")

---

