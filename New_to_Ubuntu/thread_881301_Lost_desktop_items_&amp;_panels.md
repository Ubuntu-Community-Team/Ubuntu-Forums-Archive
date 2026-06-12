---
title: "Lost desktop items &amp; panels"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by flyingsolo on 2008-08-05
Please help--Somehow I seem to have lost all Desktop items & top/bottom panels though I don't know how.  It may be related to having needed to do a hard shutdown b/c system was 'frozen/locked'.  Now when I boot up & sign on, I get my Desktop with background image  as before but none of the files are on Desktop and top & bottom panels are not present.  How can I restore what I had?  (I don't know even how to get a terminal to do reinstall gnome panels)
thanks.

---

### Post by tuxxy on 2008-08-05
Try CTRL + ALT + F1 to get your prompt to re-install

---

### Post by st33med on 2008-08-05
What he said to get to tty1 and do this:
```
sudo apt-get remove gnome-panels nautilus && sudo apt-get install gnome-panels nautilus
```

---

### Post by flyingsolo on 2008-08-05
Thank to both above.  I seem to have succeeded by CTRL+ALT+F1 and then sudo apt-get install gnome-panel.  I'm back in hardy right now but haven't shut down/restart to see if it sticks.  That's what I'll do now/next.

---

### Post by tuxxy on 2008-08-05
To restart from terminal try

```
sudo shutdown -r now
```

---

### Post by flyingsolo on 2008-08-05
thanks again--all seems good to go now; thanks for the note on shutdown--I never can remember that one and so I usually try 'quit', 'stop', 'end' etc but I never remember 'shutdown'.  Maybe now I will!

---

### Post by tuxxy on 2008-08-05
Yes and if not you can always go back through the commands you alredy enetered or do a search for shutdown commands used

```
 history | grep shutdown
```

---

### Post by Muflon on 2008-08-06
> **flyingsolo said:**
> Please help--Somehow I seem to have lost all Desktop items & top/bottom panels though I don't know how.  It may be related to having needed to do a hard shutdown b/c system was 'frozen/locked'.  Now when I boot up & sign on, I get my Desktop with background image  as before but none of the files are on Desktop and top & bottom panels are not present.  How can I restore what I had?  (I don't know even how to get a terminal to do reinstall gnome panels)
thanks.

Hi flyingsolo

Out of curiosity did you uninstall Evolution before you encountered this problem?  

Muflon

---

### Post by simonuk on 2008-08-27
I had un-installed Evolution just before this happened and wondered if that was the cause.

Your solution above didn't work for me so in the end I did this which got me back to normal:

```
sudo apt-get install ubuntu-desktop
```

It installed evolution again but this programme seems to be a more major part of the OS than I thought.

---

