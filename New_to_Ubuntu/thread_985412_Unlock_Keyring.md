---
title: "Unlock Keyring???"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Graham Orpwood on 2008-11-17
I just installed Ubuntu 8.10 for the first time.  Next time I boot up, I get a window entitled "Unlock Keyring" asking me to "Enter password for default keyring to unlock" adding that "The application 'NetworkManager Applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked.

I tried entering my normal password but the window simply reappears.  I dont understand a word of what is happening and none of the books I have explains this feature.

Can someone help?  Should I start over and reinstall Ubuntu?

---

### Post by nhasian on 2008-11-17
it should be the superuser password.  you only need to enter it once.

---

### Post by Graham Orpwood on 2008-11-17
I only have used one password when installing Ubuntu...so that must be what you call the "superuser password"  right?  And that does not work in getting rid of this window.

---

### Post by achase79 on 2008-11-17
You will have to rebuild the keyring.  in the home folder there should be a .keyring folder that is a hidden folder or in the .gnome* folder. If you rename it or delete it and restart it will have you rebuild it and you can set it to your user password.

---

### Post by Keen101 on 2008-11-17
The keyring is a place to store your passwords. If you set up a wireless password, that is the reason it asks you on startup... it wants to connect to your wireless device. Personally i don't like the keyring.

---

