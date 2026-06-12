---
title: "recommended directory for local user apps"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by clearski on 2013-04-22
I was wondering what was the best directory in Ubuntu hierarchy to place and run a downloaded application, which doesn't require any specific location outside its containing folder.

Now I am running it from /usr/bin, but I also read that a good place to store apps is /usr/local/bin, while others recommended to create a folder called /Application in my ~.

What do you recommend?

---

### Post by sudodus on 2013-04-22
The classical location since unix for user specific executables (programs and scripts) is
 [B][FONT=courier new]
~/bin[/FONT][/B]

If you create that directory, it will be found and included in $PATH at the next boot. But if you want other users to be able to run it, you should put it into some other directory, for example those you suggested.

You should also check that the new app/program/script does not interfere with a standard program with the same name.

---

### Post by deadflowr on 2013-04-22
It really depends on whether you want it accessible for all users or just a single user.
If for all users, then put it in the /usr/local directory.
If just for a single user, put it in the home folder somewhere.

---

### Post by clearski on 2013-04-22
> **sudodus said:**
> The classical location since unix for user specific executables (programs and scripts) is
 [B][FONT=courier new]
~/bin[/FONT][/B]

If you create that directory, it will be found and included in $PATH at the next boot. But if you want other users to be able to run it, you should put it into some other directory, for example those you suggested.

You should also check that the new app/program/script does not interfere with a standard program with the same name.

Thank you, I'll move it to ~/bin. I'm the only one using this program, so it's fine to move it into my home folder.

---

