---
title: "how do i open up .bin files?"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by leah1984 on 2008-07-28
i recently downloaded realplayer for linux from theyre website and cannot open it from my desktop where it was saved.it is a .bin file and when i double click on it it  says;  there is no application installed for this file type.
im not sure what app.i need to open this file type ? can anyone help me?
:confused:

---

### Post by tuxxy on 2008-07-28
Open terminal and change dir to the one containing the .bin, then run it by typing ./appname.  This example would assume its called realplayer.bin on desktop

```
cd Desktop
```

```
./realplayer.bin
```

---

### Post by kool_kat_os on 2008-07-28
run this command to make it executable:

```
chmod +x filename.bin
```

---

### Post by leah1984 on 2008-07-28
i get to the desktop directory but when i try to run realplayer it says no such file or directory

---

### Post by kool_kat_os on 2008-07-28
uh...what commands did you run?

---

### Post by leah1984 on 2008-07-28
first i entered cd desktop to get to the proper directory then ./ RealPlayer11GOLD.bin to run it but it says no such file or directory.that is the file name on my desktop.am i missing step?

---

### Post by leah1984 on 2008-07-28
ok so i tryed sudo ./ ReaPlayer11GOLD.bin and it worked.what is the diff between sudo and chmod? its been a while since i used the terminal and i just remembered that sudo was the "command prompt" i guess you could say?

---

### Post by kool_kat_os on 2008-07-28
chmod applies the correct permisions to the file to make it executatble...

sudo temporarly applies super user(root)privelages for that command(which is required if you are installing somehting)


terminal is like the "command prompt" in linux

sudo is a command

---

