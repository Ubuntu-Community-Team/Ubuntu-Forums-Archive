---
title: "HOWTO: Automatically regulate the size and age of your Trash folder"
date: 2008-02-16
forum: Outdated Tutorials &amp; Tips
---

### Post by tweedledee on 2008-02-16
This script will automatically delete files from your trash folder that exceed certain age and/or size limits, and will also keep the total size down, while allowing extensive control over its behavior.

*Updated 12 June 2008: handles freedesktop.org standard trash (KDE, XFCE, Gnome 2.22+) as well as older trash (Gnome 2.20 and below).*
*Updated 5 July 2008: point out use of $HOME as ~ alternative, more reliably handle deletion of paths with spaces in name.*
*7 July 2008*: see [http://ubuntuforums.org/showpost.php?p=5327195&postcount=12](http://ubuntuforums.org/showpost.php?p=5327195&postcount=12) below for ideas on useful modifications to this script, especially for multi-user environments.  For those who don't wish to make the changes manually, I will incorporate some/all of into the main script in the "near" future, as my time allows.

**WARNING: this script will automatically delete files!  Use with caution!**
Used correctly, this script should be perfectly safe.  However, it does contain the "rm -rf" command, and has the potential to damage your system.  Please take the following precautions before using:
1) Back up your system, or at least your home folder.  You should do this anyway, it's probably been too long.
2) Before executing, always ensure that the TrashPath variable, which contains the path to be regulated, in fact points to your Trash folder, and not (for example) your home folder.
3) **NEVER** execute this script with the "sudo" command unless you know exactly what you are doing.  Improperly used, this could theoretically delete your whole system, although it would take a series of unlikely mistakes.  (To remove files/directories owned by root from your trash, you *can* run "sudo emptytrash.bash", but only do so when you are sure the script works and know there are problematic files in your trash.  Note that using sudo in this case affects your USER trash, not ROOT trash, whereas logging in as root or using "sudo -i<ENTER>emptytrash.bash" will clear ROOT trash.)

**I cannot help you if you misuse this script - once it removes the files, they are gone forever.**  (Actually, some file systems do allow for an undelete, but that is beyond the scope of my experience, and the default in Ubuntu, ext3, does not have a reliable way of recovering deleted files.)  Backups are important!

This script should work on any version of (k/x/etc)Ubuntu, provided you modify the TrashPath variable as needed.  As written, TrashPath points to ~/.local/share/Trash, which is the Trash folder used by Gnome 2.22 (Hardy and greater), KDE, and XFCE.  This script should work for any distro (certainly any Debian-based distro) using similar versions of Gnome/KDE/XFCE, and probably other file managers that use the Trash.  When pointing to the Trash path, also make sure the "freedesktop" switch is set correctly; it should be "1" for Gnome 2.22+, KDE, and XFCE; "0" for Gnome 2.20 or lower; and set appropriately for other file managers.  (The standard ones generally use the path ~/.local/share/Trash, with two sub-directories of "files" and "info".)  It should also work fine in a multi-user system, provided the trash path for all users is the same.

In addition to being able to change the TrashPath, you have control over the following parameters:

