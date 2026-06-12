---
title: "recreating folders"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by kingcobraa on 2014-01-05
Hi,

I have about 570 folders and sub-folders on my disk.

I need to create the exact named copy of folders and sub folders, I  would also need to copy over all files within the folders and subfolders  from origin to destination drive, meaning exclude the files that have the .xyz extension. The reason for this is that I have some  corrupted files which I do not want to transfer over. It is really  important that I get this solved as soon as possible!

Is there a command that can do this quickly?

kind regards

---

### Post by TheFu on 2014-01-05
Yes, there is. I don't have it myself at this instance, but either **rsync** or a **find -exec mkdir -p** command is where I'd start.

I didn't test this, but .... 
```
find $TOP_DIRECTORY -type d -exec mkdir -p {} \;
```
ought to do it. Run it from the directory where you want all the subdirs to be created. Don't expect groups, owners and special permissions to be retained.  Might want to include symlinks (or NOT) and other special ACLs too. Don't know your situation.

That should get you started on a workable path.

Update ... that find command may need to be swapped around ... that is run from the source directory to get relative dirs.

```
find . -type d -exec mkdir -p $TARGET_DIR/{} \;
```
Does that make sense?

---

### Post by steeldriver on 2014-01-05
There's a bunch of hairy-chested ways to do this, however I *think* the easiest way is using rsync, with filters to exclude everything and include directories e.g.

```
rsync -av -f'+ */' -f'- *' /path/to/source/dir/ /path/to/target/dir/
```

see for example [http://www.cyberciti.biz/faq/unix-linux-bsdosx-copying-directory-structures-trees-rsync/](http://www.cyberciti.biz/faq/unix-linux-bsdosx-copying-directory-structures-trees-rsync/)

e.g. to duplicate the directory structure of your Documents directory

```
rsync -av -f'+ */' -f'- *' ~/Documents/ ~/Documents2
```

(rsync creates the Documents2 directory for you - no need to mkdir first)

---

### Post by kingcobraa on 2014-01-05
Hi, please see my edit.

---

### Post by kingcobraa on 2014-01-05
hi i tried the commands and get errorsrsync -av -f'+ */' -f'- *' /home/downloads/All workouts/ /home/desktop/all workouts/
sending incremental file list
rsync: change_dir "/home/downloads" failed: No such file or directory (2)
rsync: link_stat "/home/desktop/all" failed: No such file or directory (2)

sent 2074939 bytes  received 1729 bytes  1384445.33 bytes/sec
total size is 0  speedup is 0.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]

---

### Post by TheFu on 2014-01-05
> **kingcobraa said:**
> Hi, please see my edit.

Copying all files is exactly what rsync is for. Use the --exclude option to prevent specific file patterns.

rsync -avz  --exclude '.xyz' SOURCE TARGET

**man rsync** explains more. Your Linux system already has most answers preloaded.

---

### Post by steeldriver on 2014-01-05
... and put the SOURCE and TARGET directory paths in quotes since you have spaces in them

---

### Post by TheFu on 2014-01-05
> **steeldriver said:**
> ... and put the SOURCE and TARGET directory paths in quotes since you have spaces in them

Most definitely correct. Thanks SD!

---

### Post by oldfred on 2014-01-05
If you look at all the options rsync has it can be very confusing as it has so many. I think you need exclude or filter option to restrict what you copy. I use --exclude but with a file with several folders listed in the file that I do not want to copy.

I use a script for backup but like to list the options I may use, just to remmember what I am doing. Best to use the n option for testing until you are sure you have correct settings.

If a one time thing you do not need script just the one line rsync command.
#!/bin/bash
# backup script - mybackup.sh
# a - archive, retain file settings equals -rlptgoD (no -H,-A,-X)
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
# -l, --links copy symlinks as symlinks
# -i, --itemize-changes
# -t, --times preserve modification times
# --exclude option to prevent copying things

