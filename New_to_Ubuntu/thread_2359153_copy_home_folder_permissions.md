---
title: "copy home folder permissions"
date: 2017-04-21
forum: New to Ubuntu
---

### Post by fattyz on 2017-04-21
Hi all,

I need to copy my home folder from my old ubuntu laptop to my windows pc and then I can get it onto my new laptop.  I want compiz fusion and emerald and all my settings to transfer over so I don't have to "learn" how to set it all up again.  The old laptop has no working usb ports or wifi.  The wired network is ok though.  The home folder is too large to fit on a dvd.

I am trying to drag and drop the home folder onto the public folder on a windows pc networked.  I'm fairly sure this can not be done and must be done in terminal?  I get the following error, "ERROR WHILE COPYING The folder &#8220;.gvfs&#8221; cannot be handled because you do not have permissions to read it."  Please could someone help me with this?  Although I have been using Ubuntu for a long time when I need to do this kind of thing years have gone by and I don't remember anything about how it works.

Thanks in advance

---

### Post by TheFu on 2017-04-21
Welcome to the forums.

.gvfs can be ignored. 

Why not just use the restore process from your backups? Seriously, this is an ideal time to validate that your backup/restore stuff is working!

The reason we don't usually explain things with GUI tools here is that is too much work - too many copy/click/paste/click and useless waste of bandwidth. Basically, 1 command can do the task you want.  Not using the shell is like trying to swim with 1 arm tied to both your legs. It is about 10% of the power that Unix has to offer in the GUI.

Put both laptops on the same network. Setup ssh between them - after all all great networking in the *nix world starts with ssh. Then use 
```
$ rsync -avzp ~/    other-machine:~/
```
# 'other-machine' is the hostname or IP of the other machine where you want all the files to be copied.  
# This assumes your usernames match between the systems. If not, there are options. *man rsync* will explain.
# if you've setup ssh-key based authentication, then you will only be prompted for a password the first time, until the timeout period happens. That is configurable.

**ssh** and **rsync** are basic tools that every Unix/Linux user should know, IMHO.  They are like the wheel and fire for the Unix world.

I have no clue how to do this easily if Windows has to be in the middle - I suppose **tar** or **gtar** or **star** could be used, not rsync. The trick is to get the permissions. Going through Windows would lose the permissions if they aren't embedded inside the archive. Different files/directories have different permissions and if those are not handled correctly, you could easily end up with a userid that is broken or highly non-secure or both.

If you are interested in learning Linux, [https://linuxjourney.com/](https://linuxjourney.com/) has a nice intro - it is almost a game.

---

### Post by SeijiSensei on 2017-04-21
I recommend creating a tar archive of your home directory, copying that to Windows, then copying it back onto the new machine and untarring it.  Let's start with step one:
```

cd /home
sudo tar czvpf fattyz.tgz fattyz

```
That creates a complete archive of /home/fattyz including hidden files and directories.  The "p" switch to tar preserves permissions, etc.  Now copy fattyz.tgz to the Windows machine. When you have the new machine set up, copy the file to the /home directory, then run
```

cd /home
sudo tar xzvf fattyz.tgz

```
The "v" switch creates a list of the files archived or unarchived.  You can omit it if you like.  The "z" switch uses gzip compression.  If you're short on disk space on the Windows machine, you can try replacing "z" with "j" to use the slightly more efficient bzip2 compression algorithm instead.

---

### Post by fattyz on 2017-04-22
Thx, the copy operation started anyway after the error message.  I will let you know if I am able to get the folder over onto the new computer and if it works!  I found vmware vcenter converter and was going to try and make a virtual machine out of the laptop but was having connection problems over the network.  I will update this tonight thanks very much again.

FattyZ

---

### Post by oldfred on 2017-04-23
If you did not follow either of the suggestions above, you will probably lose all ownership & permissions as Windows formats do not support them.
If copied to FAT32 you also truncate any file over 4GB.

If just /home and your data, you probably can just restore permissions.


If moving it, and manually creating new /home, some details:
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

 Ubuntu /home is permissive:
[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)
sudo chown -R $USER:$USER /home/$USER
sudo chmod -R a+rwX,o-w /home/$USER 
Do not run on any system partition other than /home. -R is recursion and all lower levels also are changed.


Some other issues:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

