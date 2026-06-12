---
title: "How I Delete Files and Directory in Linux"
date: 2022-07-22
forum: New to Ubuntu
---

### Post by lokeshjoshi94 on 2022-07-22
Hello all, i am new to use Ubuntu, and i am deleting a file by using -rm command but i am not able to delete it i am facing an error directory not empty error i do not know ahy this happen, i search this issue on the internet as well. but i am not able to find the correct solution, please help

---

### Post by mIk3_08 on 2022-07-22
Try to use sudo the administrative command. And let me know the results. If you can do screenshot and show us here in this thread it will be much better. Regards and cheers

---

### Post by Impavidus on 2022-07-22
**rm** can remove files. Just files. **rmdir** can remove directories, but only empty directories. As a shortcut, there's **rm -r**, rm with the r (=recursive) option. This will remove a directory and all its contents. If rm encounters any write-protected files, it will first ask for confirmation. May I suggest you read the manual page?```
man rm
man rmdir
```You can close the manual by hitting q.

Don't use sudo when you don't know why you need elevated privileges. An approach like "I got an error, let's try it with sudo" will get you in trouble. sudo is used when the ordinary user doesn't have permission to do something. It sometimes helps against "permission denied" errors, not against other errors.

The contents of the terminal can be pasted as text on the forum. That's far easier than making a screenshot. And easier for us to copy from.

---

### Post by mIk3_08 on 2022-07-22
> **lokeshjoshi94 said:**
> Hello all, i am new to use Ubuntu, and i am deleting a file by using -rm command but i am not able to delete it i am facing an error directory not empty error i do not know ahy this happen, i search this issue on the internet as well. but i am not able to find the correct solution, please help
Try to empty the directory before you can delete the directory alone using rmdir command. Regards and cheers.
```
rmdir
```

---

### Post by drawde111 on 2022-07-25
Hi, you will likely require the recursive flag to delete folder with content. rm -fr /name/of/directory
This is a fairly destructive command so tread carefully.

---

### Post by col48 on 2022-07-25
Although the Terminal commands are far quicker if the number of files is large, I prefer to use a GUI approach.

In this way you can see what you are about to do more readily than when using a Terminal command, so a pending mistake is more obvious (at least, to me!).


In Ubuntu 16.04, Nautilus is installed as the standard file manager, but I prefer nemo for reasons which are irrelevant here.

Click your way down the file structure until you select the folder (=directory) you want to delete (with all the files and subfolders it contains) and hit the delete key, which transfers the lot onto 'Trash' from where it can be restored as long as the space has not been needed meanwhile for newly created files.  If you use shift+delete you delete permanently instead of to Trash, but you get a warning first.

---

### Post by lokeshjoshi94 on 2022-07-27
Hi, Thank You for the Suggestions, and these are really help me to delete the Directory, i rm -rf 'AccessType' (directory name) and it works for me, i also visit [this post]("https://monovm.com/blog/how-to-delete-directory-and-file-in-linux/") on the internet about the delete the linux directory and this also help me a lot, thank you, My problem is solved now

---

### Post by TheFu on 2022-07-27
Basic things like this are easily learned via this free, no-hassle, no data stealing, ebook [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  No need to ask here and wait for answers.  That is a basic Linux guide that you could buy at a normal bookstore if you like or just download the PDF in your native language.

Many of the commands you've posted above aren't correct.  Details matter. Being correct matters.
Using **sudo** is dangerous, especiaily when there is little understanding.
Using **rm -rf** is also dangerous. It is very easy to completely wipe a computer with that command, so be extremely careful using it.

Even with these warnings, you'll mess up and wipe the system at least once. Everybody does. I did.  It was a work server and the only thing that saved me was a CDROM was mounted and there were thousands of "permission denied" errors being shown on the screen.  I was banging <cntl>-c about 50 times to stop the command. The deletion was happening in alphabetical order, so /bin was long gone - that's where the most important commands are.  Fortunately, the day before, I'd made a backup to tape.  I was such a noob, I didn't know how to restore the tape. This was before we connected the server to the internet and before there were search engines, so I drove to a bookstore with a large (for that time) computer section and bought a Systems Admin book for the OS.  Took about 15 minutes to find the restore command and get all the deleted files back.  I was lucky.

That wasn't the only time I wiped a system either.  ;)  It was the only time I was using rm -rf, however.  There are lots of ways to wipe a system and sudo is almost always involved. Beware.

---

### Post by TheFu on 2022-08-01
Recovering deleted files on Linux loses the names of those file system objects.  They are restored as f12345678 ... and it is up to the person restoring to create a file name.
There might be 20+ versions of the same file restored, so it is up to the person restoring to know which is the latest.
Also, if any file system blocks have been reused, the file restore will stop there, so it is common for restored files to be truncated.

There's no replacement for daily, automatic, versioned, backups.  If you want them more often, using an advanced volume manager like LVM or file systems with built-in "snapshot" support would be smart - those are ZFS and BTRFS.  Snapshots mark blocks as frozen. They aren't backups, but they help backups to be performed.  Creating a snapshot for a file system is nearly instantaneous. The block list gets a name so we can mount that "named snapshot" read-only and use it to make 100% clean backups.  

When many backup tools claim to make a "snapshot", they are doing something different.  **Timeshift uses real snapshots for backups, but only if the underlying file system is btrfs.**  For any other file system, it used rsync to copy the files/directories to other storage. This copy can take 2 hrs or 2 minutes, but while it is happening, the source files can be open and modified. That's how backups become corrupted, especially for active databases.  That is a flaw for nearly all backup tools that aren't volume manager aware.  

If using ZFS, there are some well tested scripts that will create then transmit snapshots to a different system as backups. It is freakin' amazing.  There must be a few hundred ZFS backup scripts. Google "zfs backup scripts".  [https://github.com/jimsalterjrs/sanoid](https://github.com/jimsalterjrs/sanoid) is one of the most popular, created by a guy with a long history in storage. He's also a writer for Ars Technica.  KVM + ZFS =  functionally immortal systems.  Of course, most people here won't be using ZFS (and probably shouldn't at this point).

Sorry, probably more background that anyone wants, but I type fast. ;)

There's never any replacement for having excellent backups. Guess that's my point.  Counting on a data recovery process isn't a good idea.

---