**Undelete info cleanup**
If using a Freedesktop.org-standard Trash (KDE, XFCE, Gnome 2.22+), setting this to "1" will have this script also purge the undelete information for removed files; this setting is ignored if not using a Freedesktop.org-standard Trash.  I have tested this with Gnome 2.22 (which has the infrastructure in place but does not actually allow for undelete); it should not break anything for other file managers, but it is possible it will remove too much undelete information in some cases for others (I can't find clear information on how KDE and XFCE regulate theirs).  Worst case scenario is that you'd lose the undelete path for files still in your trash, meaning that automatic restore wouldn't work (but you could still do so manually).

**Age**
Six settings control the age at which files get deleted.  FileLimit, FileLimitLarge, and FileLimitHuge are the number of days a file must remain static (i.e., not moved, modified, or had permission/ownership changes) before being removed.  FileLimit variables apply to the files that are in the root of TrashPath, i.e., not in a sub-folder.  DirLimit, DirLimitLarge, and DirLimitHuge apply to the subfolders, which are treated as a units.  Note that if you modify a file within a subfolder, it may or may not change the modified date on the folder itself, depending on the nature of the change to the file.

**Size**
FileLimit and DirLimit variables apply to all files and folders.  The Large and Huge variables apply only to those files and folders exceeding a certain size, in megabytes.  By default, the script treats all files larger than 10 MB as "large" and greater than 100 MB as "huge", with slightly higher limits for folders.

**Overall Size**
The total size of the Trash folder can be limited (in MB) using MaxSize.  In addition, you can set the AlwaysEmpty variable to 1 (on) or 0 (off).  If AlwaysEmpty is on, then the script will delete files from the Trash whenever they meet age/size requirements, even if the TOTAL size of the Trash is below the limit (MaxSize).  If AlwaysEmpty is off, files are never deleted until the Trash folder exceeds MaxSize.

**Overall Size deletions**
To address the scenario where MaxSize is exceed, but no individual files or folders meet their age/size requirements, there are some additional parameters for forcing the Trash below MaxSize.  These two groups of parameters control the rate at which the time/age limits are temporarily lowered to delete additional files, and the minimum values they can take, at which you point deletion will stop even if MaxSize is exceeded.  To deal with MaxSize being exceed, the script lowers all limits by the indicated amount, deletes any matching files, then lowers and deletes again, etc., until either MaxSize is no longer exceeded or the minimum values are reached.

To disable the looping to force the Trash below MaxSize even when individual files/folders don't meet the limits you have set, simply set the minimum values to the same as the initial values.

**The Script**
Below is the script.  Copy the contents of it into a new text file using your favorite editor (Gedit, etc.).
**REMEMBER to set the TrashPath correctly for your system!**
Make any other changes to the settings you wish, and save the file (e.g., emptytrash.bash).  Then make the file executable, either by right-clicking and selecting Properties -> Permissions, or in a terminal:
```
chmod +x emptytrash.bash
```
You can the test the script, **after backing up your files**, by running
```
./emptytrash.bash
```in a terminal.  The script should simply return a command prompt without errors.  It may or may not have actually deleted anything from your trash, depending on what matched the parameters you set.

To run automatically, you can either put the script in your daily/hourly cron, or (as I do), ```
sudo cp emptytrash.bash /usr/local/bin
``` and add ```
/usr/local/bin/emptytrash.bash
``` to your session startup commands (in Gnome, System -> Preferences -> Sessions -> Add).

The script:
```
#! /bin/bash

# Purge files from Trash, if meet sufficient time and size criterea
# Directories are treated as blocks
# Uses only ctime (modified/moved) for time matching, as access time for directories is often
#   much more recent (e.g., if listed files within) and files are sometimes made more recent
#   by find and other system commands rather than actually reading it
# Will never delete files/directoires changed (deleted) less than 1 day (24 hours) ago
# Note that if files not owned by the user end up in the user's Trash directory, this script
#   may not be able to delete them unless it is run as root

# Path to Trash directory and Trash type
# If path contains spaces, enclose in "" and do not use ~; use $HOME instead (e.g., "$HOME/path to trash/trash/")
# Gnome 2.20 and earler use ~/.Trash (not freedesktop.org standard)
# Gnome 2.22 & later, XFCE 4.4 & later, and KDE 3.4? & later use ~/.local/share/Trash (freedesktop.org standard)
# Freedesktop is 1 if uses a files/info subfolder system in TrashPath (freedesktop.org standard);
#	0 if stores files directly in TrashPath (i.e., set appropriately to match the path type)
TrashPath=~/.local/share/Trash
Freedesktop=1 

# Maintain undelete information
# 1 if using freedesktop.org system and want to purge unneeded .trashinfo files from TrashPath/info;
#	0 otherwise
# this is ignored unless Freedesktop (above) = 1
# NOTE: not entirely sure how non-Gnome handle maintaining TrashPath/info, so this could break "undelete"
#	Trash functions, but it probably is safe to use
MaintainInfo=1 

# Time limits are in days; File settings refer to files in base folder,
#   Dir to directories in same
# Large & Huge limits refer to files/directories larger than the indicated size
# These values must be integers, and must be greater than 0
FileTime=90
FileTimeLarge=30
FileTimeHuge=7
DirTime=90
DirTimeLarge=45
DirTimeHuge=10

# Size limits (in MB) to trigger shorter time intervals
# These values must be integers, and must be greater than 0
FileSizeLarge=10
FileSizeHuge=100
DirSizeLarge=15
DirSizeHuge=150

# Overall maximum size (in MB) before begins to delete things before the above limits
# Must be an integer and greater than 0
MaxSize=2000

# Set following to 1 if wish to empty trash, based on above limits, even when MaxSize
#   is not exceeded; set to 0 if only empty the trash when above MaxSize
AlwaysEmpty=1

# Following values are amount to reduce limits by if necessary to reduce total size below MaxSize
# All values must be integers and greater than 0
FileTimeDec=1
FileTimeLargeDec=1
FileTimeHugeDec=1
DirTimeDec=1
DirTimeLargeDec=1
DirTimeHugeDec=1
FileSizeLargeDec=1
FileSizeHugeDec=2
DirSizeLargeDec=1
DirSizeHugeDec=3

# Following values are the smallest value that the limits/sizes can take on, when MaxSize is exceeded
# Set to 3 if, for example, you wish to never delete files less than 3 days old
# All values must be integers and greater than 0
FileTimeMin=1
FileTimeLargeMin=1
FileTimeHugeMin=1
DirTimeMin=1
DirTimeLargeMin=1
DirTimeHugeMin=1
FileSizeLargeMin=1
FileSizeHugeMin=1
DirSizeLargeMin=1
DirSizeHugeMin=1

#-------------------------------------------------------------
EmptyTrash() {
    # files first, in the main directory only
    # Normal
    TP="$1"
    find "$TP" -maxdepth 1 -type f -ctime +$FileTime -execdir rm -f '{}' +

    # Large
    find "$TP" -maxdepth 1 -type f -ctime +$FileTimeLarge -size +${FileSizeLarge}M -execdir rm -f '{}' +
    
    # Huge
    find "$TP" -maxdepth 1 -type f -ctime +$FileTimeHuge -size +${FileSizeHuge}M -execdir rm -f '{}' +
    
    # Now directories
    # Normal
    find "$TP" -maxdepth 1 -type d -ctime +$DirTime -execdir rm -rf '{}' +
    
    # For Large & Huge, need to loop to be able to get directory size
    # Large
    for i in `find "$TP" -maxdepth 1 -type d -ctime +$DirTimeLarge`
    do
      if [ `du -sm "$i"|awk '{print $1}'` -gt $DirSizeLarge ]
      then
        rm -rf "$i"
      fi
    done
    
    # Huge
    for i in `find "$TP" -maxdepth 1 -type d -ctime +$DirTimeHuge`
    do
      if [ `du -sm "$i"|awk '{print $1}'` -gt $DirSizeHuge ]
      then
        rm -rf "$i"
      fi
    done
}

EmptyInfo() {
    # get list of all files in TrashPath/info, then remove ones that don't have a matching file in TrashPath/files
    # strip './' and '.trashinfo' from list of files in TrashPath/info before storing in a temp file
    find "$TrashPath/info" -maxdepth 1 -type f -execdir ls '{}' + |sed -e 's/.\///' |sed -e 's/.trashinfo$//' > /tmp/emptytrash_trashinfo.list
    while read line
    do
      ls "$TrashPath/files/${line}" > /dev/null 2>&1
      if [ $? -ne 0 ]
      then
        rm -rf "$TrashPath/info/${line}.trashinfo"
      fi
    done < /tmp/emptytrash_trashinfo.list
    rm -rf /tmp/emptytrash_trashinfo.list
}

MaxVal() {
    if [ $1 -gt $2 ]
    then
      return $1
    else
      return $2
    fi
}

# Set needed variables for splitting lines and comparisons
export IFS=$'\n'
CompVal=$(($FileTimeDec + $FileTimeLargeDec + $FileTimeHugeDec + $DirTimeDec + $DirTimeLargeDec + $DirTimeHugeDec))

# purge based on individual file times/sizes, even if total size is not exceeded
if [ $AlwaysEmpty -eq 1 ]
then
  if [ $Freedesktop -eq 1 ]
  then
    EmptyTrash "$TrashPath/files"
  else
    EmptyTrash "$TrashPath"
  fi
fi

# Now loop until overall size does not exceed maximum
while [ `du -sm $TrashPath|awk '{print $1}'` -gt $MaxSize ]
do
  # First time through this may be redundant, if AlwaysEmpty is 1
  if [ $Freedesktop -eq 1 ]
  then
    EmptyTrash "$TrashPath/files"
  else
    EmptyTrash "$TrashPath"
  fi

  if [ $(($FileTime + $FileTimeLarge + $FileTimeHuge + $DirTime + $DirTimeLarge + $DirTimeHuge)) -eq $CompVal ]
  then
    # Stop, because all time limits are as small as they are going to get
    break
  fi

  # reduce all time and size limits by appropriate values, keeping at least minimum size
  MaxVal $((FileTime - $FileTimeDec)) $FileTimeMin
  FileTime=$?

  MaxVal $((FileTimeLarge - $FileTimeLargeDec)) $FileTimeLargeMin
  FileTimeLarge=$?

  MaxVal $((FileSizeLarge - $FileSizeLargeDec)) $FileSizeLargeMin
  FileSizeLarge=$?

  MaxVal $((FileTimeHuge - $FileTimeHugeDec)) $FileTimeHugeMin
  FileTimeHuge=$?

  MaxVal $((FileSizeHuge - $FileSizeHugeDec)) $FileSizeHugeMin
  FileSizeHuge=$?

  MaxVal $((DirTime - $DirTimeDec)) $DirTimeMin
  DirTime=$?

  MaxVal $((DirTimeLarge - $DirTimeLargeDec)) $DirTimeLargeMin
  DirTimeLarge=$?

  MaxVal $((DirSizeLarge - $DirSizeLargeDec)) $DirSizeLargeMin
  DirSizeLarge=$?

  MaxVal $((DirTimeHuge - $DirTimeHugeDec)) $DirTimeHugeMin
  DirTimeHuge=$?

  MaxVal $((DirSizeHuge - $DirSizeHugeDec)) $DirSizeHugeMin
  DirSizeHuge=$?
done

# If requested, clean up the .trashinfo files
if [ $Freedesktop -eq 1 ]
then
  if [ $MaintainInfo -eq 1 ]
  then
    EmptyInfo
  fi
fi
```

If at any point you wish to stop using and/or remove the script, just delete the file or reference from your cron/session commands, and/or delete emptytrash.bash.

This should work in a mutli-user environment with a single copy, provided all users have the same relative path to their trash, or multiple copies of the script with different names could be used, each with its own path.

Note that if you want to check the total size of your Trash, you can either use a graphical tool like Disk Usage Analyer or, in a terminal
```
du -sm ~/.local/share/Trash
```which will output the total size of your Trash in megabytes (assuming ~/.local/share/Trash is your Trash folder).

Also note that if this solution is more complex than you need/want, and you just want a simple one-liner that prevents the Trash folder from becoming too large, see [http://ubuntuforums.org/showthread.php?t=319211](http://ubuntuforums.org/showthread.php?t=319211).

Please post (not private message) if you have any questions, comments, or complaints.

This script is becoming a bit of a communual effort, so I thank those who have posted below and pointed out problems or contributed new ideas/extensions.

---

### Post by bhavi on 2008-03-24
Thanks.. but I have a doubt.. How to restore files from trash to the exact location?

---

### Post by tweedledee on 2008-03-24
That feature is implemented (at least in Gnome) in Hardy; I'm not sure yet (since I've not used Hardy) how the restore ability will affect this script.

---

### Post by bhavi on 2008-03-24
> **tweedledee said:**
> That feature is implemented (at least in Gnome) in Hardy; I'm not sure yet (since I've not used Hardy) how the restore ability will affect this script.
Yup tried it out today.. Didnt know that feature was there....

