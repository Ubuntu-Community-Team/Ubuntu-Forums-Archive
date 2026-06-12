---
title: "[SOLVED] Removable Drives and Media Settings - Hardy"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by crjackson on 2008-05-13
Since a clean install of Hardy, I'm no longer prompted for what action to take when a CD or DVD is placed in the drive.

I've looked in the settings as above and there is no option to change this setting in Hardy (I've looked in Gutsy and it's there.

Is this normal for Hardy or have I disabled it somehow?  I don't really use it but it was nice for starting movie DVD's and music CD's.

How do I turn this back on?

---

### Post by alienexplorers on 2008-05-13
I have the same problem and was wondering myself how to get Hardy to recognize the insertion of a new CD into my drive and run the program associated with it.

---

### Post by Rhubarb on 2008-05-13
Open up nautilus (or go Places --> Home Folder).
Then go to Edit --> Preferences
Select the Media tab

From here you can change it to "Ask what to do" for CDs / DVDs / etc

---

### Post by AndrewTheArt on 2008-05-13
[http://ubuntuforums.org/showpost.php?p=4549198&postcount=4](http://ubuntuforums.org/showpost.php?p=4549198&postcount=4)

In Nautilus:
 
 Edit->Preferences, Media tab, _Software combo box. Select "Do Nothing". Enjoy.

---

### Post by dizee on 2008-05-13
It is probably somewhere in gconf-editor in Ubuntu. Also have a look in Nautilus, in Edit > Preferences > Media.

Xubuntu has a nice GUI for it anyway.

---

### Post by crjackson on 2008-05-13
> **Rhubarb said:**
> Open up nautilus (or go Places --> Home Folder).
Then go to Edit --> Preferences
Select the Media tab

From here you can change it to "Ask what to do" for CDs / DVDs / etc

Thanks, I found it.  Only problem is that it doesn't work.  It has no effect no matter what the settings are it does nothing...

---

### Post by AndrewTheArt on 2008-05-13
You don't happen to have GParted installed, do you?

---

### Post by crjackson on 2008-05-13
> **AndrewTheArt said:**
> You don't happen to have GParted installed, do you?

Nope...

---

