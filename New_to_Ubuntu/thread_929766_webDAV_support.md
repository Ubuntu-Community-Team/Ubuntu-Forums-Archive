---
title: "webDAV support"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by estanton on 2008-09-25
I'm currently trying to figure out how to enable webDAV support on my laptop. Basically I want to be able to upload files to a remote server which hosts my webspace. It would be nice to be able to do this through something akin to drag-and-drop. I know this is possible using KDE, however I'm partial to Gnome. What is the best way to accomplish this?
Thanks!

---

### Post by pp. on 2008-09-25
Suggestion:

Connect to your server using the menu "Places/ConnectToServer" or similar. Select WebDAV(HTTP) as protocol.

The menus and entries might be called differently. I don't have the English version of Ubuntu.

---

### Post by Veljance on 2010-01-09
This question may sound noobish but i cant pass the point where i need to save the edits for "vi /etc/apache2/sites-available/default"

I use terminal but do not have a clue on how to save the edit, i tried Ctrl X, Ctrl O but nothing, it does not save the file and afterwards if i try to edit again asks for recovery. Can you please help me how to save the edits for this?

---

### Post by kellemes on 2010-01-09
> **Veljance said:**
> This question may sound noobish but i cant pass the point where i need to save the edits for "vi /etc/apache2/sites-available/default"

I use terminal but do not have a clue on how to save the edit, i tried Ctrl X, Ctrl O but nothing, it does not save the file and afterwards if i try to edit again asks for recovery. Can you please help me how to save the edits for this?

Try this instead..
```
gedit /etc/apache2/sites-available/default
```

With the editor *vi* you save like so..
```
:w
```
save & quit
```
:wq
```

Edit: I think we just hijacked an old thread.. :eek:

---

### Post by Veljance on 2010-01-11
I would like to thank you and apologize if this thread was already somewhere in the forum discussed.

Thanks again

---

