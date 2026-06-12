---
title: "Running Basket under Unity"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by Garland Fox on 2011-11-17
Newbie here needs to know something:
I am trying out BasKet Notes and having a lot of problems especially with pasted image quality.
Since it is a "KDE" development, should it run ok in a Unity environment?
With Nixnote (old Nevernote), I can import and paste decent images.
But with Basket, I can Shutter or PrintScreen a good image - but it goes poor quality when I paste it into BasKet.
If I start it in terminal then BasKet asks about files in a kde folder...
It can't find...

---

### Post by oldos2er on 2011-11-17
Can you please post the terminal output?

Edit: I've changed the thread title so it won't appear as YAUC (Yet Another Unity Complaint).

---

### Post by Garland Fox on 2011-11-17
Sorry - I'm a newbie and cannot navigate the terminal and copy text.
I get the output on screen but cannot select it and copy to a text file...
Working on it.
Thanks

---

### Post by Garland Fox on 2011-11-17
Here we go - BasKet terminal text:

garland@garlanddellone:~$ basket

(basket:1906): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(basket:1906): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(basket:1906): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(basket:1906): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
basket(1906): ""lastBackup" - conversion of "-4713,1,1" to QDate failed" 
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)

(kdeinit4: kded4 [kdeinit]:1923): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(kdeinit4: kded4 [kdeinit]:1923): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(kdeinit4: kded4 [kdeinit]:1923): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(kdeinit4: kded4 [kdeinit]:1923): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
kbuildsycoca4 running...
kbuildsycoca4(1933) KBuildSycoca::checkTimestamps: checking file timestamps
kbuildsycoca4(1933) KBuildSycoca::checkTimestamps: timestamps check ok
kbuildsycoca4(1933) kdemain: Emitting notifyDatabaseChanged ()

(kglobalaccel:1942): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(kglobalaccel:1942): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(kglobalaccel:1942): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(kglobalaccel:1942): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
QDBusConnection: name 'org.kde.kglobalaccel' had owner '' but we thought it was ':1.139'
basket(1906)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(1906)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(1906)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(1906)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(1906)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(1906)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(1906)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(1906)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(1906)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
basket(1906)/kdeui (K*Gesture*) KAction::setGlobalShortcut: Attempt to set global shortcut for action without objectName(). Read the setGlobalShortcut() documentation. 
garland@garlanddellone:~$ 

That's it.
Thanks.
I can't figure out why pasted object quality is so poor.
I gotta be doing something wrong.

---

### Post by Garland Fox on 2011-11-17
2 items:
1. should I post text output in a box or something?
2. re: BasKet image quality; I was able to play around with a screen grab resolution and size reduction to get a good image. Lot of steps - aggravating.
Thanks

---

### Post by Garland Fox on 2011-11-17
Nope- still not right.
Pasted images will still not display on the note page until the program is closed and re-started.
Acts weird.

---

### Post by oldos2er on 2011-11-17
Not a clue, I'm afraid. If you click the Help menu, Send a Comment to Developers, you can ask them if it's a known bug.

---

### Post by Garland Fox on 2011-11-18
OK thanks much - bye the way how does one unsubscribe from a thread?
I going to mark this one solved for now-thanks

---

### Post by oldos2er on 2011-11-18
Marking the thread 'Solved' without any posted solution isn't the best course of action, since the entire purpose of 'Solved' is to help others who may have the same problem.

If you hear anything back from the developers, please post it here. For now, I'm going to remove the 'Solved' tag.

---

### Post by Garland Fox on 2011-11-18
ok

---

