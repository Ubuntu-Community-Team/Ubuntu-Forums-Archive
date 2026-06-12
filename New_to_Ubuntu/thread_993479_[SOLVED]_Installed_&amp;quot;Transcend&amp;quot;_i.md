---
title: "[SOLVED] Installed &amp;quot;Transcend&amp;quot; in Synaptic, no clue where it is..."
date: 2008-11-25
forum: New to Ubuntu
---

### Post by Jesan Fafon on 2008-11-25
I just installed a game called Transcend through Synaptic, and I've no clue where the package went, or installed to.

That said, I've also downloaded the source and compiled my own version which gave me directions to run an application that didn't exist in the directories created during the install.

Thanks.
-Jesan Fafon

---

### Post by bumanie on 2008-11-25
I don't know where it installs to, but if you push alt-F2 together, a window will appear. Type transcend in there and then click on run and it should start if it has installed correctly.

---

### Post by handydan918 on 2008-11-25
You may also want to try ```
which transcend
```

---

### Post by nhasian on 2008-11-26
i love to use the *locate* command. try:

```
locate transcend
```

it uses a database of all the files in your filesystem.  the database is updated every morning at 5am.  if you've recently added files you can update the database manually before using locate with:

```
sudo updatedb
```

---

### Post by nakama85 on 2008-11-26
> **Jesan Fafon said:**
> I just installed a game called Transcend through Synaptic, and I've no clue where the package went, or installed to.

That said, I've also downloaded the source and compiled my own version which gave me directions to run an application that didn't exist in the directories created during the install.

Thanks.
-Jesan Fafon

Every now and then I find a simple reboot will put my newly installed app in my aplications menu.

---

