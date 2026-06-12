---
title: "removing FireFox 3"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by akamuza on 2008-04-26
hi all
i'm a novice to Ubuntu and need some help in a simple problem i think.
just installed Hardy and realized i don't like Mozilla FF 3 at all.
so i want to remove it and install Mozilla FF 2.0.14

how correctly am i to remove FF 3 ?? what issues should i know??
'cause it seems to me that "Add/Removw programs" is not the best idea.


ps
sorry my english

---

### Post by swegner on 2008-04-26
Hi akamuza,

If you would like to use firefox 2 instead of firefox 3, you can simply uninstall Firefox 3, and install Firefox 2, all from the Add/Remove dialog.

In the main menu, open ""Add/Remove..".  Search for Firefox.  Uncheck "Firefox Web Browswer"-- this represents Firefox 3.  Then, you can check "Firefox 2 Web Browser", if it isn't already checked.  Then click "Apply Changes", and the correct versions will be installed / uninstalled.  You can find Firefox 2 inside of the Applications > Internet menu.

The only other trouble I could imagine you might have is with the default browser.  To set Firefox 2 as your default browser after it's installed, go to System > Preferences > Preferred Applications.  On the first tab, check to see if "Firefox 2" is selected as the default browser.  If not, I would recommend using "Custom", and enter the command
```
firefox-2 %s
```

Hope this helps!

---

