---
title: "MS OS File Explorer"
date: 2019-08-06
forum: New to Ubuntu
---

### Post by oskar44 on 2019-08-06
Is there any Ubuntu / Linux OS which has a File Explorer similar the MS?

   
  I have downloaded various OS alternatives and they all are very good alternatives to MS OS except the “File Explorer”. 

   
  The MS File Explorer is unique as you can see in a **hierarchical directory / file system **all your directories / files in one screen and you are able to change, re arrange, re name, add, delete any file or directory on the same screen with a simple cut / paste command.
   
  Thanks

---

### Post by TheFu on 2019-08-06
No.  Unix operating systems care about file permissions, unlike Windows.  It is core to the Unix OS philosophy, which is very different from Microsoft.  Unix is always multi-user. Always.

In general, users should only modify files in their HOME directories. This is normal for Unix systems, unless you work in a team, then your team would have some directories with permissions specifically setup to be modified by all the members of the team. 

As for file managers, you can try out a bunch. There must be 45+ of them.   caja, thunar, nautilus, pcman, dolphin, off the top of my head.  [https://www.tecmint.com/top-best-lightweight-linux-file-managers/](https://www.tecmint.com/top-best-lightweight-linux-file-managers/) says there are 30.

Almost every Linux GUI file manager supports sftp:// URLs, which is very convenient to access files at home when I'm away. Just setup ssh-keys between the laptop and home computer, so the access is much easier and more secure. With ssh working using ssh-keys, all the ssh-related commands will honor them - so ssh, sftp, scp, rsync, rdiff-backup, x2go, and 50+ others.

Don't use **sudo** with any GUI programs.  You've been warned.  I know you won't listen and in 3-26 weeks when the permissions on your OS are screwed up, it is common for the best answer to be wipe the OS, start over, and don't use sudo with GUI programs.  There is no magic script to put permissions back - well, there is - it is called restoring from proper backups.  Unfortunately, most people new to Linux don't do backups and if they do, they only copy off the files, which is only useful for files inside your HOME.  For files everywhere else, you must, must, have the owner, group, and permissions along with the data for a backup to be of any use.

I haven't used MS-Windows outside the 3 things I do with it in years.  I don't notice much difference except that Linux file managers can be extended by little scripts, which Windows cannot. That and Windows Exploder crashes every few days when accessing SMB shares. Scripting is handy when we need to run 82 files through some special processing.  Unix respects the power of the user.

---

### Post by cruzer001 on 2019-08-06
Nemo is what I would call top of the line.  You can try it out.
```
sudo apt install nemo
```
You probably have Nautilus installed.  You do not like it?
What are you running? Ubuntu? what version

---

### Post by sevendogs1337 on 2019-08-06
If OP is looking for a windows explorer file manager look-alike, try "XFE". It is very configurable and powerful. 

Heed TheFu's advice: you should not be renaming, adding or deleting any files in any other directories anywhere other than /home/<your user>.

---

### Post by cruzer001 on 2019-08-06
> **sevendogs1337 said:**
> If OP is looking for a windows explorer file manager look-alike, try "XFE". It is very configurable and powerful. 

Heed TheFu's advice: you should not be renaming, adding or deleting any files in any other directories anywhere other than /home/<your user>.
Funny :D I run XFE but did not think that would suit the OP.  XFE fits nicely in my xWindow system.
```
sudo apt install xfe
```
[http://roland65.free.fr/xfe/index.php?page=screenshots](http://roland65.free.fr/xfe/index.php?page=screenshots)

---

### Post by sevendogs1337 on 2019-08-06
Yeah, XFE was my exclusive file manager in FreeBSD - could script actions, etc, liked it, except for the fact it looked like explorer. I used to configure XFE to be 2 paned and just a directory listing without a tree on each side.

---

### Post by oskar44 on 2019-08-06
Thanks for the heads up on Unix OS
   
  I have 2 laptops and a desktop; one laptop runs Windows10, the other Windows 8.1 and the desktop runs Vista Home 32 bit. 
   
  I&#8217;m experimenting with alternate OS&#8217;s on the desktop and I have installed on it VMware PlayStation where  the following OS&#8217;s are installed: PCLinux Mate, Linux Mint, Cinnamon, ChaletOS and a few others.
   
  The link for the 30+ file managers is very useful and I will try the ones I like
   
  Much appreciated
  Nicolas

---

### Post by mastablasta on 2019-08-07
i am not sure what the issue mentioned in first post it. i use win 10 at work, win 7 on laptop and Kubuntu on all PC (well one is dualbooting windows XP). i can't see any huge difference between Dolphin and explorer or to find something i would miss. 

the only thing maybe was Windows commander/Total commander like file manager which i would normally use on windows machines at home. but even for that there is Krusader, Double commander, midnight commander... and Dolphin also does the job well.

as mentioned you mostly browse (99.99%) in /home anyway.

---

### Post by oskar44 on 2019-08-07
> **mastablasta said:**
> i am not sure what the issue mentioned in first post it. i use win 10 at work, win 7 on laptop and Kubuntu on all PC (well one is dualbooting windows XP). i can't see any huge difference between Dolphin and explorer or to find something i would miss. 

the only thing maybe was Windows commander/Total commander like file manager which i would normally use on windows machines at home. but even for that there is Krusader, Double commander, midnight commander... and Dolphin also does the job well.

as mentioned you mostly browse (99.99%) in /home anyway.

It all depends on the user and for me its a very big issue since 99.99% I'm in the Windows file explorer

I'm not aware of Dolphin and the others mentioned but I will give them a try

---

### Post by mastablasta on 2019-08-08
> **oskar44 said:**
> 
  The MS File Explorer is unique as you can see in a **hierarchical directory / file system **all your directories / files in one screen and you are able to change, re arrange, re name, add, delete any file or directory on the same screen with a simple cut / paste command.


i still don't understand. this is possible in all file managers. well at least all default ones. can you maybe attach a screenshot of what you want to have/see in file manager?

btw you can't rearrange stuff from windows install folder for example. or from program files. at least not without admin permission. and even with that permission, you will break the OS if you freely cut and paste files elsewhere.

linux doesn't have the OS install folder. more on linux file system: [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
so in any case the system files will be locked (need admin access), the user files will be available for moving around freely.

article on Ubuntu admin permissions: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
sudo manpage: [http://manpages.ubuntu.com/manpages/bionic/man8/sudo_root.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/sudo_root.8.html)

---

