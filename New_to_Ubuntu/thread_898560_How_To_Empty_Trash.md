---
title: "How To: Empty Trash"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by drs305 on 2008-08-23
[COLOR="MAROON"]**[SIZE="4"][CENTER]*Disk Full? - Check Your Trash Bin(s)*[/CENTER][/SIZE]**[/COLOR]

**[COLOR="DarkGreen"][SIZE="3"]In a Rush? Go Directly to #6 ...[/SIZE][/COLOR]**

**[COLOR="Navy"][SIZE="3"]1. Error Messages - Why You Are Here?[/SIZE][/COLOR] **
*"There is not enough room on the disk to save ..."* Perhaps you received an error message. Maybe you have tried but cannot delete the contents of the Trash bin. Perhaps you looked at your system files and realized that you were running out of disk space. Emptying the trash has been a tradition throughout the world since long before computers were invented. Over time we sometimes forget to do perform this important task. 

With computer trash, you have to not only remember to delete, you must know ***[COLOR="DarkRed"]how[/COLOR]*** to do it. If you cannot explain why you are running out of hard drive space, it may be because you haven't emptied the trash - properly, often enough, or perhaps both! Read on.

**[COLOR="Navy"][SIZE="3"]2. Checking Your Partition[/SIZE][/COLOR] **
Here are some of the many ways to check your free space. Each has its advantages. Use the one or combination you like the best.
[LIST]
[*]**[COLOR="DarkRed"][B][SIZE="1"]df - Th | sort[/SIZE]**[/COLOR][/B] (Terminal)
```

/dev/sda1     ext3     23G  9.6G   12G  46% /
/dev/sda2     ext3     34G  2.1G   30G   7% /home
/dev/sdg2  fuseblk    965M  5.4M  960M   1% /media/test
Filesystem    Type    Size   Used   Avail   Use%   Mounted on

```
Note: "sort" will order the partitions alphabetically. The "T" switch shows the file type - you can omit it if desired. If used, ntfs partitions will show type: "fuseblk".
 

[*]**[COLOR="DarkRed"][B][SIZE="1"]Gnome-Device-Manager[/SIZE]**[/COLOR][/B] (GUI)
System, Administration, System Monitor (gnome-system-manager) 
```

Device      Dir     Type   Total     Free      Available   Used     %
/dev/sda2   /home   ext3   33.1GiB   31.1GiB   29.4GiB     2.0GiB   6%

```


[*]**[COLOR="DarkRed"][B][SIZE="1"]Disk Usage Analyzer[/SIZE]**[/COLOR][/B] (GUI)
Applications, Accessories, Disk Usage Analyzer.
This is a graphical app that displays hard drives and partitions.
While DUA is a valid tool, it often brings up questions about its use. Here are a couple of things to keep in mind:
[LIST]
[*] One common question is why DUA seems to show twice as much space as the partition contains. By default DUA It displays the .gvfs (gnome virtual file system) folder contents. To get an accurate picture of the actual/physical contents, uncheck ".gvfs" via Edit, Preferences.
[*] The top directory will *always* show 100% full. The percentages of all the folders adds up to 100%. It does not mean there is no space left on the drive/partition.
[/LIST]
[/LIST]
 
