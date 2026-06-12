---
title: "rsync can't create symlinks?"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by raccoonone on 2008-07-12
I just tried to use rsync to backup my home directory to a windows share, and it seems to have choked trying to move the symlinks.
The command I used is: ```
rsync -aE --exclude="/.config/xpad/" --exclude="/Examples" --exclude="/.dbus/" --modify-window=2 /home/christopher/ /media/christopher_files/Backup/CONROE/home/christopher/
```
But after running that I got a whole bunch of errors which seem to be related to symlinks:
```
rsync: symlink "/media/christopher_files/Backup/CONROE/home/christopher/wine-git/programs/winver/winver" -> "../../tools/winewrapper" failed: Operation not supported (95)
rsync: symlink "/media/christopher_files/Backup/CONROE/home/christopher/wine-git/programs/wordpad/wordpad" -> "../../tools/winewrapper" failed: Operation not supported (95)
rsync: symlink "/media/christopher_files/Backup/CONROE/home/christopher/wine-git/programs/write/write" -> "../../tools/winewrapper" failed: Operation not supported (95)
rsync: symlink "/media/christopher_files/Backup/CONROE/home/christopher/wine-git/programs/xcopy/xcopy" -> "../../tools/winewrapper" failed: Operation not supported (95)
rsync: symlink "/media/christopher_files/Backup/CONROE/home/christopher/wine-git/tools/winegcc/winecpp" -> "winegcc" failed: Operation not supported (95)
rsync: symlink "/media/christopher_files/Backup/CONROE/home/christopher/wine-git/tools/winegcc/wineg++" -> "winegcc" failed: Operation not supported (95)

```
That's just a few of them. I get pages and pages of that. Is there another option I need to add, or do samba shares not support symlinks? Would it help if I installed rsync on the Windows server, using Cygwin?

---

### Post by p_quarles on 2008-07-12
rsync is so flexible that it might help us help you if you were to say something more about what type of backup you're trying to do. I.e., the scope and expected use of the backup, and how the computers are connected, etc.

In any case, the -l option will copy symlinks, but you may want to do something else (like -L, which will transform the symlink into a copy of the target). It depends on what this situation looks like.

---

### Post by raccoonone on 2008-07-12
I have a computer running Windows XP which offers the folder "christopher_files" as a network share, from a hard drive formatted in NTFS. On my Ubuntu computer, I have mounted that folder to /media/christopher_files/ using samba. What I would like to do is backup my home directory (/home/christopher/) to the windows share, just in case the hard drive fails, or some other disaster befalls my Ubuntu machine.

I tried the -a option, which is suppose to include the -l option. But that doesn't seem to make the symlink transfer work. Would it help if I created a .tar file from my home folder and transferred that instead, or would that defeat the purpose of using rsync (fast backups)?

---

### Post by chris_nava on 2008-07-12
I don't think NTFS supports symlinks.
Use a Linux formatted destination drive (ext2 or ext3).
OR
Copy the target files instead (-L option)
OR
Use something like tar to archive the links into a single file that can live on any drive.

---

### Post by raccoonone on 2008-07-12
> **chris_nava said:**
> I don't think NTFS supports symlinks.
Use a Linux formatted destination drive (ext2 or ext3).
OR
Copy the target files instead (-L option)
OR
Use something like tar to archive the links into a single file that can live on any drive.

The first one isn't an option, as the server I'm backing up to will be running Windows for the foreseeable future.

If I use the second option my file system will have changed in the event that I have to restore from this backup, correct? A lot of those symlinks I didn't create myself (they're in the WINE source tree...etc), so I don't want to mess around with them.

If I tar all the files, in my home directory, together before I use rsync on them, will rsync still be able to transfer only the differences? I'm not sure how the rsync algorithm works, and backing up a 100GB+ tar file every night could be problematic.

---

### Post by cariboo on 2008-07-12
Windows file systems do not support symlinks. You can use the -d option with tar to create a differetial backup. Check out:

```
man tar
```

The answer to a lot of questions can be found using man pages. many of the man pages even have examples of how to use commands.

Jim

---

### Post by raccoonone on 2008-07-15
Thanks, I've been looking at tar and it seems like that will work, but it says that I should run it when the files aren't in use. So I looked into using LVM2 to create a snapshot that I could backup, so that I could continue using my computer while the backup was running. However, it seems that to use LVM2 I would need to erase my hard drive to create a logic volume on it, is there another way that I can do this that will be easier?

---

### Post by Aaron Thoma on 2010-01-05
> **chris_nava said:**
> I don't think NTFS supports symlinks.> **cariboo907 said:**
> Windows file systems do not support symlinks.

Update: since Windows Vista, NTFS features symbolic links. (They have better compatibility with *nix symbolic links than the older directory junctions.)

[http://en.wikipedia.org/wiki/NTFS_symbolic_link](http://en.wikipedia.org/wiki/NTFS_symbolic_link)

---

