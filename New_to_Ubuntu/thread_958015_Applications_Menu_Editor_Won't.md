---
title: "Applications Menu Editor Won't"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by wmichaelb on 2008-10-24
Hi, I've been trying to add a category to my Applications Menu on Hardy. 
- If I right-click on Applications and left-click on Edit Menus, I get the dialog box to open. I've been able to create my new category by clicking on New Menu, and filling in the dialog box. Then I click on the "show" box. But the item refuses to show up on the menu. If I reopen the Edit Menu dialog box, the "show" box is unchecked.

- If I open the terminal, and type 

sudo alacarte 

I get the same dialog box. But when I try to add a category, it doesn't show. However, if I revert to Edit Menu, it shows up there!

- If I open the terminal and simply type 

alacarte

I get the same behavior as clicking on Edit Menu.

Does anyone have a suggestion as to what I'm missing?
Thanks!
:confused:

---

### Post by mc4man on 2008-10-24
You need to add something to the new category you created (a menu item) before it will show up as a category in the applications menu.
In other words a category with nothing enabled in it won't show up.

---

### Post by wmichaelb on 2008-10-25
Thanks, mc4man! That worked; I figured it was something basic.

---

