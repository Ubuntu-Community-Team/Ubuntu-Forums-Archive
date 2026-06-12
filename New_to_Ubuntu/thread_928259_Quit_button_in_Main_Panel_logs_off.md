---
title: "Quit button in Main Panel logs off"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by rojodojo on 2008-09-23
Hi,

When I click the 'Quit' button in the main panel, instead of giving me the option to log off, restart, or shut down, it automatically logs off. I've been tweaking ubuntu quite a bit lately, but I'm not sure what I may have done to alter the action of the quit button.

Is there a way to restore the quit button's intended function?

---

### Post by phidia on 2008-09-23
If you changed system files it's harder. You would perhaps need to compare (use diff?) the live cd to your system. and copy files to see if that would correct this. You might also reinstall gnome. "sudo apt-get install --reinstall ubuntu-desktop"

If the changes are just to your user account then this is another good reason to have a test user. If the test user account functions normally then you can copy files (dot files) from the working account to the faulty one. "sudo adduser test".

---

### Post by hackerseraph on 2008-09-24
that reinstall desktop thing; its like reinstalling all of gnome in its original state yet does it leave programs still installed like emerald and such? does it merely overwrite everything else back to its default states like the x11 setup file and such?

---

### Post by rojodojo on 2008-09-24
> **phidia said:**
> If you changed system files it's harder. You would perhaps need to compare (use diff?) the live cd to your system. and copy files to see if that would correct this. You might also reinstall gnome. "sudo apt-get install --reinstall ubuntu-desktop"

If the changes are just to your user account then this is another good reason to have a test user. If the test user account functions normally then you can copy files (dot files) from the working account to the faulty one. "sudo adduser test".

I tested a new user and it works perfectly. So am I better using this new account and deleting the old one, or could I possibly salvage the old one?

---

### Post by phidia on 2008-09-24
You might have problems with a second accound since sudo only works with the first account created-or at least that's the way it use to work.

To answer the previous question you asked; re-installing gnome should not cause any problems with your personal files nor with X11 either.

---

### Post by SunnyRabbiera on 2008-09-24
you may wish to remove your gnome profile folders and remove sessions and such.

---

### Post by rojodojo on 2008-09-24
I'm a little confused with your answers. Sorry.
All I know is that reinstalling the genome didn't affect my problem in any way, and that the Test account's quit button worked as it should.
So is there a way to change my test account into the main(sudo?) account with all the privileges and then delete the faulty account?
thx again

---

