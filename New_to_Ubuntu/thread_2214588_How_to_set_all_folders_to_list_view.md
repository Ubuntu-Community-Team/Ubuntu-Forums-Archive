---
title: "How to set all folders to list view?"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by 171742 on 2014-04-02
Hello,

pretty much all that. That I do not have to repeat it.

Thanks!

---

### Post by apohal9 on 2014-04-02
Hi,

I currently do not have access to an Ubuntu installation, but I remember, that there is an option in the settings (available from the menubar of nautilus) which view is the default for displaying folders.

---

### Post by slickymaster on 2014-04-02
Open a terminal and run the following command:```
gsettings set org.gnome.nautilus.preferences default-folder-viewer 'list-view'
```There are two more options you can use '_icon-view_' and '_compact-view_'.

---

### Post by apohal9 on 2014-04-02
@171742: I assume you are on Unity on Ubuntu 13.10: click on the top left corner of the screen why nautilus is open. Select Files -> Settings. Right on the first dialog that gets open, you can select to open new folders with listed view as default.

---

