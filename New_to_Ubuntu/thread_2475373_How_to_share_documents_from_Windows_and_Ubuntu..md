---
title: "How to share documents from Windows and Ubuntu."
date: 2022-05-24
forum: New to Ubuntu
---

### Post by daring-t on 2022-05-24
Hello, I have a SSD that has a Windows partition, a personal partition and the reset for Ubuntu partitions. In windows you can change to path of Document, Pictures, etc. to a different directory path. I don't see a way to change the directory path for those folders in Ubuntu like Windows. Is there a way to remap Documents and other Personal folders?

Also what file system do you recommend for this personal partition that would be used by both Windows 10 and Ubuntu?



Thanks,
Daring_t

---

### Post by Impavidus on 2022-05-25
The simplest way is to replace those directories (Documents, Download, Music etc.) with symbolic links to the directories you want to use. I think it's also possible to make changes in ~/.config/user-dirs.dirs, but I never tried that myself.

Use an ntfs filesystem. It's what Windows understands. Use fstab to mount it automatically at boot time.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by ActionParsnip on 2022-05-25
+1 for symlink to the folders in the mounted NTFS. Super easy

---

### Post by daring-t on 2022-05-26
Sorry about not getting back to you on this post. I'm still new to Linux and I looked up how to create a symbolic link I ran the following command: 
sudo ln /media/daren/Personal/Documents ~/Documents

and got this message:

ln: /media/daren/Personal/Documents: hard link not allowed for directory

Do I have to change how its mounted so it does not show up as portable device like a Flash Drive or DVD? 


Thanks,
Daring_t

---

### Post by oldfred on 2022-05-26
My last Windows was XP and I had both NTFS & Linux partitions with data. The NTFS had some I wanted to share and the Linux partition the files I only needed in Ubuntu.
I now only have Ubuntu, but have multiple installs, mostly test or experiments on different settings where I do not want to modify my main working install. But I often then want my data. So I now have a data partition that I link into all my installs.

[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by Impavidus on 2022-05-27
1: When you mount the data partition by clicking it in the file manager, it gets mounted on /media/username/devicename/. It's where removable drives are mounted. This is not the most convenient place to mount it when doing so automatically using /etc/fstab, as it may interfere with the things done automatically by the file manager. Many people mount such data partitions at /data or something like that. You can take any empty directory you like, as long as it's not in a directory that already has a specific purpose.

2: You create the symbolic link in your own home directory. You can write there, so there's no need for **sudo**. Don't use **sudo** when you don't need it and don't use it when you don't know why (yes, that takes some time to learn).

3: **ln** without any further options creates hard links. You cannot create hard links to directories and you cannot create hard links to targets on another partition. That's why you need a symbolic link, using the -s option:```
ln -s /data/Documents ~/Documents
```Change that command to fit the mountpoint you choose.

---

### Post by daring-t on 2022-05-27
1. Thanks for the assistance. I do need to make my disk mount more permanent.
2. Yes I am a noob and I don't know when I should and should not use **sudo**, I am going to be mainly using Ubuntu instead Windows for coding.
3. I do need look into how **ln** works and what the arguments do, but thank you that worked


Again Thanks,
Daring_T

---

### Post by Impavidus on 2022-05-28
Have a look here:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

What it means in practical terms, is that you need sudo when you want to write to some file/directory where the ordinary user has no write permission. Creating, deleting or renaming files or directories counts as a write operation on the directory containing them. For editing files with root permissions, we recommend to use the sudoedit command. This will copy the file to a temporary location, allow you to edit it and copy the edited file back. It's better than running the text editor as root (which is what many guides still recommend).

Every command has a manual page. In the terminal, you can read those manual pages with the man command. To view the manual on ln, run```
man ln
```Scroll with arrow keys, close the manual with q. Manuals pages aren't always easy to read, but very useful. By reading them with the man command (and not on some website), you know for sure you're reading the manual for exactly the same version of the command as installed on your computer.

---

### Post by daring-t on 2022-05-29
Do you have to create symbolic links for all folders or is there a way to map everything that is in Documents to my Personal partition. In Windows 10 if you go to Documents>Properties>>location it will remap anything in Documents to the the path specified. This is what I'm looking for in Ubuntu.

A bit of a janky way of doing this would be is to make the \home my personal data partition and install a driver on Windows 10 that will let me access that partition in Windows 10. Then remap my Pictures, Documents, etc. to my \home partition. 

If there's a better solution to this problem or if you need me to reclarify, Please let me know. 


Thanks,
Daring_t

---

### Post by oldfred on 2022-05-29
As I posted above:
[https://ubuntuforums.org/showthread.php?t=1811198](https://ubuntuforums.org/showthread.php?t=1811198)
All my folders are in /mnt/data

#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

---

### Post by Impavidus on 2022-05-30
Move everthing that's now in your ~/Documents directory to your shared partition, delete the ~/Documents directory, create the ~/Documents symlink, pointing to where you moved your documents to. That's all.

You can do the same for ~/Videos, ~/Music etc., if you wish

---

