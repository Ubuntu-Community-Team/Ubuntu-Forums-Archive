---
title: "Login window change"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by richiewrt on 2008-07-09
I am trying to change my login window, and when I launch the loginwindow application it immediately closes. I think this may have something to do with the fact that I installed the xubuntu packages a while back and have since uninstalled them. Now I am stuck with the xubuntu login window, and can't figure out how to change it.

**Edit
I have also tried gksudo gdmsetup and it does the same thing.

---

### Post by rainwalker on 2008-07-09
Do you have GDM installed?

---

### Post by richiewrt on 2008-07-22
BUMP,

I reinstalled ubuntu and I was able to change the login window for a bit, but I am having the same problem once again when trying to change the login window. Now I just have a straight ubuntu install with no xubuntu or kde. I'm not sure what has caused this. I would like to be able to change the login screen and this is becoming a pita.

---

### Post by RomeReactor on 2008-07-22
Hi. When you launch the Login Window application from the terminal, does it leave any error messages there? If so, it would be useful if post them here so we can try to pinpoint the problem.

---

### Post by richiewrt on 2008-07-22
Attached image.

---

### Post by RomeReactor on 2008-07-22
It seems you're using a theme that has a missing icon, or that icon has a problem; try switching back to the Human or Clearlooks theme and launch GDMSetup again.

---

### Post by richiewrt on 2008-07-22
I tried that, still didn't work.

Edit**
I just get the segmentation fault after reverting to the human theme.

---

### Post by RomeReactor on 2008-07-22
I'm not absolutely sure if this will help, and I suggest you wait for someone else to provide you a better answer before you do this, but you can reconfigure GDM from the terminal:
```
sudo dpkg-reconfigure gdm
```
After it finishes, restart Ubuntu.

---

### Post by artmendez on 2008-07-25
Same thing happened to me since yesterday.

I did gdmsetup, tried the dpkg...

no success.

I get the Segmentation Fault message from terminal. When called from the menu, it opens, closes after about half a second. I have thw Windows List applet running in a panel. A "Starting Login Window" label in the space taken by this stays for several seconds, then disappears.

Any ideas?


thanks.

---

### Post by lori on 2008-08-09
> **RomeReactor said:**
> I'm not absolutely sure if this will help, and I suggest you wait for someone else to provide you a better answer before you do this, but you can reconfigure GDM from the terminal:
```
sudo dpkg-reconfigure gdm
```
After it finishes, restart Ubuntu.

Thank you very much RomeReactor! Your suggestion worked for me! :)
Login Window now opens with no problem!

---

### Post by rainwalker on 2008-08-09
> **lori said:**
> Thank you very much RomeReactor! Your suggestion worked for me! :)
Login Window now opens with no problem!

Don't forget to mark your thread as solved :)
(It's under Thread Tools up at the top)

---

