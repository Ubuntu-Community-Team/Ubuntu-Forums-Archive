---
title: "File permissions, Deletion"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by Taigrr on 2008-10-25
I recently installed Ubuntu on my fathers computer, and there's one problem that's not helping your cause!


He uploaded all his music files, from CD's, onto his hard drive. All works well and good. But, there's thumbnails of all the album covers that he wants to get rid of. In Windows, those files were displayed over the icons of the albums. In Ubuntu, they do nothing.

He wants to remove those files, but can't. Permission denied. So we setup root, logged in as root, navigated to the default music folder, and there were no files. 

So how, *without the command line* is he supposed to delete and move files? They are not system files, they're just images that he doesn't want in there.


(Yes, I understand it's an easy "sudo mv" command, but I'd like to keep this as windows-user friendly as we can.)

Thank you Ubuntu gods and goddesses! You are my saviors.

---

### Post by cariboo on 2008-10-25
You can use, Alt-F2 and the type:

```
gksu nautilus
```

to run Nautilus as root. If the files were all copied to his home folder you shouldn't have to jump through any hoops to add or delete files. If you copied them as root then all you have to do is change the ownership.

Jim

---

### Post by chrisamiller on 2008-10-25
Assuming that this is a standard linux-formatted drive (ext3 or similar) and not FAT32 or NTFS, the problem is probably one of two things.  

1) He's not the owner of the files.  If this is the case, it can be fixed with one command from the root of his music directory:

```
sudo chown -R <username>:<username> *
```

2) He owns the files, but they're set to read only.  Also easy to fix.  Again, from the root of his music directory:

```
sudo chmod -R u+rw *
```

If the files were copied over from an NTFS or FAT32 drive, it may explain the screwy permissions.

Additionally, if you set up a root account and logged into it, you probably weren't finding the music files because you were looking in the root user's 'Music' folder, instead of your fathers (which would be at /home/<username>/Music

That said, it's almost never a good idea to run as root, and that's doubly true if your father is something of a computer novice.

---

