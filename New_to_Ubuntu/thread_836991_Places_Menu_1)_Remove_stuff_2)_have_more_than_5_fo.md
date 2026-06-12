---
title: "Places Menu: 1) Remove stuff 2) have more than 5 folders  w/o cascdng subfolder"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by hanzj on 2008-06-22
Hello,
1) How can I remove some stuff from the Main Menu/Places/ menu?
I want to remove (or hide) "Network" and "Connect to Server"

2) I have 5 personal folders appearing right under the "Desktop" folder.
When I have 6 or more, they then appear in a subfolder. How can I prevent that from happening? I do not want the subfolder. I want 6 or 7 folders to just appear in the main dropdown Places menu?

Thanks.

---

### Post by KaliVoid on 2008-06-23
Answer for question 1 :

To remove items from the main menu use "Main menu" editor in System->Preferences->Main menu.

To remove items from the "Places" menu open nautilus and in the menu click Bookmarks->Edit Bookmarks.

Question 2 i don't know.

---

### Post by hanzj on 2008-06-23
KaliVoid,
"Edit Bookmarks" won't remove the 2 things I said I want to remove.

---

### Post by KaliVoid on 2008-06-24
[Removing "Network" from 'Places' menu]("http://ubuntuforums.org/showthread.php?t=525826")

---

### Post by Sonic Reducer on 2008-10-28
> **KaliVoid said:**
> [Removing "Network" from 'Places' menu]("http://ubuntuforums.org/showthread.php?t=525826")

so [this]("http://ubuntuforums.org/showpost.php?p=3196991&postcount=4") is the way to go?

[QUOTE=mannheim]These entries are hard coded. But you can remove them by deleting or renaming the items to which they refer. So, to remove the "Connect to server ..." menu item, do:

```
sudo mv /usr/bin/nautilus-connect-server /usr/bin/nautilus-connect-server.hidden
```

and to disable the "Network" item, do:

```
sudo mv /usr/share/applications/network-scheme.desktop /usr/share/applications/network-scheme.desktop.hidden
```

(Do a "killall gnome-panel" after this to reload the panel and see the changes.) Of course, the first of these in particular may have other unwanted side-effects! And I'm sure this is a really bad thing to do (or a bad way to do it) from many points of view.[/QUOTE]

(also posting here in case it screws my system up and i need to fix it lol)

---

### Post by KaliVoid on 2008-10-29
> **Sonic Reducer said:**
> so [this]("http://ubuntuforums.org/showpost.php?p=3196991&postcount=4") is the way to go?

Try the [next post]("http://ubuntuforums.org/showpost.php?p=3197006&postcount=5"), it's sounds safer.

---

### Post by Sonic Reducer on 2008-10-30
> **KaliVoid said:**
> Try the [next post]("http://ubuntuforums.org/showpost.php?p=3197006&postcount=5"), it's sounds safer.

but i'm trying to remove the "network servers" from the places sidepane in nautilus

---

### Post by repsakkgn on 2010-01-14
no idea?

---

