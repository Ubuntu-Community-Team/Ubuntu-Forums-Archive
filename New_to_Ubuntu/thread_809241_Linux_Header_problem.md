---
title: "Linux Header problem"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Ginoxy on 2008-05-27
Good day, 
i've been faing a problem with this : 
any idea ?
[ATTACH]71757[/ATTACH]

[ATTACH]71758[/ATTACH]

---

### Post by unutbu on 2008-05-27
The latest version of Ubuntu, Hardy, comes with 
linux-headers-2.6.24-16. Are you installing these packages from an unofficial repository?

See [http://packages.ubuntu.com/hardy/linux-headers-generic](http://packages.ubuntu.com/hardy/linux-headers-generic)

---

### Post by Monicker on 2008-05-27
I would try again later, as the second messages suggests   Once in a while I see issues similar to this because a repository may not be fully synced its updates when you connect to it.

Or you could try going into Synaptic and switching to a different repository, reloading, and then go back to Update Manager.

---

### Post by Monicker on 2008-05-27
> **unutbu said:**
> The latest version of Ubuntu, Hardy, comes with 
linux-headers-2.6.24-16. Are you installing these packages from an unofficial repository?

See [http://packages.ubuntu.com/hardy/linux-headers-generic](http://packages.ubuntu.com/hardy/linux-headers-generic)

One of the updates which I received yesterday included linux-headers-2.6.24-17

---

### Post by Ginoxy on 2008-05-27
> **Monicker said:**
> I would try again later, as the second messages suggests   Once in a while I see issues similar to this because a repository may not be fully synced its updates when you connect to it.

Or you could try going into Synaptic and switching to a different repository, reloading, and then go back to Update Manager.

and how to do that?

---

### Post by Monicker on 2008-05-27
System -> Administration -> Synaptic Package Manager -> Settings -> Repositories -> Download from

---

### Post by Ginoxy on 2008-05-27
okay now i have this !!![ATTACH]71764[/ATTACH]

---

