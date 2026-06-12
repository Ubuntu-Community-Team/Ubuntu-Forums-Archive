---
title: "can uninstall KDevelop"
date: 2007-02-17
forum: Programming Talk
---

### Post by yvinogradov on 2007-02-17
So I installed a bunch of KDevelop tools for programming when I couldn't figure out how to make gvim and g++ work for me, Now that I have them working fine I don't need all those KDevelop but I  don't seem to be able to remove the links. I remove the programs but the menu items under Applicatoins->Programming stay. When I click them they say "can't find the program' which makes sense since I remoed them, but how do I make those menu items go away?

Thanks.

---

### Post by j_g on 2007-02-17
Will this work?

Select the "System -> Preferences -> Menu layout" menu item. This brings up the "Menu layout" dialog.

Navigate the listboxes until you see the menu item you want to delete.  Move the mouse pointer over it, and click the right mouse button. This presents a pop-up menu for that item. In that popup menu, you should see a "Delete" command. Select this to delete your unwanted menu item.

Repeat this for other items you wish to delete.

Oh yeah, I should mention that it seems you need to log out, and then log back in, to see the change happen to your Applications menu.

---

### Post by yvinogradov on 2007-02-18
Thanks, that worked. But why didn't those menu items got deleted when I uninstalled the applications? A possible bug?

---

### Post by j_g on 2007-02-19
It has much to do with the fact that a typical Linux system is made up of a whole lot of things, many of which aren't so well integrated. It's this lack of integration that causes various inconsistencies and "odd behavior".

You look at your desktop and you just see some menus and windows. But beneath that facade is a whole lot of separate entities, some of which are essentially achieving the same result, but in different, inconsistent ways. For example, a program could be creating its window using libraries based around GDK (Gtk+, Gtkmm, Glade). Or, it could be creating its window using libraries based around QT. Or, it could be using Motif. Or it could be using a plain X window, which is the lowest level that all of the other UI libraries run atop of.

In your case, you've got a Gnome (GDK-based) desktop. The Gnome window manager is the one creating/maintaining that menu you see where your Applications are listed. This means that GDK-based (Gnome) apps are going to be better integrated with your desktop than apps written with other UI toolkits, such as QT, Motif, or X Windows apps. KDevelop is a QT-based app. Although it "runs" on a Gnome desktop (ie, works with the Gnome window manager), it doesn't really "register" nor directly communicate with the underlying Gnome components, particularly the Gnome components that store "configuration data". This QT app may be storing its configuration using some QT based component that keeps the configuration data in an entirely different place than Gnome does. That's why sometimes QT apps don't seem to retain/maintain/update their "configuration" as well as Gnome apps do, under a Gnome desktop.

The opposite could also be true. If you were using the KDE (QT-based) window manager, such as Kbuntu uses for its desktop, then you may see that your GDK-based (Gnome) apps don't seem as well-integrated with the desktop as QT-based apps.

Suffice it to say that, since you're using Gnome, give preference to GDK/Gtk+/Glade/Gtkmm apps. Avoid QT, Motif (Lestif), Xaw, Xt, etc, apps if you want to avoid any inconsistencies and odd behavior. These other apps _will_ run under Gnome. But it's just that you may not experience the same level of integration as with GDK-based apps.

---

