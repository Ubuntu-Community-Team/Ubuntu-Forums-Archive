---
title: "How can I install a downloaded TAR package with Synaptic?"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Friccy on 2008-11-12
Hi there!

I have downloaded a .TAR package for *glabels*.
I can't install it!
How can I use Synaptic to install this package or any other from now on?
Thanks!

---

### Post by markjensen on 2008-11-12
I assume the .tar file either contains a .deb or some source and an installer script.

I guess, if I understand you right, you are asking how to install something _outside_ of the package manager, and still have the package manager handle it?

I'm not familiar with the app glabels.  But it would make sense to use the package manager to install it in the first place, that way you get every update when it is put into the repos.

Do a **sudo apt-get install glabels**, or search it in the syanptic GUI to click and install it.

---

### Post by fooman on 2008-11-12
did you look in synaptic for glabels?

it should already be there....no need to mess with the .tar

---

### Post by Friccy on 2008-11-12
Yes, I have looked in Synaptic.
There is an older version of the app.
Now I'm installing that and hope that I can upgrade to the new one.
Thanks for everybody!

---

### Post by hessiess on 2008-11-12
Probally extract the tar, cd into the extracted directory and 
```
./configure && make && sudo make-install
```

---

