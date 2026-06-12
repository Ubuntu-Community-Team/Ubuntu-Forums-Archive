---
title: "Java JPopupMenu - Dispose?"
date: 2009-12-21
forum: Programming Talk
---

### Post by PaulM1985 on 2009-12-21
Hi

I am using a JPopupMenu which opens when a tab on a JTabbedPane is clicked.  This is to give options such as save, save all, close, close all etc.

Generally, when using JFrames, if I don't want the frame anymore I would use the dispose method to remove the frame and release the memory.  In this case, there is no dispose method for a JPopupMenu, but I could use:

setVisible(false);

I have a feeling that this will only hide the popup menu rather than close it and release the memory.  Does anyone know if this is the case?  And if so, is there a way I can "dispose" of this object?

Paul

---

### Post by MrStill on 2009-12-21
Hi Paul,

You are correct in your assumption that the setting a component invisible does not clear it from memory. As for a dispose() method for the popup menu, consider what you are trying to do with the menu.

By clicking an item inside the menu (or even clicking outside of the menu); you want your menu to disappear. But, you want the menu to come back in the proper state when it is activated again. If this menu is opened often, you might not want to give it to the garbage collector (only to initialize it again). The PopupMenu should hide itself after you choose a menu item; and clicking outside of it will probably just cause the menu to move. 

If it is a one time thing, I would assume you can achieve the same outcome by setting the popup menu equal to null. Just remember null pointer exceptions in your action listeners if you choose this.

---

