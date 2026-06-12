---
title: "Adding applications to 'Applications'"
date: 2008-04-04
forum: Programming Talk
---

### Post by Ansible on 2008-04-04
I've written a couple of applications for ubuntu. One is a game using SDL. The other is a time tracker using GTK. I created application launchers for them in the 'Applications' menu, but from there I can only launch the game, not the GTK app. I can still launch the GTK app by going to it in Nautilus and double clicking. Any ideas?

---

### Post by nanotube on 2008-04-04
> **Ansible said:**
> I've written a couple of applications for ubuntu. One is a game using SDL. The other is a time tracker using GTK. I created application launchers for them in the 'Applications' menu, but from there I can only launch the game, not the GTK app. I can still launch the GTK app by going to it in Nautilus and double clicking. Any ideas?

obvious question: are you sure you didn't mistype the commandline in the launcher for the gtk app? :)

---

### Post by Ansible on 2008-04-05
> **nanotube said:**
> obvious question: are you sure you didn't mistype the commandline in the launcher for the gtk app? :)

Yeah; I used the 'Browse' button and then the 'Choose an application' dialog so I didn't actually type the name in.  The same process worked for my other app...

---

### Post by Ansible on 2008-04-05
Doh!  Never mind.  The GTK app was looking for its .glade file in the wrong directory - when you run it from the application launcher apparently it gives your '/home/username' directory as the default dir, not the application directory.  I need to have this thing give an error if the .glade isn't found, or link it in...

---

### Post by nanotube on 2008-04-05
> **Ansible said:**
> Doh!  Never mind.  The GTK app was looking for its .glade file in the wrong directory - when you run it from the application launcher apparently it gives your '/home/username' directory as the default dir, not the application directory.  I need to have this thing give an error if the .glade isn't found, or link it in...

or even better, detect where it's located (sys.path[0] contains that info), and load the glade from there. :) (an error if it's not found is not a bad idea either way, of course)

---

