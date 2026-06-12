---
title: "How to make it so Private folder doesn't automatically mount everytime I login"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by dugh on 2008-10-31
I enabled support for the private encrypted folder, but I don't wanted it mounted on my desktop everytime I login.

How can I disable this, I don't see an entry in /etc/fstab

---

### Post by poldie on 2008-10-31
> **dugh said:**
> I enabled support for the private encrypted folder, but I don't wanted it mounted on my desktop everytime I login.

How can I disable this, I don't see an entry in /etc/fstab

type gconf-editor in a console, then click apps/nautilus/desktop and untick the buttom option (`show icons on desktop` I think it's called)

---

### Post by Silent Ninja on 2008-11-05
> **poldie said:**
> type gconf-editor in a console, then click apps/nautilus/desktop and untick the buttom option (`show icons on desktop` I think it's called)
That will only hide ALL the disk mounts from the desktop, that's not what he asked for.

I have the same issue, I do want to show the other mounts, but I do NOT want the Private folder to be "automounted" on boot.

¿Is there any way to "config" the Private folder?
I mean... skip the automount, mount it via nfs, converting it to a normal folder, deleting it, making another private folder besides the "private" home... ?

---