**[COLOR="Navy"][SIZE="3"]3. Free Space - Where Did It Go?[/SIZE][/COLOR] **
[LIST]
[*]Has it been a while since you deleted your Trash bins?
[*]Do you regulary install and then uninstall apps without using dpkg/apt/synaptic/Add-Remove?
[*]Do you have a particularly small partition, such as /boot?
[*]Are you sure you understand what the computer is telling you?
[*]Have you wondered why your disk size seems under-reported? (See # 8 ).
[/LIST]

**[COLOR="Navy"][SIZE="3"]4. Trash Characteristics[/SIZE][/COLOR] **
Under normal circumstances, only files/folders deleted with the terminal "rm" command or via the Shift-Del key combination in file browsers such as nautilus or thunar are immediately erased - freeing up disk space. The rest go to a trash bin, where deleted materials remain until the bin(s) are emptied.

The Trash folders are hidden. If using the "ls" command in the command line, you must include the "-a" switch (ls -a). In nautilus or other file browsers, you must have "view hidden files" enabled (nautilus = Ctrl-H).

There are two folders within the Trash bin - "info" and "files".
[LIST]
[*]*info*: The "info" folder contains information regarding the files contained in the "files" folder. Each deleted file has an entry in the "info" folder, containing the deletion date and path. 
[*]*files*: This folder contains the actual deleted files.
[/LIST]

**[COLOR="Navy"][SIZE="3"]5. Why Must I Delete Trash?[/SIZE][/COLOR] **
***[COLOR="DarkRed"]Until the trash bins are emptied, deleted items continue to take up disk space just as a normal files do. The space containing these deleted items cannot be used as long as the deleted files reside in Trash bin(s).[/COLOR]***

If you want proof, find a suitably large file and make a copy of it. Using any of the methods above, review the free and used disk space and then delete the file via a file browser or right click/remove in a file browser. Reheck the results. You will notice the used and free space have not changed. The reason is because the deleted files in a Trash bin are still intact - they have only been moved to a different folder.

**[COLOR="Navy"][SIZE="3"]6. Okay, Where Are the Trash Files?[/SIZE][/COLOR] **
Here is where these files normally reside.

[LIST]
[*]**/home/*username*/.share/local/Trash**   User's Trash (hardy and later)  
[*]**/home/*username*/.Trash**   User's Trash (pre-hardy)  
[*]**/root/.local/share/Trash**        Root Trash (hardy and later)  
[*]**/root/.local/share/Trash**       Root Trash (pre-hardy):  
[*]**/.local/share/.Trash-1000**       NTFS/FAT32/etc: Trash deleted in these partitions is placed in a Trash bin named in accordance with the user deleting the file, e.g. -1000, 1002, -0, etc 
[/LIST]
 
All trash on your system, regardless of where it resides, by default contains the name "Trash". Here is a command that will greatly simplify your task. It seeks out all folders on your system that contain either "trash" or "Trash" while eliminating other files such as "trashapplet". It must be run with root privileges since it will be searching the system files. It does not require root privileges to be run on your home partition. It searches your entire system, so it may take a few minutes and may initially produce 

```
[SIZE="5"][COLOR="DarkRed"]**sudo find / -type d -iname *Trash* | grep Trash**[/COLOR][/SIZE]
```
[LIST]
Here is an example run on my computer:
```

~/Desktop: sudo find / -type d -iname *Trash* | grep Trash
/media/data/.Trash-1000
/home/username/.local/share/Trash
/home/.Trash-0
/root/.local/share/Trash

```
[/LIST]

**[COLOR="Navy"][SIZE="3"]7. How Do I Delete Trash and Free Up Space?[/SIZE][/COLOR] **
[LIST]
[*][SIZE="2"]The Safe Way: File Browser with Administrative Powers[/SIZE]
[LIST]
[*]**[COLOR="DarkRed"][SIZE="1"]gksudo nautilus[/SIZE][/COLOR]** (Terminal)
[LIST]
[*]Do not use "sudo". Sudo is meant to be used for terminal commands and processes. This command, even though run in terminal, will open a gui application. "gksudo" is the appropriate command.
[*]You can start nautilus with the folder path ( *gksudo nautilus ~/.local/share/Trash* ) It is necessary to navigate to each Trash folder to delete it's contents.
[*]Use Shft-Delete to delete individual folders/files. Confirm the "permanent delete" message. If you just hit the Delete key, the folders/files will be deleted and moved to the .... Trash/files folder! If you delete the parent *Trash* folder, this is not necessary. A simple press of the Delete key will remove the Trash folder and subfolders.
[*]You may delete the entire Trash folder. It will be created the next time an item is deleted.
[/LIST]
[/LIST]

 
[*][SIZE="2"]The Efficient Way: Command Line[/SIZE] (with "chown" when required)
[LIST]
[*]**[COLOR="DarkRed"][SIZE="1"]Using the Terminal.[/SIZE][/COLOR]** By using commands in terminal you can quickly delete all user-owned Trash folders. Using the command line combines ease of use with a bit of risk. 

**[COLOR="Red"]You must ensure you have correctly input the command. Files deleted with the "rm" command are generally NOT recoverable![/COLOR]**
 

[*]**To delete *your* Trash contents in your home folder:**
```
**[COLOR="DarkRed"]rm -rf ~/.local/share/Trash/*[/COLOR]** 

```

[*]**To delete *root's* Trash contents in your home folder**:
Sometimes root trash ends up in your local Trash bin. You cannot delete this without administrative powers. To accomplish the task, use "sudo" to change ownership of the Trash folder contents to the user, then delete the folder as above:
```
[COLOR="DarkRed"][B]
sudo chown -R *yourusername* /home/*yourusernameA*/.local/share/Trash
rm -rf ~/.local/share/Trash/*[/COLOR][/B] 

```
 
[*]**To delete *root's* Trash contents in root's Trash bin:**
I recommend using nautilus or another file browser, opened with root privileges, to accomplish this task. Using the command line to delete system Trash is safe *only if* the command is entered properly. A mistake could possibly erase system files and render the system unusable.  

There are commands which will directly delete root trash using "sudo rm -rf" but I will not reproduce them here. A safer method is again to change the ownership to yourself and then delete the Trash. Of course, if you enter the wrong commands twice you can still destroy your system...

We will again use "sudo" to change ownership of the Trash folder contents to the user and then delete the folder as previously:

```
[B][COLOR="DarkRed"]
sudo chown -R *yourusername* /root/.local/share/Trash/*
rm -rf ~/.local/share/Trash[/COLOR][/B] 

```

[/LIST]
[/LIST]
 
**[COLOR="Navy"][SIZE="3"]8. Other Ways to Regain Space[/SIZE][/COLOR] **
Briefly, here are some other methods to reclaim space on your partitions. These commands are run from the terminal.

[LIST]
[*]**[COLOR="DarkRed"][B][SIZE="1"]sudo apt-get clean[/SIZE]**[/COLOR][/B]
Empties all the packages from /var/cache/apt/archives. The archives folder in general contains the .deb packages of installed apps. It can grow quite large. Current packages can be downloaded via synaptic if they need reinstallation. There is program called [APTonCD]("http://aptoncd.sourceforge.net/") that can save these packages to a cd/dvd if desired.

[*]**[COLOR="DarkRed"][B][SIZE="1"]sudo apt-get autoclean[/SIZE]**[/COLOR][/B] 
Empties all expired packages from /var/cache/apt/archives that are no longer available for download.

[*]**[COLOR="DarkRed"][B][SIZE="1"]sudo apt-get autoremove[/SIZE]**[/COLOR][/B] 
Removes packages that were installed to satisfy dependencies for other apps but which are no longer needed.
[*]**[COLOR="DarkRed"][B][SIZE="1"]localepurge[/SIZE]**[/COLOR][/B] 
By default a number of language packages are installed on the system. On a full disk the space can be noticeable. *localepurge* can be installed and run to remove and prevent future installation of extra language packages that you do not use. Install it using the command "sudo apt-get install localepurge". Read the man page for warnings about it's use.
[*]**[COLOR="DarkRed"][B][SIZE="1"]deborphan[/SIZE]**[/COLOR][/B] 
This app locates unused libraries and is installed with "sudo apt-get install deborphan". It can also be set up in synaptic.  
[*]**[COLOR="DarkRed"][B][SIZE="1"]tune2fs[/SIZE]**[/COLOR][/B] 
If you *really* need to free up space, *tune2fs* can free up some space by reducing the 'reserved blocks' used for journalling and other system use. By default, 5% of the disk space is reserved for system use. There is a reason for having this space, but if you feel you must reduce the percentage you can run "sudo tune2fs -m X /dev/*partition*" where *m* is the desired percentage. (Example: sudo tune2fs -m 3 /dev/sda1)
**[COLOR="Navy"]Note: This reserved space accounts for the disparity between a disk's actual capacity and that reported by disk management commands and apps. The reserved space is often not reported and thus the drive/partition appears to have 'lost' some of its capacity. [/COLOR]**

[/LIST]

**[COLOR="Navy"][SIZE="3"]9. A Few Tips About Trash[/SIZE][/COLOR] **
[LIST]
[*]If your user Trash icon is not displayed on the Desktop, try this. Change the value to "false" to hide it.
```
[COLOR="DarkRed"]**gconftool-2 --type bool --set /apps/nautilus/desktop/trash_icon_visible "true"**[/COLOR][/B] 

```
[*]If the .Trash-1000 (or user's id if different) folder exists in ntfs/fat32 partitions the contents should be displayed in the user's Desktop Trash bin.
[/LIST]



[COLOR="MAROON"]***[SIZE="2"]Other Useful Trash-Related Links:[/SIZE]***[/COLOR]
[SIZE="1"][HOWTO: Cleaning up all those unnecessary junk files]("http://ubuntuforums.org/showthread.php?t=140920&highlight=trash")
[HOWTO: Automatically regulate the size and age of your Trash folder]("http://ubuntuforums.org/showthread.php?t=698649&highlight=trash")
[A send-to-trash command for the shell. ]("http://ubuntuforums.org/showthread.php?t=124137&highlight=trash")[/SIZE]

---

