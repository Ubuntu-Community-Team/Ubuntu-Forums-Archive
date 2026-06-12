---
title: "[SOLVED] Rubyripper has separation anxieties!!!!"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Teabicky on 2008-10-31
I have installed Rubyripper and no longer want it. The problem is that it does not show up on the Add/ Remove application or the Synaptic Package Manager.

Also I have deleted the folder Rubyripper-0.5.3 from my desktop and I can't move it back to where it was or even delete it.  I get a message saying "There was an error deleting LC_MESSAGES." and "Error removing file: Permission denied".

Also there doesn't seem to be a man page either!!

Nothing bad is happening as a result of any of this it's just annoying.

---

### Post by chrisod on 2008-10-31
```
sudo apt-get remove rubyripper
``` in the terminal should do it.

---

### Post by Teabicky on 2008-10-31
I have just tries that and got the following message

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package rubyripper"

Could it be something to do with the directory that is stuck in my trash?

---

### Post by mc4man on 2008-10-31
Anything else remaining will probably need to be removed as root. The easiest way would be from gksudo nautilus and then shift+delete the files. 
Do a search from 'places' on rubyripper to find. (plus look in /usr/bin for rrip_gui, rrip_cli and home for .rubyripper

If you compiled
If you did a 'make install' then also look in /usr/bin or /usr/local/bin for rrip_gui and rrip_cli. There would also be a .rubyripper in home directory.
If you just did a 'make' and was running RR from the build folder then just the folder and the .rubyripper

---

### Post by Teabicky on 2008-10-31
Thanks that seems to have got rid of it, although I still can't remove the folder from my trash.:confused:

---

### Post by shifty_powers on 2008-10-31
have you tried

```
gksudo nautilus
```

and then clearing the trash from nautilus?

---

### Post by gandaran on 2008-10-31
try this, open terminal and type **sudo rm -r** next open the trash, drag the folder to the terminal and hit enter, type password, enter and it's gone!

---

### Post by Teabicky on 2008-10-31
> **shifty_powers said:**
> have you tried

```
gksudo nautilus
```

and then clearing the trash from nautilus?

Tried this and all I get is this message
"Sorry, couldn't display all the contents of "trash": Operation not supported"

---

### Post by gandaran on 2008-10-31
gksu nautilus- you have to go to /home/user/.local/share/trash
this is where trash is located (depends on what version of ubuntu you have)
my first tip also only works on some ubuntu versions

---

### Post by Teabicky on 2008-10-31
I can't find the  /.local directory in nautilus or anywhere using the GUI so I tried to use terminal.

I've found it with the 'locate' command (/home/flanagan/.local/share/Trash/files/rubyripper-0.5.3/locale/ru/LC_MESSAGES).  But when I try to navigate there It is missing;

> root@flanagan-desktop:/home/flanagan# ls
autosave  Documents    Examples  mp3    Pictures  Templates
Desktop   dvdrip-data  Inbox     Music  Public    Videos


Sorry for being dumb, I know there is a simple answer I just can't figure it out myself.:confused:

---

### Post by gandaran on 2008-10-31
it's your hidden home folder
nautilus » view, show hidden files

---

### Post by Teabicky on 2008-10-31
Thanks. Thats done it.:)

---

