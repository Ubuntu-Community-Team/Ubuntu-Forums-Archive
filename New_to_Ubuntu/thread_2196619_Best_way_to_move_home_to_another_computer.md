---
title: "Best way to move /home to another computer?"
date: 2013-12-30
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2013-12-30
I have read many threads on various forums on how to do this without any clear result on the best way to go, so thought I would post the topic and seek current guidance.

Oldcomputer runs 10.04 which is no longer supported, so have installed 12.04 (latest LTS) on newcomputer and modified the desktop on newcomputer to look as much as possible like 10.04. (I tried Unity and literally spent hours trying to figure out how to do things that were simple under 10.04), so have a Gnome (no effects) appearance. (This is mentioned in case it affects how the move should be done.)

1) One approach would be to create a tarball of /home on oldcomputer, then move the tarball to newcomputer, then unpack the tarball in /home on newcomputer. (There are several issues for me to resolve before I can do this, but will address them after determining that this is the preferred approach.)

2)I have seen recommendations to set up SSH and use rsynch to copy the files to the new location rather than use tar.

Which would you recommend and what advantages over the other are there?

---

### Post by buzzingrobot on 2013-12-30
Perhaps you've seen this, but here is a page on the Ubuntu wiki about moving /home: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving).  Note that it addresses /etc/fstab and other points.  I've followed it with success moving the partion from one disk to another on one machine.

Here's a link on using dd and gzip to back up a partition: [http://wiki.rosalab.ru/en/index.php?title=How_To_Backup_a_Partition](http://wiki.rosalab.ru/en/index.php?title=How_To_Backup_a_Partition). Given a large enough USB stick or other medium, you could copy the compressed archive to it and expand it on the new machine.

The choice of method might come down to what you want to preserve.  If it's just the actual content of /home, that's one thing.  If you want the content and you want permissions, ownerships, etc., to remain the same, you'll need to be sure the technique you use preserves them.

---

### Post by whitesmith on 2013-12-30
As #buzzingrobot's post implies you can't backup to a Win format medium if you need to preserve permissions, so you'll need an ext3 or ext4 partition to grab everything. You might want to look into "Move /home to it’s own partition"  ([http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)). I can vouch for this methodology, having used it several times to separate /home from everything else. Cheers!

---

### Post by Odyssey1942 on 2013-12-30
Thanks for these links. Very helpful.

> Here's a link on using dd and gzip to back up a partition: [http://wiki.rosalab.ru/en/index.php?...up_a_Partition](http://wiki.rosalab.ru/en/index.php?...up_a_Partition).

In that link, it is mentioned:

> Note: If you are creating a backup copy of a partition when someone is writing files on it, then the filesystem in your backup can be damaged!

Firstly how would you know if anything is changing in any way, whether someone is writing files on it or the system is updating or a webpage is refreshing, etc? How does one avoid this possibility?

> In order to check what is included in your backup copy, extract the data of even modify/update it, mount the backup file using the 'loop' option: mount -o loop backup_file /mnt/folder

Secondly, I do not understand this, especially "extract the data of even modify/update it", but also the mount instructions. Can you elaborate/clarify please?

Then yours: > Given a large enough USB stick or other medium, you could copy the compressed archive to it and expand it on the new machine.

Are there not some issues having to do with FAT32 (which most USB drives are formatted as)? Does one need to reformat to EXT4 (which is what I use on both machines) before the copy, then format it back to FAT32 after?

Then > The choice of method might come down to what you want to preserve. If it's just the actual content of /home, that's one thing. If you want the content and you want permissions, ownerships, etc., to remain the same, you'll need to be sure the technique you use preserves them.

Since I am not likely to know if I needed to preserve permissions, etc until somewhat after the fact, shouldn't I plan to preserve them JIC? Which method preserves these?

Also that prompted me to look at the contents of /home on oldcomputer and I find:

lost+found
username              [size is 20.2 GB]
usernameorig        [size is 20.6 GB] this is basically a tarball of 20.6 GB which is probably the original tarball which was unzipped to move /home to this computer back when it was first set up.
usernamex            [size is    5.2 GB] unsure what this is but all files dated prior to the date of the tarball

I don't want to include either of 'orig or 'x when I copy, so how do I insure that only username is either copied or tarballed as the case may be?

---

### Post by buzzingrobot on 2013-12-30
Think hard about what you really need to do here before it gets unnecessarily complex. 

Since you already have the new 12.04 system created and configured, there is already a /home partition on it. You are copying from a 10.04 system to a 12.04 system. Those are two very different environments.  The configuration files in your 10.04 /home folder -- the hidden files --  are unlikely to be of much use to 12.04, or even understandable, and could easily overwrite the new configuration you labored to create. 

