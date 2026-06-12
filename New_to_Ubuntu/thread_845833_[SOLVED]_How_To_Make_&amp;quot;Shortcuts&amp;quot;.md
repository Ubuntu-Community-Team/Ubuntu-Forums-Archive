---
title: "[SOLVED] How To Make &amp;quot;Shortcuts&amp;quot; on Desktop?"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Eric Qel-Droma on 2008-07-01
This is a very Windows-centric question, I know, but I'm trying to make Ubuntu more palatable to my wife.  I have our personal docs stored on a separate FAT32 partition and I'd like to put a link to that directory on our Ubuntu desktop.  I have a bookmark to it under "Places" up top, but it would be easier to know how to make something like a shortcut.  Can that be done?

Thanks!

Eric

---

### Post by untermensch on 2008-07-01
O let me try to remember.. ok right click on your desktop. then click on create launcher. type application name <whatever you want to be, mine is documents> command is nautilus /home/wherever/the/drive/is and then hit ok. and you should see one come up. hope that helps. =]

---

### Post by RomeReactor on 2008-07-01
Hi. In Nautilus navigate to where the folder in question is; right-click on it and select 'Make link'. Now cut that link and place it in your desktop.

---

### Post by Eric Qel-Droma on 2008-07-01
> **RomeReactor said:**
> Hi. In Nautilus navigate to where the folder in question is; right-click on it and select 'Make link'. Now cut that link and place it in your desktop.

Even when running "gksudo nautilus" I get the error ```
Error making symbolic link: Operation not permitted
```.

??

---

### Post by harjp on 2008-07-01
> **Eric Qel-Droma said:**
> I have a bookmark to it under "Places" up top, but it would be easier to know how to make something like a shortcut.  
I can drag a copy of the icons in the Places menu (Computer, Desktop, Documents, etc.) onto the desktop and a shortcut is automatically created!

---

### Post by Eric Qel-Droma on 2008-07-01
> **untermensch said:**
> O let me try to remember.. ok right click on your desktop. then click on create launcher. type application name <whatever you want to be, mine is documents> command is nautilus /home/wherever/the/drive/is and then hit ok. and you should see one come up. hope that helps. =]

I just tried this, but nautilus apparently thinks whatever folder I want should be in my home directory, whereas my drive is NOT in my home dir.  I still don't really understand Linux directory structure, so I don't know how to fix this.

Thanks.

---

### Post by Eric Qel-Droma on 2008-07-01
> **harjp said:**
> I can drag a copy of the icons in the Places menu (Computer, Desktop, Documents, etc.) onto the desktop and a shortcut is automatically created!

When I try this, it actually starts File Operations copying ALL files onto the desktop.  I just want a shortcut.

---

### Post by bab1 on 2008-07-01
Navigate to the directory where the folder you want is.  Depress BOTH buttons on the mouse while highliting the folder you want.  Drag the folder to the desktop and the option to create a shortcut (link) should be available.

---

### Post by Eric Qel-Droma on 2008-07-01
> **bab1 said:**
> Navigate to the directory where the folder you want is.  Depress BOTH buttons on the mouse while highliting the folder you want.  Drag the folder to the desktop and the option to create a shortcut (link) should be available.

THAT did EXACTLY what I wanted it to.  Thank you!  How did you know to do that?

---

### Post by RomeReactor on 2008-07-01
Try making a link like this:
```
ln -s /PATH/TO/FOLDER ~/Desktop
```
Just make sure to substitute **/PATH/TO/FOLDER** with the complete, actual path.

EDIT: Disregard.

---

### Post by Locutus_of_Borg on 2008-07-01
cd ~/Desktop
ln -s /path/to/documents Documents

edit: i swear this wasnt marked as solved when i clicked reply...

---

### Post by Eric Qel-Droma on 2008-07-01
Thanks for the alternate solutions, everybody!

BTW, as a note for anyone else who reads this thread, I had to do a search for how to automount my internal drives at start-up, as restarting the computer meant that the drives didn't automount, didn't show up, and thus the links I'd just created became broken links.

Anyway, make sure you're automounting whatever you're linking to if you want to avoid broken links!

---

### Post by Eric Qel-Droma on 2008-07-01
> **Locutus_of_Borg said:**
> cd ~/Desktop
ln -s /path/to/documents Documents

edit: i swear this wasnt marked as solved when i clicked reply...

Should I enter that in Terminal?

---