---

### Post by tweedledee on 2008-06-12
Posted update to deal with standard trash format in addition to the old Gnome style.  Should now work for almost any file manager running almost any *nix.

---

### Post by Simon-v on 2008-06-24
I find this script insanely useful. It will sometime become part of the default Linux installation. I think.

---

### Post by lobner on 2008-06-27
Regarding the post by 'tweedledee' I am using Hardy and I have been searching the web but I can't seem to find the answer I am looking for. Can anyone tell me how the in the world I manage to restore files lying in the trash bin? 

I see no option when right clicking them or anything like that - where am I supposed to look??!

The directory structure looks as I supposed it should, with the ~/.local/share/Trash/{files, info}

The deleted files are in there, but also here, there is no option to undelete any of them? :confused:

---

### Post by tweedledee on 2008-06-27
> **lobner said:**
> The deleted files are in there, but also here, there is no option to undelete any of them? :confused:

I believe, though I am not 100% sure, that undelete was removed from Gnome 2.22 shortly before final release, and will appear in a final version in 2.24 (which should be released with Intrepid).

---

### Post by lobner on 2008-06-29
Ohh... ok thanks, have to wait then. But I can still find the deletion-points nonetheless. In the [FONT="Courier New"]info[/FONT]-folder :)

---

### Post by ghostdog74 on 2008-06-30
@OP: good effort.
some improvement suggestion:

