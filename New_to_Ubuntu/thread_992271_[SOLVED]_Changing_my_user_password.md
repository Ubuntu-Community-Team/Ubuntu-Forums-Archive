---
title: "[SOLVED] Changing my user password"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by the.scarecrow on 2008-11-24
If I use the Passwd app. to change my user password (I am the only user), what will happen to my sudo password e.g.

Will it stay the same as my old user password?
Will it change to my new user password?
or will everything be screwed up and I need to do a re-load!

Thanks
The.Scarecrow.

---

### Post by jken146 on 2008-11-24
It will be your new password.

---

### Post by mali2297 on 2008-11-24
sudo uses the current user password; changing it should not "screw up" anything.

---

### Post by the.scarecrow on 2008-11-25
So I have changed my password using the passwd app. with lets say 90% success. 

The only problem seems to be that just after logging in I am asked to put my password in again to allow access to the WiFi router pass. This does not accept my new password, I still have to use my old one.

There doesn't seem to be any obvious application installed that lets me change the WiFi key store to my new password as well.

Thanks for your help so far.

---

### Post by aysiu on 2008-11-25
Rename the /home/*username*/.gnome2/keyring folder to keyring.old and then reboot (logging out may be sufficient, but a reboot will certainly take care of it).

You'll be asked to create a keyring password. Either use your new user password or don't set one at all (just leave it blank).

---

### Post by the.scarecrow on 2008-11-25
```

Rename the /home/username/.gnome2/keyrings folder to keyrings.old and then reboot 
(logging out may be sufficient, but a reboot will certainly take care of it).

You'll be asked to create a keyring password. Either use your new user password or don't 
set one at all (just leave it blank).
```

That's solved it. So now its 100%, all using my new and very secure password. This bit even rated how strong my password is. I will delete my copy keyrings.old folder in a few days assuming there are no problems.

Now I just have to make sure I don't forget it!

Thanks to you all

---

