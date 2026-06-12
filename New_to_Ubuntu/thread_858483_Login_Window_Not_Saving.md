---
title: "Login Window Not Saving"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by guitar4ya on 2008-07-13
I tried asking about this yesterday in a two part question, but the part I really needed answered wasn't...  Anyways, I'm trying to disable my login window and every time I go into the login window settings and change something and exit out, it reverts back and doesn't save any changes.  I tried setting it for automatic login and it reverted back.  I also did the same with the timed login checkbox.  I selected my username and everything.  I've been searching everywhere for how to fix this.  I'm totally new to ubuntu/linux.  I'm wondering if there's just a way to either fix the login window gui or just go to terminal and disable the login window that way.  Please help if you can.  Thanks...

---

### Post by guitar4ya on 2008-07-13
I should also add that I've installed new login window themes and when I try to select them and close the login window settings the new theme isn't applied and sure enough when I go back in the old settings have been reverted here as well...

---

### Post by guitar4ya on 2008-07-13
bump

---

### Post by Inxsible on 2008-07-13
that is strange...but have you tried doing it as root.

I am not sure if that would work...but you can always try. 

Word of caution : You need to be careful what you change there since you can make your system unbootable if you muck something up.

---

### Post by guitar4ya on 2008-07-14
I haven't tried that.  How would I do that?

---

### Post by guitar4ya on 2008-07-14
I just tried switching to root in terminal and then using gksu gdmsetup there, but it wouldn't open it under root... Any setting, not just the automatic login check box reverts back when I close out of the login window preferences...

---

### Post by djacidjac on 2008-09-24
I had a similar problem; no changes to "Login Window" would save. I deleted /etc/gdm/gdm.conf-custom and then made a copy of /etc/gdm/gdm.conf named gdm.conf-custom. Everything works in "Login Window" now. Just remember that any changes you made in the past will be gone and you'll be left with the default settings.

This took me a while to figure out. I hope this helps.

---