1) find can include compound statements eg
```

find . \( -name "*.txt" -o -name "*.jpg" \) -ls

```
maybe that can be applied to EmptyTrash() function where you have a few repetitive find commands with ctime, size ...
2) if you use the for loop to iterate the results of a find command, you might hit problems if there are files with spaces. Use a while read loop and quote your variables instead.
```

find ..... | while read DIR
do
  # do something with "$DIR"
done

```
3)  for this piece of code:
> 
```

    for i in `find "$TP" -maxdepth 1 -type d -ctime +$DirTimeLarge`
    do
      if [ `du -sm $i|awk '{print $1}'` -gt $DirSizeLarge ]
      then
        rm -rf $i
      fi
    done

```

can be a one-liner like this :
```
find . -type f -ctime +$DirTimeLarge -print0 | xargs -0 du -sm | awk '$1>"'$a'"+0' | xargs rm -f

```

---

### Post by tweedledee on 2008-07-05
General announcement: small update posted, anyone using this who reads this probably should update their script with the new version to avoid a chance of failing to delete directories with the previous versions.

> **ghostdog74 said:**
> @OP: good effort.
some improvement suggestion:

Thanks for the feedback.  Regarding your #1 and #3, you are absolutely correct.  However, I deliberately chose NOT to implement the script that way, taking the small speed penalty (increases typical run time by 10-20%, mainly because additional find commands can use the cache and add very little) in the interest of keeping the purpose of the code very clear.  Nobody has any reason to trust me, and this is a potentially destructive script, so I wanted to keep it transparent to anyone with even a little general programming knowledge, not just those comfortable with shell scripting.

