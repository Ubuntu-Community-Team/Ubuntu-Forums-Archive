---
title: "Keyboard Woes"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Pyrophorus on 2008-06-20
I have a MS Natural KB, and shift-2 gives you double quotes, instead of the at symbol, and the question mark slash key gives an é.

I have tried different layouts, and I can seem to find the right layout, for
this keyboard.

---

### Post by iaculallad on 2008-06-20
System->Preferences->Keyboard, under the "Layouts" tab, choose **Generic 105-key (Intl) PC** as your "Keyboard Model:". Selected layout should be **U.S English**.

---

### Post by Pyrophorus on 2008-06-20
Did not work :(

Generic Keyboard
USA was selected and default.

---

### Post by cariboo on 2008-06-20
You may have to logout and then log back in again for your keyboard change to take place.

---

### Post by Pyrophorus on 2008-06-21
> **cariboo907 said:**
> You may have to logout and then log back in again for your keyboard change to take place.

No Luck with that either

It might just have to be trial and error

---

### Post by iaculallad on 2008-06-21
Using your terminal, try to execute **sudo dpkg-reconfigure xserver-xorg** to reset your keyboard layout.

---

### Post by Pyrophorus on 2008-06-23
That didn't work

in that I did reset the deafault to US, and used the Generic Super Multi-Media KB, and everything worked fine!

Thanks for all the help.

---

