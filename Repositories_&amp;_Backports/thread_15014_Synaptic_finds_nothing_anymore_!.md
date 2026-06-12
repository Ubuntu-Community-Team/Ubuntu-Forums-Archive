---
title: "Synaptic finds nothing anymore !"
date: 2005-02-11
forum: Repositories &amp; Backports
---

### Post by M-Rick on 2005-02-11
I have run synaptic to install a few software like inkscape and abiword.
After ine the preferences I have cleaned the cach with the option but now when I run synaptic it doesn't show me no one package anymore ! It is impossible to add something else ! But is says no broken package, no update necessary and 8531 packages installed. So it sees the softwares ... I have made an update of the list but same issue, what can I do ?

---

### Post by mendicant on 2005-02-11
Try running aptitude, and see if you can see packages.  If so, you've just set up synaptic so that it doesn't show certain files.  Since I don't use synaptic, that's all I can tell you.

---

### Post by symbiat on 2005-02-16
I have the same problem. After doing an update the list of packages disappear.
If you hit Reload you can see it loading package info but nothing is shown on the right. I haven't changed any filters or set any preferences but this still happens.

I was able to run aptitude and run an update followed by an upgrade of packages - no problems with that.

I am running the PPC version on a ("blue n white") G3 Mac.

---

### Post by M-Rick on 2005-02-16
The solution is there : 
[https://bugzilla.ubuntu.com/show_bug.cgi?id=6151](https://bugzilla.ubuntu.com/show_bug.cgi?id=6151)

---

