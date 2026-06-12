---
title: "file problem"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by ldarkphoenix on 2011-12-29
ok I just installed ubuntu to run with windows vista on my laptop. it works fine other than the fact that when I run ubuntu, none of my files from vista show up. how do I fix this without using that ubunu one thing?

---

### Post by yetiman64 on 2011-12-29
Is your Ubuntu install a Wubi install or a separate partition install ?

Edit: if a Wubi install check out [[COLOR=Blue]--this link--[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F") (the link is set to display the info you are after directly)

---

### Post by cortman on 2011-12-29
There should be links to the other partitions on the left side bar in the file manager, assuming you're dual booting. I don't know if it's the same with Wubi or not.

---

### Post by ldarkphoenix on 2011-12-29
> **yetiman64 said:**
> Is your Ubuntu install a Wubi install or a separate partition install ?

Edit: if a Wubi install check out [[COLOR=Blue]--this link--[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F") (the link is set to display the info you are after directly)

yeah it was a wubi install. I'm gonna check the link out. thanks

---

### Post by ldarkphoenix on 2011-12-29
yeah still can't find the files

---

### Post by yetiman64 on 2011-12-29
> **ldarkphoenix said:**
> yeah still can't find the files
Open any nautilus window (your home folder will do) and click on filesystem in the sidebar. Look at the folders within "filesystem" for one called "host". Open it and your Vista files should be in there. If not let us know, if they are but "host" is not showing in the nautilus sidebar, you may want to consider using the bookmarks in Nautilus to create an entry in the sidebar for the folder /host for easier access to your Vista files.

---

### Post by 3rdalbum on 2011-12-29
> **yetiman64 said:**
> Open any nautilus window (your home folder will do) and click on filesystem in the sidebar. Look at the folders within "filesystem" for one called "host". Open it and your Vista files should be in there.

+1.

In a Wubi install, this is where they are.

In a real dual-boot install your Vista partition would be listed in the sidebar.

---

