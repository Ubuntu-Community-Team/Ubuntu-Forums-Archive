---
title: "Dynamic trash icon"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by zaklinux on 2008-06-15
Hi Everybody!

I recently fudged up my trash icon on my desktop and it no longer shows when its full.

No matter which icon theme I chose, the trash shows empty even though there are files in there.

Anybody know of a way to revive a trash icon to make it dynamic?

Is there a reset button or something for the trash.

---

### Post by Barriehie on 2008-06-16
> **zaklinux said:**
> Hi Everybody!

I recently fudged up my trash icon on my desktop and it no longer shows when its full.

No matter which icon theme I chose, the trash shows empty even though there are files in there.

Anybody know of a way to revive a trash icon to make it dynamic?

Is there a reset button or something for the trash.

Mine has done that before and the fix is quite simple!  I made an empty folder on the desktop and then deleted it, i.e. put it in the trash can and then emptied the trash can.  Works everytime!

Barrie

Worst case you could right click and remove the trash can and then add it back.

---

### Post by zaklinux on 2008-06-16
Thanks I'll give it a shot as soon as I can.

---

### Post by zaklinux on 2008-06-17
Unfortunately, that didn't work.

Add a file and folder to trash, empitied, and it still shows as full.

I've tried changing the icon to an empty trash can and adding documents, but it still shows as empty.

Is there a special icon I have to choose that will actual reflect the Trash can's status?

---

### Post by iaculallad on 2008-06-17
Try to "re-empty" the Trash using the Terminal:

For User:

```
sudo rm -rf /home/your_username/.local/share/Trash/*
```

For Root:

```
sudo rm -rf ~/.local/share/Trash/files/*
```

---

