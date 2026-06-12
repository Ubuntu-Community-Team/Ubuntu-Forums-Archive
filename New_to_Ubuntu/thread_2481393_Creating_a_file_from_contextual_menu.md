---
title: "Creating a file from contextual menu"
date: 2022-11-28
forum: New to Ubuntu
---

### Post by tonyMusante on 2022-11-28
Howdy,
On 20.10 it's possible to right click and create a new folder, options are to name that folder on-the-spot. WHY is it not so for a new document(naming)?
[IMG]https://pasteboard.co/JlrditFRHZIR.png[/IMG]

---

### Post by Morbius1 on 2022-11-28
Because your Templates folder is empty. It's by design in the Gnome-landia universe.

Open a terminal, then run this command:
```
touch $HOME/Templates/gedit.txt
```
Now open Nautilus to your desired location, right click, then you will see New Document:
[ATTACH=CONFIG]291316[/ATTACH]

You can populate the Templates folder with whatever you want like a new spreadsheet document, etc ...

---

### Post by tonyMusante on 2022-11-28
THanks. Perhaps there is no option to create a custom name for the document on the fly as it is possible for folders. Often I do not want to use the terminal. I am kinda repeating the same, hope you dont' mind.

---

### Post by Morbius1 on 2022-11-28
Ah, so this is about renaming it automatically like you do with Folders.

That isn't possible but you can follow this if you want to see the status of the request: [https://gitlab.gnome.org/GNOME/nautilus/-/issues/524](https://gitlab.gnome.org/GNOME/nautilus/-/issues/524)

---

### Post by Morbius1 on 2022-11-28
I don't know how wedded you are to using Nautilus but Thunar file manager can do what you want:

Right click > Create Document > Empty File:
[ATTACH=CONFIG]291318[/ATTACH]

---

### Post by mIk3_08 on 2022-11-29
I think this is what he means. see image below. Regards and cheers

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291322&stc=1[/IMG]

---

