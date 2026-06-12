---
title: "Should i upgrade the X server ?"
date: 2013-03-18
forum: New to Ubuntu
---

### Post by esst on 2013-03-18
Im using Kubuntu 12.04.
Should i upgrade the X Server, if everything looks fine now ?
Last time i did that, i had problems starting the X and had to reinstall.
Im not asking about backports updates, but the default repositories.
Is upgrading the X server necessary and what are the benefits ?
And if i upgrade it, should i update other things like Nvidia drivers and the kernel ?

---

### Post by KnownSyntax on 2013-03-19
Are you talking about upgrading it manually or having the package manager update it (such as when Kubuntu will say that you have updates)?
If you do update it then you will more than likely have to update the graph drivers to make sure that they are up to date fully.

---

### Post by SeijiSensei on 2013-03-19
On my Kubuntu 12.04 machine, the most recent updates to xserver-xorg come from late February via automatic updates.  It's unlikely you'd need to upgrade the kernel or the nvidia driver.  If you do, they will be automatically updated via dependencies.

In general there isn't any reason to upgrade software unless the system determines there are updates that need installing.  Just let the updater do its job, and you'll be fine.

---

### Post by esst on 2013-03-20
ok, i updated without problems this time.
thanks

---

