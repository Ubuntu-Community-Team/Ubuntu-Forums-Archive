---
title: "hard link?"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by mreyna16 on 2013-05-16
how can i hard link two folders?

basically i have a ntfs partition where i store all my music, pics, vids etc... and i want the home folders to show what ive put in them + what i have in my ntfs partition folders. i want to hardlink them specifically (i.e. music to music, pictures to pictures, etc.)

is there an app that can do it for me or can somebody show me the proper way of doing this? ive seached with no luck

---

### Post by Impavidus on 2013-05-16
You cannot make hardlinks from one partition to another, but you can make symbolic links: **ln -s target linkname**

---

### Post by mreyna16 on 2013-05-16
> **Impavidus said:**
> You cannot make hardlinks from one partition to another, but you can make symbolic links: **ln -s target linkname**

out of curiosity, why is that? im new to linux and if i dont ask then im not really learning it lol

---

### Post by CatKiller on 2013-05-16
Because they have to be in the same filesystem as the data. A hard link is the pointer from the block of data to the filename. It might help if you think of all files as hard links; when you create a hard link yourself you are simply creating an additional pointer to that block of data.

A symbolic link, on the other hand, is a pointer from one filename to another. The actual block of data is still addressed in the usual way.

---

### Post by mreyna16 on 2013-05-17
> **CatKiller said:**
> Because they have to be in the same filesystem as the data. A hard link is the pointer from the block of data to the filename. It might help if you think of all files as hard links; when you create a hard link yourself you are simply creating an additional pointer to that block of data.

A symbolic link, on the other hand, is a pointer from one filename to another. The actual block of data is still addressed in the usual way.

and a symbolic link will show the files stored in the folder itself and the ones in the folder of the ntfs partition? just like in windows?

---

### Post by CatKiller on 2013-05-17
The symbolic link won't really be a directory itself, it'll just pass through to the target. It will behave like a directory in your Home folder but any files you put in there will actually be on the other partition.

---

### Post by mreyna16 on 2013-05-17
> **CatKiller said:**
> The symbolic link won't really be a directory itself, it'll just pass through to the target. It will behave like a directory in your Home folder but any files you put in there will actually be on the other partition.
and how would i do it? i have a music folder, pictures, etc. and would like to link it to the folders in home

---

### Post by fantab on 2013-05-17
Here's how: [http://ubuntuforums.org/showthread.php?t=2145037](http://ubuntuforums.org/showthread.php?t=2145037)

---

### Post by prodigy_ on 2013-05-17
> **mreyna16 said:**
> and how would i do it? i have a music folder, pictures, etc. and would like to link it to the folders in home
Example, assuming that your user name is **username** and your NTFS partition is mounted as **/mnt/ntfs**:
```
rmdir /home/username/Music # But first make sure the folder is empty
ln -s /mnt/ntfs/Music /home/username/Music
```
Substitute actual paths and repeat for every folder you want to link.

---

### Post by vanadium on 2013-05-17
Open two instances of file manager. In the first window, have the folder on your ntfs partition displayed, to which you want to link. Leave the second window open in your home folder.

Press Ctrl+Alt and drag the folder from the first file manager window to the second. Release. Now, a symbolic link is created. It has the name "Link to <yourfolder>", and an arrow in the icon denotes it is a link. Clicking that link will bring you to the data on the ntfs folder.

You can rename the link, and move it to another location (only on a file system that supports symbolic links).

---

