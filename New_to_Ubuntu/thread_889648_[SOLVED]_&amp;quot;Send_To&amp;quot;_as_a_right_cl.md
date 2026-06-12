---
title: "[SOLVED] &amp;quot;Send To&amp;quot; as a right click command through Nautilus?"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by sdim on 2008-08-14
Hi,everyone.
I think I've asked this before,but just to be sure:
Can I add a right click command (in Nautilus maybe...?) to send files to other directories without using the Copy/Paste dialogue ?
Is there anything that can be added to the Nautilus Scripts mentioned in other cases ? Something we can create as a command ?

Thank you.

---

### Post by renzokuken on 2008-08-14
like this?

[http://gnome-look.org/content/show.php/Send+to...?content=67627](http://gnome-look.org/content/show.php/Send+to...?content=67627)

should be fairly simple to create your own nautilus script too

---

### Post by ibizatunes on 2008-08-14
I have to say this is the only thing i miss from xp, i wish someone would add it permanently to ubuntu

---

### Post by sdim on 2008-08-14
Yes,renzokuken.Thank you for the link.I was talking about something like that.
I read the documentation and I hope it can send a folder to other directories in the system,apart from removable drives,etc.

How can someone create a script like that,anyway?

---

### Post by kaboodle_fish on 2008-08-14
Ubuntu-Tweak has scripts under the Desktop > Nautilus heading which I think includes send to. It certainly has move and copy options. 
 
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by sdim on 2008-08-14
Thank you,kaboodle_fish.You were right.
There are Nautilus Scripts including _Move To_,in the Personal section of Ubuntu Tweak 0.3.4.
Many thanks.

---

### Post by ice60 on 2008-08-14
i got that script too, it's really good, but i haven't really needed to use it.

nautilus-actions is a great way to put things in your right-click menu, i added loads of extras to my nautilus right-click menu (you can add the same things to thunar too if you use that instead of nautilus with custom actions.)

you can put the moveto script in the right-click menu with nautlius-actions

---

### Post by airtonix on 2008-08-21
it is also possible (from what i have read around these pages) to make use of python in order to place options directly in the right click menu. 

Although the scripts menu is more than sufficient in my opinion and every linux user that wishes to control their system to the utmost really ought to learn the basics of bash scripting, it also does not presupose that every linux user has python on their system.

Here is one i made that allows you to take a selection of files and make a archive that spans over many files, the file size of each span can be selected from a list.

it requires zenity and rar : 

```
sudo aptitude install zenity rar
``````
#!/bin/bash
rar a -m`zenity --scale --max-value=5 --title "Choose the level of compression" --text "0 = no compression, 5 = max compression"` -v`zenity --title "Create split archive..." --text "Please choose the file size of each archive part : " --list --radiolist --column " " --column "Size" False 3GB False 1GB False 500M False 100M False 20M False 5M False 500K False 100K False 20K False 5K --height 400` -R "$1.rar" $1
```

---

