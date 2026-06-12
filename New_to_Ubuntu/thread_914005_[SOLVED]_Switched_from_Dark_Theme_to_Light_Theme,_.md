---
title: "[SOLVED] Switched from Dark Theme to Light Theme, How do you change Firefox menu text"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by AegisTalons on 2008-09-08
Hey everyone,

I have been using a dark theme (Elegant Brit specifically) and switched over to a light theme. Included in Elegant Brit was userChrome.css (for Firefox) that you replace the current one that Firefox has. It was included to make the Firefox menu font color work with the dark background. (Changed font color from black to white.)

Does anyone know how to change the menu font color? I would like to change it from white to black.

Thanks for the help.

---

### Post by Thingymebob on 2008-09-09
In ~/.mozilla/firefox/*.default/chrome there is file called userchrome-example.css which contains the firefox defaults just copy this to userchrome.css

if userchrome-example.css isn't there, then remove the line in userchrome.css that reads:
```

#main-menubar > menu {
color: white !important;
}

```

---

### Post by cdtech on 2008-09-09
[quote]1

---

### Post by alienexplorers on 2008-09-09
menu#file-menu {color: blue ! important;}
menu#edit-menu {color: red ! important;}
menu#view-menu {color: green ! important;}
menu#history-menu {color: black ! important;}
menu#bookmarksMenu {color: red ! important;}
menu#tools-menu {color: green ! important;}
menu#helpMenu {color: blue ! important;}

---

### Post by AegisTalons on 2008-09-10
Sweet! It works. Thank you very much.

---