So, you actually want to avoid recreating the old /home/username on the 12.04 system.  All you need to do is copy over the folders and files in /username.  How you do that depends on the size of /username and the size of the medium used to make the transfer.  If /username is smaller than that medium then a simple copying (check out cp's man page) would work.  if not, you would need to created an archive of /username and compress it so it might fit on the USB drive or other device. (You could even drag and drop with the file manager, on both ends, which would greatly simply things.)

Here's one scenario:  Let's say the old /username fits on a USB stick without compression. And, a new /username is on the 12.04 machine. Open the USB in one window of the file manager and /username in another, on the 10.04 machine.  Drag and drop old /username to the USB. When the copy is done, attach the USB to the new machine and open it in the file manager.  Open another file manager window to the new 12.04 /home/username. Drag and drop everything below *old* /username to *new* /username.

No matter how it's done, expect at least a few bumps and some manual tweaking after the copy.

---

### Post by Impavidus on 2013-12-30
If you copy all files to a fat32 usb stick, permissions won't be conserved. However, if you put everything in a tarball on a fat32 usb stick, permissions can be conserved (except for the permissions of the tarball, but you don't need those). First delete everything you don't need, like caches, compiled files that can be recompiled (you'd have to do so anyway on the new version of Ubuntu). Then,```
tar -czf /media/yourusbdrive /home/username
```You may need some additional tweaking, to skip the configuration files which won't be of much use on 12.04 and to properly set ownership and permissions on extraction. Have a look at the manual page. As you don't have a lot of data to move, this may be the quickest way.

---

### Post by Odyssey1942 on 2013-12-30
> Think hard about what you really need to do here before it gets unnecessarily complex.

Buzzingrobot, thanks for your good counsel on this, and that is exactly what I am trying to do. Up to this stage, I have not been so much concerned about how to do it as what I should do.

> The configuration files in your 10.04 /home folder -- the hidden files -- are unlikely to be of much use to 12.04, or even understandable, and could easily overwrite the new configuration you labored to create... and...
All you need to do is copy over the folders and files in /username

If I understand yours, I could copy all folders and files except any starting with a "."?  Further, the drag and drop scenario/illustration you gave will accomplish just that (i.e. excludes the .directories)? If this is not correct, please clarify for me.

There is so much discussion in the various forums about permissions, for example, yet yours did not mention it, while Impavidus did. Does your scenario preserve permissions? I ask because Impavidus appears to confirm my concern about using a USB drive as mentioned above.

Impavidus, Thanks for yours. Could I accomplish the tar creation you suggest with:

```
tar cpf /home/user/backup-user/131230home.tg --exclude=/home/user/.Trash --exclude=/home/user/.thumbnails /home/user
``` and, incorporating buzzingrobots guidance, would also exclude all of the rest of the .directories (which for brevity I did not include in the code)?

(Also I added "p" to preserve permissions, and removed the "v" and "z" just to keep this to the bare minimum for discussion purposes)

As you both can see, I am unsure about permissions and hidden files therefore uncertain which method is better for me. Buzzingrobot's approach is certainly very simple to understand and implement if it does the things I have asked about.

[BTW, I have looked at the man pages and simply do not understand them.]

---

### Post by C.S.Cameron on 2013-12-30
Several years ago I cloned my wifes HDD to an external HDD so she could boot her system from my laptop while we travel.
Each year I update her home on the external before departing and on the internal upon returning.
What works for me is to copy/update home from the old drive to the new drive using grsync, (a GUI for rsync).
Then I do a sudo chown -R hername /home/hername].

Edit:
This worked fine going from 10.04 to 12.04 also.

---

### Post by Impavidus on 2013-12-31
I think the -p option to conserve permissions must be used on extraction of the archive, not on creation. You need a dash before the -p, -f and -z options. That it's only optional for the c or x is a historical curiosity. Best not create the archive in the directory you're archiving, but create it on the usb drive directly. Otherwise your command seems fine to me.

---

### Post by buzzingrobot on 2013-12-31
I just did a quick test here.  If I drag a folder, the hidden files go with it.  I.e., Click and hold the icon for folder "Foo" and drag it to a new location and all the files in it will transfer, including the hidden files.

But, if I open the file, select all the contents (crtl-a will do that) and drag that to a new location, the hidden files are copied only if the "Show hidden files" option is selected.  I.e., if "Show hidden files" is on and the hidden files are visible, then if they are selected they will be transferred.  If the option is not selected, the hidden files will not be seen, cannot be selected, and not transferred.

(BTW, the business of hiding files by prefacing the name with a '.' is a convention from the earliest days of Unix. They are hidden in the sense that you won't see them in a directory listing unless you specifically opt to see them.  It's a way of keeping things tidy and, if the user can't see the files, the user is less likely to accidentally remove or alter them.)

Remember, any hidden files that do transfer can be removed manually. It's possible there are some you want to copy because you've edited them and want to keep the edits. (That's one reason why it's impossible to give a definitive "Do This and Only This" answer.)

The tar invocation you showed looks correct to me. You can test it with a smaller folder and some dummy files first, perhaps.

As I  said, files you don't want can be deleted after the copy. (Or before, if you aren't going to use the 10.04 machine.) 

The tar invocation is the safest, and drag-and-drop probably the easiest. Your data will be copied in both cases.  If permission and ownership issues do crop up later, they can be resolved.  That's annoying, though, and can be prevented by creating the tar archive.

---