Point 2 is absolutely correct that I should have been quoting the variables; for some reason it worked in all my tests anyway, but quoting is far more reliable.  I've actually had better success with the for than while approach, but if you have a specific case where while works better, I'd probably switch.

---

### Post by Simon-v on 2008-07-05
Thought i'd share my doings.
In order to make this script easily usable for multi-user systems i wrote a simple wrapper script that calls the cleaner script and which can be launched from root crontab:
```
#!/bin/bash
# Handle trash in all listed trash directories. Passes any arguments to the child script.
TrashCommand="/path/to/emptytrash/script"
TrashDirs="/home/user1/.local/share/Trash
/home/user2/.local/share/Trash
/home/user3/.local/share/Trash
/root/.local/share/Trash"

for Directory in $TrashDirs; do
   "$TrashCommand" "$Directory" $@
done
```
I then edited the cleaner script to use the first argument as TrashPath or use the default if not provided with any:
```
if [ "$1" = "" ]; then
  TrashPath=~/.local/share/Trash
else
  TrashPath="$1"
fi

```

To make sure the cleaner script does what it is supposed to, i added a bit of verbosity to it by inserting ```
if [ $Verbose = 1 ]; then
  echo "Deleting $i"
fi

``` before every "**rm**" statement and adding a Verbose=1 in the setting area. I used the following crude, non-optimal, to-be-changed-really-soon routine:
```
# Take the second argument as verbosity setting
case "$2" in
  -v | --verbose)
  Verbose=1
  FeedBack1=", verbose mode"
esac

# Extra feedback
if [ $Verbose = 1 ]; then
  echo "Processing $TrashPath (Freedesktop=$Freedesktop$FeedBack1)"
fi

```

Adding a possibly-needed "dry run" option for testing purposes is a trivial matter. Making the script read and use user configuration files ("~/.trash_policy", maybe?) is slightly more difficult but might be interesting to try.
The wrapper script is rather crude too; i simply don't yet know any way to automatically figure out all the users who exist on a system. Maybe it's something about /etc/passwd.

May someone find this interesting.

---

### Post by tweedledee on 2008-07-07
> **Simon-v said:**
> Thought i'd share my doings.

Thanks for sharing!  I was considering making some of the modifications you talk about if there was interest expressed; since there clearly is, I will incorporate some/all of it into the script in the main post in the near future (but don't hold your breathe).  In the meantime, I've at least added text pointing to your post.

---

### Post by Lockheed on 2011-05-08
This script is godly, except I am getting this small error on Arch:
```
./emptytrash.bash: line 119: /tmp/emptytrash_trashinfo.list: No such file or directory
```

---

### Post by tweedledee on 2011-05-09
> **Lockheed said:**
> This script is godly, except I am getting this small error on Arch:
```
./emptytrash.bash: line 119: /tmp/emptytrash_trashinfo.list: No such file or directory
```

I'm not sure what to make of that, because a reference to line 119 is ambigious.  The most obvious problems to me are that either the script does not have permission to write to /tmp/ or the "info" folder is not in the expected location.  You could try isolating the emptytrash routine into a new script (keeping the necessary variable declarations and last part of the main routine to call it) and comment out each step to see which one(s) lead to the error being generated, but otherwise I don't immediately see any troubleshooting approach.

Worst case, this error should just mean that the restore/undelete information is being left behind, which is not really a big deal.  You can always disable this step (set MaintainInfo=0) to silence the error.

---

