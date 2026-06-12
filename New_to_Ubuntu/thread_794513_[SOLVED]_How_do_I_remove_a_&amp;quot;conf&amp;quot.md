---
title: "[SOLVED] How do I remove a &amp;quot;conf&amp;quot; line"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by hufferd on 2008-05-14
So I want to edit the xorg.conf file...  How to I edit in the terminal?? 

ie.  I can open it from with in gnome but cant save it after I edit I assue this is because from within gnome I don't have root access...

Can anyone place help?

thanks

~D

---

### Post by shifty_powers on 2008-05-14
```
gksudo gedit *path of file*
```

you need sudo, i.e. root, privileges to save it. that is what gksudo and sudo do, grant temporary admin rights ;)

---

### Post by MaindotC on 2008-05-14
You can open files with root permissions and edit them by preceding your commands with the word "sudo".  For example:

```

sudo nano /etc/X11/xorg.conf

```

Please make a backup of your xorg.conf before editing it.  Here is an example:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

The above command copies the contents of the source file xorg.conf to the desination file xorg.conf.backup.  If you edit xorg.conf and produce undesirable results, you can boot into your system and issue the following command to replace the xorg.conf file with the original contents that had a working display:
```

sudo cp /etc/X11/xorg.conf.back /etc/X11/xorg.conf

```

Good luck!

---

### Post by Thirtysixway on 2008-05-14
You can do
```
sudo gedit XORG
```

replace XORG with the path to xorg.  You won't be able to use the same terminal while the text editor is up.

You can also get a commandline text editor, I recommend joe
```
sudo apt-get install joe
```
joe filename.bbq

---

### Post by hufferd on 2008-05-14
Hey everyone thank you for all the help I did what I needed to do --- you guys are great - and yes thank you for reminding me about the "backup file" just in case LOL thats a good idea.  

This is all so neew to me being a long time windows user :) 

thank for the help!

---

