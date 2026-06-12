---
title: "adding variables to /env/skel/.bashrc"
date: 2011-11-28
forum: New to Ubuntu
---

### Post by linux_noob0 on 2011-11-28
How come the variable I declare in /env/skel/.bashrc doesn't show in printenv nor does echoing show the value I assigned?
Thanks.

---

### Post by cavh on 2011-11-28
If you want to edit your .bashrc, it's located at /home/<your user name>/.bashrc

You need to log out and back in again for changes to your .bashrc to be effective.

No idea what /env/skel/.bashrc is for.

---

### Post by Paqman on 2011-11-28
> **linux_noob0 said:**
> How come the variable I declare in /env/skel/.bashrc doesn't show in printenv nor does echoing show the value I assigned?
Thanks.

So when you create a new user, it doesn't show what you expect? Can you post your /etc/skel/.bashrc and what you see in the new account?

---

### Post by JKyleOKC on 2011-11-28
> **linux_noob0 said:**
> How come the variable I declare in /env/skel/.bashrc doesn't show in printenv nor does echoing show the value I assigned?
Thanks.Because the /etc/skel directory's files are copied into a user's home directory **only** when the user is created. Their purpose is to provide initial settings when you create another user account, not to provide a place for system-wide changes.

To change your own settings, modify $HOME/.bashrc instead. Note also that no "/env" directory exists in a normal installation, but I suspect that's just a typing error...

---

