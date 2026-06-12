---
title: "Make use of NTFS partitions to save files in Ubuntu"
date: 2019-12-04
forum: New to Ubuntu
---

### Post by valletosh97 on 2019-12-04
Hello everyone, I am new to Ubuntu, I want to try to install ubuntu on my pc, and I have everything clear with the standard way to install. The question or doubt that still does not let me install and test ubuntu is how to make the / home directory where user data is stored, save data in an NTFS partition where I am currently saving all my files?

I am currently using Windows 10 and I partitioned my data in case there was a problem. And I want that now that I will use Ubuntu, not losing the partition or having to format so that ubuntu can save files like music, videos or documents as directory / home.

I read in some forums questions about ubuntu that you could make a small / home directory or that was within "/" and link the directories that are in the other partition so that ubuntu defaults to those directories but I don't know how to I haven't installed it yet and I'm new to Linux in general.

Any help would be greatly appreciated, since I also want to do the same with a laptop to which I will install linux mint.
I enclose the disks that I am using as partitions for personal data use.
HTML Code:

[https://ibb.co/TkFwBgL](https://ibb.co/TkFwBgL)

---

### Post by wildmanne39 on 2019-12-04
Hello and welcome to the forum, you have posted in an English only sub-forum, in the future please translate your message before posting or you can post in your own language if we have a sub-forum that is in your language:

[https://ubuntuforums.org/forumdisplay.php?f=183](https://ubuntuforums.org/forumdisplay.php?f=183)

---

### Post by oldfred on 2019-12-04
Back when I had XP, I had a shared NTFS data partition and shared ext4 data partition. Now I do not have Windows and all the data that was in the NTFS partition is now in ext4 partition(s). 

       [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by yancek on 2019-12-05
If your purpose is to share and to be able to access music, video and other documents between windows 10 and Ubuntu, I think you would be better off creating a separate /data partition formatted ntfs.  Ubuntu/Linux systems can access and write to ntfs partitions while a default windows system can not read/write to a Linux filesystem.  Your /home partition, if you create a separate one, needs to have a Linux filesystem as there are numerous configuration files stored there.  

Since you have not yet installed Ubuntu, I would suggest you read the documentation on dual booting with windows 10 at the link below.  

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by TheFu on 2019-12-05
Assuming the NTFS "data" partition is mounted inside Ubuntu, perhaps to /Data, then inside there you'd have 
Downloads/ Documents/ Videos/ Pictures/ as subdirectories.

Next you'd make symbolic links from your HOME on an ext4 partition to those locations.  On all Unix systems there is help for every command via manpages.  ln is the command (el n), so **man ln** is how you can find information about the command and all the options.

Assuming /Data/Documents exists, 

Caveat, there cannot be a "~/Documents" directory already, so you'll want to move it to a different name.
```
mv ~/Documents ~/Documents.orig
```

```
# Make a symbolic link to your HOME
ln -s /Data/Documents ~/
```
or
```
ln -s /Data/Documents ~/Documents
```, but I'm lazy. Why take a chance on mistyping the target name?

Do similar commands for each directory you want to be accessible from $HOME that are stored elsewhere.

$HOME is an environment variable setup based on the passwd entry at login.  For me, 
$HOME == ~/ == /home/thefu == ~thefu/
Those are all the same.

NTFS is fine for pure data, but cannot be used for files that require full Unix permissions or files or directories to have varied permissions.  For non-Linux file systems, all permissions for files and directories are set via mount options, which is highly limiting.  NTFS is a security risk.

---

### Post by SeijiSensei on 2019-12-05
You can't use an NTFS-formatted filesystem for /home since NTFS doesn't support some *nix filesystem primitives like hidden ("dot") files and symbolic links. As others have said, if you want to create a filesystem to share files between Linux and Windows, create a separate partition, format it as NTFS, and mount it in another root-owned location like /data.

---

### Post by valletosh97 on 2019-12-21
Thank you very much for your comments. I already solved the problem by editing the file $ HOME / .config / user-dirs.dirs. Sorry for my English, it's bad and I had to translate with Google. :)

---

