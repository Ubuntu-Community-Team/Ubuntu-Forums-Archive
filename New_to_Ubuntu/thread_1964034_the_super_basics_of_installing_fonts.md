---
title: "the super basics of installing fonts"
date: 2012-04-23
forum: New to Ubuntu
---

### Post by feralfinds on 2012-04-23
hi! 

i would like/love to install "century gothic" onto my computer. i'm using the 11.04 version of ubuntu, if that makes a difference. i'll be using the font in gimp & inkspace, maybe libreoffice writer. 

i checked out the synaptic package manager, but didnt see the font in there. i installed msttcorefonts, but it wasn't there either. i found some sites online, from which i can (hypothetically) download the files for this font, but i am in need of some reeeeallly basic instructions on how to do this! describing every little step. 

can someone be so kind as to point me to a thread or site that will help me in this installation? and, if there is a good place to find this font online, that would also be appreciated information. 

thanks! jenfer

---

### Post by Cheesemill on 2012-04-23
If only you want to use the font just copy it into ~/.fonts/ (you may have to create the folder first).
If you want it to be available for all users then copy it into /usr/share/fonts/

Then run:
```
sudo fc-cache -f -v
```You may need to restart any applications or log out then back in for the new font to be recognised.

Edit -Apparently you can just double click on the downloaded font to install it.
Edit 2 - As far as I am aware Century Gothic is not in the public domain, it's owned by Monotype Imaging  so you will have to pay for it.

---

### Post by feralfinds on 2012-04-23
are there any web-sites you would recc'd for dowloading the .ttf file(s)? 
i dont have a sense of, if its ok to just do this from any site, or if one should be more careful than that...

---

### Post by zombifier25 on 2012-04-23
> **feralfinds said:**
> are there any web-sites you would recc'd for dowloading the .ttf file(s)? 
i dont have a sense of, if its ok to just do this from any site, or if one should be more careful than that...
Before downloading fonts, you should always check their licenses to see if you're violating any.

---

### Post by feralfinds on 2012-04-23
got it! i think i was expecting a much more complicated process. 
this was truly very easy! thanks for the help! 
jennifer

---

