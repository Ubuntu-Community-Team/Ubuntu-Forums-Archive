---
title: "Unable to Remove fonts"
date: 2012-01-06
forum: New to Ubuntu
---

### Post by MUK3SH on 2012-01-06
I have downloaded some fonts from various sites and installed them from The Option In The Fonts...

Now i want to remove some of them But i am unable to find Option To remove the fonts .. 
I have visited on  
/usr/shared/fonts 
But the fonts are not there.. :(
I have searched whole computer But unable to find where they are installed...
](*,)

---

### Post by coffeecat on 2012-01-06
Not quite sure what you mean by this:

> **MUK3SH said:**
>  and installed them from The Option In The Fonts...

Did you simply double-click on the font files to install them?

Have a look in ~/.fonts. Open your home folder and then press ctrl-H to reveal hidden files. If there is a folder called ".fonts" (with a leading dot) open it and see if your fonts are there. If they are, simply delete them.

They should disappear from the system as soon as they are deleted from the .fonts folder, but if not log out and log in again. If they still do not disappear, then regenerating the font cache may help, but I don't believe this will be necessary. If you need to know how to regenerate the font cache, post back.

---

### Post by MUK3SH on 2012-01-06
Yes.. It worked..
Thanks a Lot for your response.. :)

---

