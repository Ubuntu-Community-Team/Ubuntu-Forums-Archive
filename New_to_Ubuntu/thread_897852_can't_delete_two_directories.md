---
title: "can't delete two directories"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-08-22
there are two directories on my desktop,which i want to delete.when i try doing so,it says that i do not have the permission for that.how can i delete them from the terminal using some sudo command?

---

### Post by Oldsoldier2003 on 2008-08-22
> **stonecoldjha said:**
> there are two directories on my desktop,which i want to delete.when i try doing so,it says that i do not have the permission for that.how can i delete them from the terminal using some sudo command?

```
sudo rm -rf /path/to/directory
```

```
sudo rm -rf ~/Desktop/dirname
```

---

### Post by aysiu on 2008-08-22
What Oldsoldier2003 told you is technically correct. I would be very careful in typing that command, though. If you hit the **Enter** key too early, you may end up deleting a lot more than those two directories.

Instead, I'd recommend changing ownership of the files so that you *do* have permission to delete them. Use [this terminal command](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R *username* ~/Desktop
``` where *username* is your actual username.

How did those directories get on your desktop? What program put them there?

---

