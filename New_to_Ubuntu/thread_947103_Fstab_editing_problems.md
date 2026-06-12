---
title: "Fstab editing problems"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by conway.federico on 2008-10-14
all i need to do is amend my /etc/fstab so that i can mount gmailfs.

I need to know how to do this...

"Open /etc/fstab and insert this in the bottom:

vim /etc/fstab"

---

### Post by jemate18 on 2008-10-14
> **conway.federico said:**
> all i need to do is amend my /etc/fstab so that i can mount gmailfs.

I need to know how to do this...

"Open /etc/fstab and insert this in the bottom:

vim /etc/fstab"

to edit fstab you need root privileges

sudo pico /etc/fstab

What do you want to append?

---

### Post by conway.federico on 2008-10-21
Basically I want to get the "Gmailfs" up and running... From...  [http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html)  But i am a very new to linux... and thus have yet to get it to work... does anybody know a good walk-through for this problem?  Or can explain the process clearer?  My problems come up when trying to mount or fstab for the drive... and I have problems getting the python scripts transfered to root. I did it in command line, but now i can't remember how...

I'm loving Ubuntu so far, and loving learning about it.  I just haven't had time to sit down and really look at the basic elements of command line... If anybody can lend me a hand I would be very grateful.

---

### Post by oldos2er on 2008-10-21
Anytime you need write permission outside of your /home directory, you must give yourself admin privileges. In Ubuntu, you do this by prepending "sudo" or "gksu" in front of the command. For example, if you want to edit your fstab with the gedit editor, you'd open a terminal and type "gksu gedit /etc/fstab". Use "gksu" for graphical applications, and "sudo" for CLI ones.

---

