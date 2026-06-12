---
title: "[SOLVED] Copying .dat file to /usr/local/matlab folder"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by chaddiesel on 2008-06-22
I need to copy a license.dat file into the /usr/local/matlab folder. I'm assuming you use a sudo command but don't know exactly what to do.

---

### Post by Biggy on 2008-06-22
read [here]("http://ubuntuforums.org/showthread.php?t=834576&page=2")

---

### Post by chaddiesel on 2008-06-22
how do i get to /home/name of user/.gnome2/nautilus-scripts?

i'm guessing that /.gnome2 is hidden

---

### Post by Biggy on 2008-06-22
to view .gnome2 folder ,go to home folder > View menu > Show Hiden Files

check it

---

### Post by iaculallad on 2008-06-22
> **chaddiesel said:**
> how do i get to /home/name of user/.gnome2/nautilus-scripts?

i'm guessing that /.gnome2 is hidden

If nautilus-scripts is a folder, you can change directory there by:

```
cd ~/.gnome2/nautilus-scripts
```

~ will bring you to your home directory and YES, .gnome2 is a hidden directory.

---

### Post by chaddiesel on 2008-06-22
Thanks!! 

worked like a charm. I've been wondering how to see those hidden files too!!!!:)

---

### Post by iaculallad on 2008-06-22
Or when inside your /home or any directory, you could press the Ctrl+H key combination to see hidden files and folders.

---

### Post by chaddiesel on 2008-06-22
While i'm in the matlab installer, it won't continue becuase it says that /usr/local/matlab73 is not writable.

I don't get that. Is there a way to sudo the cdrom/install & command?

---

### Post by chaddiesel on 2008-06-22
played with the folder permissions. GOT IT!!!!:guitar:

---

