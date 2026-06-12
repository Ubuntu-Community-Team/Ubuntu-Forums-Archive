---
title: "[SOLVED] Trash applet acting up. . ."
date: 2008-08-16
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-08-16
Hi.  My trash can is acting strange.  If I click on the trash applet, and click on empty trash, everything is deleted, except for a few folders that stick around.  If I right click on any of them and select delete from trash, I get:  Error removing file: Permission denied

If I right click and select properties, I see that I have full folder access, but file access is blank (under the permissions tab).  If I select "read and write" in the drop down list, and then click the apply to enclosed files button, and finally close the window, I can see that the changes aren't applied if I reopen the properties window.

Is there a way to empty the trash as root?  I tried sudo nautilus in a terminal but no avail.  Anything I can do?

Thanks in advance!

---

### Post by drs305 on 2008-08-16
You should be able to delete root trash in your trash bin by deleting
the 'files' and 'info' folders in trash:
```
gksu nautilus $HOME/.local/share/Trash
```

or:
```

sudo chown -R *username* /home/*username*/.local/share/Trash
rm -R /home/*username*/.local/share/Trash

```

---

### Post by pi.boy.travis on 2008-08-16
OK, thanks for that.  That got rid of the files in the trash, but that applet icon still shows that the trash is full. . .  Perhaps a restart is required?

EDIT:  Yup!  A clean install fixes all. . . OOPs. . . . Wrong saying. . . . 

Thanks!

---

### Post by drs305 on 2008-08-16
Do you have ntfs partitions or others that may have trash in them. You could have trash folders named Trash-1000 (or your userid).

You can search for all trash with the following command. I'd recommend using "gksu nautilus" to empty them the same as above. Find folders named Trash, .Trash, or .Trash-XXXX with X being some digit(s).

```
sudo find / -type d -iname *Trash*
```

---

