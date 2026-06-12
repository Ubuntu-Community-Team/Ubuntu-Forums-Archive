---
title: "Placing Trash bin on desktop..."
date: 2008-07-01
forum: New to Ubuntu
---

### Post by hamishnz08 on 2008-07-01
Hi There,

Just changed over to Ubuntu (bye bye bill),

and but how do I get the trash bin onto the desktop ?

thankyou so much:D

---

### Post by Elfy on 2008-07-01
Alt+F2 and run gconf-editor

Navigate to apps>nautilus>desktop - there is an option to have trash on desktop

---

### Post by Bubba64 on 2008-07-01
Install Ubuntu tweak from launch pad and this will make this easy and a lot of other things.
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)
If you install the launchpad repository you can save time by trying to intall a targz. :D

---

### Post by llama320 on 2008-07-01
the only way i know how to do it is to go into gconf-editor, though there may be an easier way. So do this:

1) Alt+F2
2) type gconf-editor
3) go to apps > nautilus > desktop
4) Click the checkbox for trash_icon_visible

And there you have it

Good Luck

Edit: sorry to be repetitive..forestpixie beat me to it :)

---

### Post by iaculallad on 2008-07-01
Press Alt+F2, enter the string "gconf-editor" (w/o double quote) and press Enter key.

Navigate to Aps->Nautilus->Desktop, and **place a check mark** on **trash_icon_visible** option on the right-side of the window. Close your configuration editor.

---

### Post by llama320 on 2008-07-01
wow we all really want to help
yay for fast response times

---

### Post by hamishnz08 on 2008-07-01
That works perfect...thanks so much :)

---

### Post by Elfy on 2008-07-01
Marking threads as solved can work wonders to  :D

---

