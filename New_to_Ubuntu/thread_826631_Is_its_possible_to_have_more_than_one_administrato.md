---
title: "Is its possible to have more than one administrator?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by andriy.kostyuk on 2008-06-12
I tried to create another user with the status "Administrator".
The result was terrible:
1.I couldn't unlock the "Users and Groups" neither from my account nor from the newly created one. 
2. The Synaptic Package Manager along with some other programs disappeared from my menu, but did not appear in the new user's menu.

I solved the problem by reinstalling Ubuntu.

Still, I wonder, what was the reason for such strange behavior of the system. Did I do something wrong? Is it possible to have more than one Administrator in the system?


I use Hardy 8.04. Before it happened, a huge automatic update (more than 500 files) was performed.

---

### Post by iaculallad on 2008-06-12
Try to add your username to the /etc/sudoers file:

Code:

```
sudo gedit /etc/sudoers
```

then add your username at the bottom of the file:

> username ALL=(ALL) ALL

---

### Post by kesman on 2008-06-12
NO DON'T DO IT!

Sudoers file must be edited with
```

sudo visudo

```
only!

---

### Post by andriy.kostyuk on 2008-06-12
> **iaculallad said:**
> Try to add your username to the /etc/sudoers file:

Code:

```
sudo gedit /etc/sudoers
```

then add your username at the bottom of the file:

As I wrote, I've already soled the problem by reinstalling the system. I 

Now I wonder, whether I did something wrong or it's a bug in the system.

Thanks anyway.

---

