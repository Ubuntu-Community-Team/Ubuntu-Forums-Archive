---
title: "Update Manager No Longer Works"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by ortwein on 2008-06-19
First, I have been trying to install virtualbox on my laptop (lenovo x61) to run Windows XP.  I'm afraid, however, that I've done something to screw up my sudo capabilities.  Because, now, whenever I try to update my computer it just sits there and does nothing.  the little wheel icon just spins.  

So, is there a way that I can fix this?

Please help.

mark

Oh, and Gdeb doesn't work either.:confused:

---

### Post by phidia on 2008-06-19
If you open a terminal window and enter > sudo apt-get update what is the output?

---

### Post by ortwein on 2008-06-19
tigre is not in the sudoers file.  This incident will be reported.


I should also add that I have tried to get my fingerprint reader to work with the UPEK Touchstrip software.  I followed some instructions in another post

---

### Post by Nikitas350 on 2008-06-19
You may have broken packages. Go to system ---> administration ----> synaptic package manager. Select custom filters (left and down) and then go to broken packages. Select them all and mark them for removal. Then click to the apply button.

---

### Post by phidia on 2008-06-19
> **ortwein said:**
> tigre is not in the sudoers file.  This incident will be reported.

If you are getting that message you either lost admin privileges or are using a different account/user then the one you created during install.
By default in Ubuntu only the first created account has administrative privilege.

---

### Post by cariboo on 2008-06-19
Check your /etc/hosts file it should look something like this:

```
127.0.0.1 localhost
127.0.1.1 alexis
```

replace alexis with your hostname. If you don't know your hostname, in a terminal type:

```
hostname
```

If there is anything else behind 127.0.1.1 besides your hostname, delete it.

Jim

---

### Post by ortwein on 2008-06-19
synaptic package manager is gone! All I see is update manager.

As for the etc/hosts file...looked just like yours, but with my host name.

any other ideas?

---

### Post by phidia on 2008-06-19
> **ortwein said:**
> synaptic package manager is gone! All I see is update manager.

As for the etc/hosts file...looked just like yours, but with my host name.

any other ideas?

What is the output of > apt-get -v?

However without administrative privilege you won't be able to use a package manager anyway. Did you set up a root account on this install?

---

