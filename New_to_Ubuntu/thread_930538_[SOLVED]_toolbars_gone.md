---
title: "[SOLVED] toolbars gone"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by allsys3 on 2008-09-26
I recently did an upgrade and now have no toolbars. Im running compiz fusion with avant toolbar but I still need the original toolbar for shutting down the system. Any thoughts? Thanks

---

### Post by Sycron on 2008-09-26
Go to Applicatios-->Accesorie-->Terminal and type ```
sudo adduser **a-name**
``` where a_name is what you want. Then restart X, (Ctrl + Alt + Backspace) and login with the new account.

---

### Post by Orange_and_Green on 2008-09-26
Hello allsys3 :)

If you suspect that compiz is the cause, I suppose you could also try hitting ALT+F2 and type "metacity --replace". (This will turn off compiz).

Or, maybe your panels have been canceled for some reason? In this case, hit ALT+F2 and type "gnome-panel". A brand new panel shoud pop up, you can then right-click it, select "Add to panel..." and Add a "Main Menu", a "Quit" button etc.

Good luck!!:KS

---

### Post by allsys3 on 2008-09-26
Will this restore my toolbar or just create another user account? I
have things set up just the way I like them in my current account settings. Would these settings that I prefer still be active in this new acount setting? Thanks

---

### Post by Sycron on 2008-09-26
If you don't want to manually create the toolbars again then create a new account.

---

### Post by lian1238 on 2008-09-26
To shutdown, you can press Ctrl+Alt+Del also.

---

