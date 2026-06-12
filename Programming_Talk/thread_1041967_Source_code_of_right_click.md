---
title: "Source code of right click"
date: 2009-01-17
forum: Programming Talk
---

### Post by kcode on 2009-01-17
Where can I find source code of Right Click?
I'm using Gnome on Ubuntu 8.04.

Thanks

---

### Post by nvteighen on 2009-01-17
> **kcode said:**
> Where can I find source code of Right Click?
I'm using Gnome on Ubuntu 8.04.

Thanks

What do you mean by that? The contextual menu? IIRC, that's Nautilus... so, do:

```

mkdir nautilus-source
cd nautilus-source
apt-get source nautilus # No sudo needed

```

---

### Post by kcode on 2009-01-17
> **nvteighen said:**
> What do you mean by that? The contextual menu? IIRC, that's Nautilus... so, do:

```

mkdir nautilus-source
cd nautilus-source
apt-get source nautilus # No sudo needed

```

yes, i did mean that. But here's the error:

```

~/nautilus-source$apt-get source nautilus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for nautilus
~/nautilus-source$

```

---

### Post by eye208 on 2009-01-17
> **kcode said:**
> yes, i did mean that. But here's the error:

```

~/nautilus-source$apt-get source nautilus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for nautilus
~/nautilus-source$

```
[[IMG]http://img525.imageshack.us/img525/2353/softwaresourcesgk5.png[/IMG]](http://imageshack.us)

Enable "Source code", then try again.

---

### Post by kcode on 2009-01-17
> **eye208 said:**
> 
Enable "Source code", then try again.

Thanks, it worked.

---

