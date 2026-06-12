---
title: "Saving files to network"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by dover19 on 2008-05-28
I'm having issues trying to save files to the network share at work. If I try to download something from firefox, when the window Save As window pops up, I can't see the network share icons that are on mounted my desktop.

I could save files directly on my desktop and then move them, but there has to be a way of saving it there directly.

---

### Post by justleen on 2008-05-28
you should be able to browse to /media/youdisks/.

not sure why the shortcut dont show up in there....

---

### Post by blakegrover on 2008-05-28
I have noticed that I have never seen my network shares through open or save dialogs in gnome.  I am pretty sure this isn't supported/implemented but it would be great to see this fixed.

Blake

---

### Post by hyper_ch on 2008-05-28
maybe you could just make a symlink on your desktop to the network share... maybe this shows with the open/save as dialog.

---

### Post by dover19 on 2008-05-28
> **hyper_ch said:**
> maybe you could just make a symlink on your desktop to the network share... maybe this shows with the open/save as dialog.

You mean by right-clicking on the network share then clicking on "Ma_k_e Link"?

I can't even do that, the option is grayed out.

Actually this is another annoyance. I would like to make a shortcut on my desktop to a folder within the network share but when I try to do so I get this message:
Error "Unsupported operation" while creating a link to "smb://db2/Data/Slsmktg".

---

### Post by hyper_ch on 2008-05-28
I mean by
```

sudo ln -s /path/to/network/share /home/USER/Desktop/SYMLINK

```

---

### Post by dover19 on 2008-05-28
> **hyper_ch said:**
> I mean by
```

sudo ln -s /path/to/network/share /home/USER/Desktop/SYMLINK

```

Hmmmm...It creates a broken link:
The Link "SYMLINK" is Broken. Move it to Trash? 
This link can't be used, because its target "//db2/Data/Slsmktg" doesn't exist.

---

### Post by hyper_ch on 2008-05-28
oh well, I mount network share anyway into my local filesystem

---

