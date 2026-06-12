---
title: "root filebrowser + trash = crash"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-06-15
Hi folks, 

So i think in the latest kernel there may be a bug in that if you launch nautilus with sudo (ex: gksudo nautilus) and try to empty root's trash it crashes nautilus and i don't think the trash empties.

Am I the only one getting this problem or have other gotten it too?
Any way to fix it?

Thanks, 

-'Mage

---

### Post by iaculallad on 2008-06-15
Try using the terminal to empty the root's Trash:

```
sudo rm -rf ~/.local/share/Trash/files/*
```

---

### Post by UnWarierMage224 on 2008-06-15
Ah icic...

would there be any way to script this command so it would run at shutdown?

-'Mage

---

### Post by iaculallad on 2008-06-15
Create a file named cleaner.sh (should contain the quoted text below):

> #!/bin/bash
#
rm ~/.local/share/Trash/files/*

Make it executable:

```
sudo chmod +x cleaner.sh
```

To make it execute on shutdown:

```
sudo cp cleaner.sh /etc/init.d
sudo ln -s /etc/init.d/cleaner.sh /etc/rc0.d/Dcleaner.sh
sudo ln -s /etc/init.d/cleaner.sh /etc/rc6.d/Dcleaner.sh
```

Test it afterwards.

---

### Post by 45acp on 2008-06-17
Having the same problem with gksudo nautilus crashing. Having to delete trash manually.

---

