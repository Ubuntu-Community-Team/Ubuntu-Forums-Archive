---
title: "copy file"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by davewalbert on 2008-05-17
how do i copy a file boot_v8 to the boot folder from david/pc_efi_v80 to /boot

---

### Post by warbread on 2008-05-17
```

:-$ cp /name/of/file/to/be/copied /destination/directory

```

Use "sudo" for files that are write protected.  Example:

```

:-$ sudo cp /etc/apt/sources.list /home/regularjoe/sources.list.backup

```

---

### Post by Average Joe on 2008-05-17
Assuming that "david" is in the /home directory, use this command in a terminal.
```
sudo cp /home/david/pc_efi_v80/boot_v8 /boot/
```
You'll have to use sudo here, since only root has write permissions to the /boot directory.

EDIT: warbread, what you are saying is plain wrong. As long as you can read the file, you don't need to be root to copy a file to a directory where you have write permissions (e.g. your own home folder). Just try to copy the /etc/apt/sources.list file to your own home folder, you'll see that it will work without sudo, although you don't have write permissions to that file.

---

### Post by gn2 on 2008-05-17
Or press Alt+F2 type gksudo nautilus

When you press Enter this will open the file browser with full root privileges and you will be able to move or copy and paste the file to the desired location.

Remember to close it immediately you're finished.

---