rsync -aruvlP /home/fred/Notebooks /mnt/data/Notebooks
rsync -aurvlP --exclude-from=mybackup_excludes.lst /home /mnt/backup
I do not now use this as my excludes.lst became so long as not to easily be on one line, so I use file like above.
#rsync -aurvlP --exclude '.thumbnails' /home /mnt/backup

Above are in script, so i do not need sudo, but if just running the one command line, you would need sudo.

See man rsync for more info.

---

### Post by Dennis N on 2014-01-05
The structure of the file system is not clear here and really has a bearing on the solution - where are the 570 folders in relation to one another? Are they scattered all about your home folder in various places, or subfolders of another? In any case, the option **--exclude=*.xyz** will omit files with that extension from being copied.

---

### Post by kingcobraa on 2014-01-05
rsync -avz --exclude '.xyz' "home/downloads/all workouts" "New Volume"
sending incremental file list
rsync: change_dir "/home/name//home/downloads" failed: No such file or directory (2)

sent 12 bytes  received 12 bytes  48.00 bytes/sec
total size is 0  speedup is 0.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]

---

### Post by Dennis N on 2014-01-05
> **kingcobraa said:**
> hi i tried the commands and get errorsrsync -av -f'+ */' -f'- *' /home/downloads/All workouts/ /home/desktop/all workouts/
sending incremental file list
rsync: change_dir "/home/downloads" failed: No such file or directory (2)
rsync: link_stat "/home/desktop/all" failed: No such file or directory (2)

sent 2074939 bytes  received 1729 bytes  1384445.33 bytes/sec
total size is 0  speedup is 0.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]

You need **/home/<username>/downloads** not /home/downloads, and **/home/<username>/desktop** not /home/desktop

---

### Post by kingcobraa on 2014-01-05
Basically I want to transfer from source disc to new external hard disk, excluding files with .xyz extension, once the files are fixed they will be transferred over leaving the balance of files to be fixed etc then the fixed ones will be transferred over etc.

---

### Post by oldfred on 2014-01-05
I doubt that "New Volume" is correct for the to location. That also has to be a valid path. If mounted with Nautilus it may be /media/$USER/"New Volume" or /media/"New Volume".
What format is externals drive's partition? If NTFS you will lose ownership & permissions. That is probably ok if just data. If Linux formatted you may need to set ownership & permissions.
Also better with Linux not to use spaces as you have to quote or escape the space. Better to use under_score, CamelCase, or onelongname.

Best to test with n parameter before it copies everything.

---

### Post by kingcobraa on 2014-01-05
it is media/new volume.

can someone help me to create the commands to get this transfer done?? it is really important that i sort this thing out asap.

---

### Post by Dennis N on 2014-01-05
You don't need many options for a one time copy where you are not updating already existing files:

```
rsync -ri --exclude=*.xyz /home/<username>/ /path-to-destination
```

will copy all regular files and directories in the home folder, excluding all files with extension .xyz to a destination you specify by the path from /.

if you need to preserve any of owners, groups, permissions, times, add from 'ogpt' as options.

r = recursive copy
i = gives you feedback on what is being done.

You can add an 'n' option to get a trial run - nothing really copied.  That is, **-nri**

---

### Post by kingcobraa on 2014-01-05
i only need to copy a specific directory excluding files with .xyz extension, when the files with .xyz extension are fixed i will shift them over hoping that no duplicate files are transferred over. i do not want to copy the contents of the entire home directory and only want to copy the directory "downloads/all workouts/it's sub directories". please help me fast!! the destination is "new volume"

---

### Post by Dennis N on 2014-01-05
For a specific directory under home, just change /home/<username>/ in my post #16 to whatever directory you want copied.

**/home/<username>/Documents/** for example.

---

### Post by kingcobraa on 2014-01-05
what about the path to the destination??

---

### Post by kingcobraa on 2014-01-05
no this is still not working.

i tried

 rsync -ri --exclude=*.xyz /home/name/downloads/all workouts /media/newvolume

---

### Post by Dennis N on 2014-01-05
Rename all workouts to all_workouts and try again.

---

### Post by kingcobraa on 2014-01-05
no still not working. is it so hard to copy files in ubuntu?

---

### Post by kingcobraa on 2014-01-05
if you have questions then please ask me. if you want to to perform some tests to provide diagnostic information then please tell me also.

---

### Post by Dennis N on 2014-01-05
How old is your distro? Recent releases (not certain when it started) would require **/media/<username>/newvolume**

---

### Post by kingcobraa on 2014-01-05
12.04 LTS, it is updated frequently so i don't know which version it is now.

---

### Post by Dennis N on 2014-01-05
12.04  would use **/media/newvolume**.

Check the writeability:

Navigate to /media/newvolume with the file manager, and create a new directory called test. If that works, then can you copy a file from your main disk to that directory?

---

### Post by kingcobraa on 2014-01-05
yes created without any problem.

---

### Post by Dennis N on 2014-01-05
And you could copy a file over to the new directory you made? If so, no reason rsync won't work, if the paths to source and destination are correct.

Please post your entire rsync command again. What errors do you get when you run it?

---

### Post by kingcobraa on 2014-01-05
rsync -ri --exclude=*.xyz /home/name/downloads/all_workouts/media/new_volume
rsync: change_dir "/home/name/downloads/all_workouts/media" failed: No such file or directory (2)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]

---

### Post by Dennis N on 2014-01-05
Suggestion: You should use code tags (#) around the command to make it clearer. Highlight the command and press # in the toolbar.

Anyway

```
/home/name/downloads/all_workouts/media/new_volume
``` 

is missing a space between workouts and /media...

I assume you are using your actual user name for **name**?

You want:

```
/home/name/downloads/all_workouts /media/new_volume/
```

note the space added. Got to get the paths correct!

---

### Post by kingcobraa on 2014-01-05
rsync -ri --exclude=*.part /home/name/downloads/all_workouts /media/new_volume/


rsync: change_dir "/home/name/downloads" failed: No such file or directory (2)
rsync: mkdir "/media/new_volume" failed: Permission denied (13)
rsync error: error in file IO (code 11) at main.c(605) [Receiver=3.0.9]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(605) [sender=3.0.9]

---

### Post by Dennis N on 2014-01-05
rsync says **/home/name/downloads** doesn't exist. Your folder name is probably **Downloads** with a capital **D**, which is how it is in the default installation. Capitals make a difference in Linux.

---

### Post by kingcobraa on 2014-01-05
still the same. is there some software that can do the job for me?

---

### Post by Dennis N on 2014-01-05
Once more: You need to repost the command and error message again after the last try. Use code tags around everything.

---

### Post by kingcobraa on 2014-01-05
```
rsync -ri --exclude=*.part /home/name/Downloads /media/new_volume/rsync: change_dir "/home/name" failed: No such file or directory (2)
rsync: mkdir "/media/new_volume" failed: Permission denied (13)
rsync error: error in file IO (code 11) at main.c(605) [Receiver=3.0.9]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(605) [sender=3.0.9]
```

---

### Post by steeldriver on 2014-01-05
Perhaps you'd find it easier to use the GUI file manager to copy and  paste everything from the old location to the new one - then we can give you a command to delete the files  you don't want from the copy

---

### Post by Dennis N on 2014-01-05
Two errors to fix: The first error is explained right here:

```
"/home/name" failed: No such file or directory
```

you are using **name** in the command which is not your user name. Substitute your real user name and it will work, after you fix this **other problem** too:

The target was **/media/newvolume** several posts ago. Now you have used **new_volume**

Change **new_volume** back to **newvolume** in the rsync command and it will work!

You see, rsync tried to make a directory new_volume under /media, but can't since /media is owned by root.
```
rsync: mkdir "/media/new_volume" failed: Permission denied (13)
```

---

### Post by oldfred on 2014-01-05
its not "name" but your user name on the system like mine is fred
/home/fred/Downloads

fred@A105-Precise:~$ echo $USER
fred

And how is the external mounted. type this to see mount
mount

And what format is external drive's partition. Do you have more than one partition.
sudo fdisk -lu
sudo blkid

---

### Post by Dennis N on 2014-01-05
> **steeldriver said:**
> Perhaps you'd find it easier to use the GUI file manager to copy and  paste everything from the old location to the new one - then we can give you a command to delete the files  you don't want from the copy

Yes, great suggestion. I was actually just thinking the same.

**@kingcobraa**

If you still have a problem with rsync working:

Open File Manager, select your **Downloads** directory and then copy. Open another file manager window, Browse to the **/media/newvolume** folder, and Paste. That should do it! 

You can study more about rsync in the future. It could update the omitted files easily once they are fixed!

---

### Post by kingcobraa on 2014-01-06
Hi,

I transferred over the entire folder to the new volume but now I have a major headache. 

I  have a couple thousand files on the new volume with .xyz extension  which need to be deleted. I need a command to try a dry run to check how  these .xyz files can be deleted from the new volume.

Also on the  working drive I have many files including those with .xyz extension and  other kinds as well. Those with the .xyz extension need to be kept on  the working volume but the others with the other extensions need to be  transferred over to the new volume bearing in mind that no duplicates  are transferred over.

Also I need a list of folders, sub  directories and files from both volumes that will tell me which file  exactly has which extension so I can compare and fix only what is  required while updating the new volume with files that have extensions  other than .xyz while at the same time making sure that the issue with  duplicates is resolved.

I hope this matter can be resolved asap because I am really super busy and this is giving me a bad headache.

---

### Post by Dennis N on 2014-01-07
> "I have a couple thousand files on the new volume with .xyz extension which need to be deleted. I need a command to try a dry run to check how these .xyz files can be deleted from the new volume."

Answer:

Easy to do - suppose you wanted to remove all files with extension .txt:

Change directory to the one containing all the files to be removed. Type:

```
find ./ -name "*.txt" -exec rm {} \;
```

will delete **all** files with extension .txt. found in the working directory (the one you are typing the command from) **and** it's subdirectories.

For a trial run (which you should do first, as the first command is for keeps),

```
find ./ -name "*.txt" -exec echo {} \;
```

will dump a list of the files that would be deleted to your terminal window.

 (You can copy and paste the above commands, then edit the line to your desired extension)

---

### Post by Dennis N on 2014-01-07
> "Also on the working drive I have many files including those with .xyz extension and other kinds as well. Those with the .xyz extension need to be kept on the working volume but the others with the other extensions need to be transferred over to the new volume bearing in mind that no duplicates are transferred over."

This is what rsync will do. The command made earlier with **--exclude=*.xyz** will do that. You will get duplicate files on the destination if there are duplicates in different folders on the source.

---

### Post by Dennis N on 2014-01-07
> "Also I need a list of folders, sub directories and files from both volumes that will tell me which file exactly has which extension.."

_Quick and Simple Solution by Example:_

The command below will give a list of all files matching *.mp3 in my home folder and its subdirectories  with the resulting list saved as a file on my Desktop called "filelist.txt". 

In the results, since the path precedes the filename for each file, you can read the directory each is in. Files are grouped by directory.

```
dn@Sydney:~$ find ./ -name "*.mp3" > ~/Desktop/filelist.txt
```

(Note: If you want a list of files from within the home folder, you change to that directory (folder) first if needed before you execute the command.)

You can edit and repeat with other extensions or other locations.

That's It.

(I'm sure there is a more elegant way to do this with nice formatting, but you would need an expert on this to come along and perhaps offer something better!)

---

