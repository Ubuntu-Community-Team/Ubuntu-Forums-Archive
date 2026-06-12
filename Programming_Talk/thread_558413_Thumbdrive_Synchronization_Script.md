---
title: "Thumbdrive Synchronization Script"
date: 2007-09-23
forum: Programming Talk
---

### Post by huzzak on 2007-09-23
The resources I drew upon for writing this are found in [this thread]("http://ubuntuforums.org/showthread.php?p=3408953").  This script automatically synchronizes a folder on my hard drive with a folder on my thumbdrive whenever I plug it into the computer.  I need some suggestions for a couple of things that aren't working as I'd like, though.

This file goes in /usr/local/bin with the filename "sync-thumb.sh
```

#!/bin/bash
#
# CONFIG SECTION
# Local folder to sync with
SYNC_LOC=/home/jlutes/Desktop/TEST
# Device folder to sync with
SYNC_DEV=TEST
#
# SCRIPT SECTION
# Wait for thumbdrive to settle
sleep 10
# Synchronize thumbdrive with local
rsync -axu /media/disk/${SYNC_DEV}/ ${SYNC_LOC}/
# Synchronize local with thumbdrive
rsync -axu ${SYNC_LOC}/ /media/disk/${SYNC_DEV}/
# Inform user that synchronization is complete.
zenity --title "Thumbdrive Sync" --info --text "File synchronization complete."

```

This file goes in /etc/udev/rules.d in a file called "95.backup.rules"
```

BUS=="usb", SYSFS{serial}=="00001619C17352CE", SYMLINK=="jet_drive", RUN+="/usr/local/bin/sync-thumb.sh"

```
The serial number should be replaced as described in [this article]("http://www.linuxjournal.com/article/9311").

I have two issues with it.  For some reason the zenity dialog indicating completion isn't popping up.  I guess I have to pipe it somewhere, but I don't know.  Another problem is that the copied files are given executable status, which I don't like and wish I could prohibit.  Thanks for any comments and suggestions.

Another question!  Is there any way that I could find out how many (and maybe even which) files were synchronized?  Is that something that could potentially be gotten from rsync?

Thanks a ton for any and all help.

---

### Post by mssever on 2007-09-24
> **huzzak said:**
> Another problem is that the copied files are given executable status, which I don't like and wish I could prohibit.
I don't know about your other questions, but am I correct in assuming that your flash drive uses a Windows filesystem (FAT32 or NTFS)? If so, you can't have all your permissions quite right because FAT32 has no permissions and NTFS permissions are incompatible with Linux's permissions.

If you tweak the umask setting in your mount options, you can change the permissions. But if you remove execute permissions from directories, you're in trouble. I think that there's an option for setting permissions for directories and separate permissions for regular files (read the appropriate man page--mount, I think). Of course, if you remove the x bit from regular files, you'll lose the x bit on any executable files that happen to be involved.

---

### Post by DavidBell on 2007-09-25
> **huzzak said:**
> 
This file goes in /usr/local/bin with the filename "sync-thumb.sh


I'm doing something similar. I've started making the pendrive my primary data drive, which is fine for most standard documents but maybe not for things that churn a lot like databases. 

I am working up a a little app that backs it up to host computer(s), and have come to the conclusion that it's best if the application/script and it's settings live on the pendrive, then it can be run to save to any host it's connected to. Best statically linked and cross-platform for the same reason.

DB

---

### Post by peitschie on 2007-09-25
Hiya huzzak,

I was inspired by your scripts and the things you were asking about to fix up my own sync problems.  I took your script and adjusted it a little to suit my needs better, but thought perhaps you might find it helpful as well.

The primary change is that rsync does an initial dry run, and then lists which files it intends to update.  The user can then either click "Ok" to accept the list and run, or can hit cancel to abort the sync.  I have a slight data paranoia atm... if this works well enough I will likely eventually make it quiet.

For me, the udev rules needed to be updated so they only respond to the *final* mounting event, i.e., when the volume itself is actually mounted.  I also added a nohup to the command so the volume would mount while the script was processing, else the script kinda prevents anything else from happening.

The new udev rules:
```

KERNEL=="sdc[0-9]*", SUBSYSTEM=="block", BUS=="usb", SYSFS{serial}=="1aa4f7807494c2", SYMLINK=="jet_drive", RUN+="/usr/bin/nohup /usr/local/bin/sync-thumb.sh"

```

The modified sync-thumb.sh script:
```

#!/bin/bash
#
# CONFIG SECTION
# Local folder to sync with
SYNC_LOC=/media/haven_drive1/documents/philip/USB
DEV_LOC=/media/disk
# r - recursive
# l copy symlinks as symlinks
# p permissions
# t preserve times
# g preserve group
# o preserver owner
# D --devices --specials
DRY_SYNC_OPTIONS="-rltxuin"
SYNC_OPTIONS="-rltxu"

# SCRIPT SECTION
# Wait for thumbdrive to settle
sleep 3

# Synchronize thumbdrive with local
FROM_LOCAL=`rsync ${DRY_SYNC_OPTIONS} ${DEV_LOC}/ ${SYNC_LOC}/`
# Synchronize local with thumbdrive
FROM_USB=`rsync ${DRY_SYNC_OPTIONS} ${SYNC_LOC}/ ${DEV_LOC}/`

# Combine the outputs from the two rsync functions.
# The grep command ignores any line beginning with a '.'.  These files are not being updated in any way
COMPLETE_LIST=`(echo -e "===From Local:===\n${FROM_LOCAL}" && echo -e "==============\n" && echo -e "===From USB:===\n${FROM_USB}") | grep ^[^\.]`

# Get the username of whoever is at the local X11 display. 
# If we don't find one, then exit. 
X11User=`who | grep :0\ | cut -f 1 -d ' '` 
if [ -z "$X11User" ] ; then 
    exit 
fi

export DISPLAY=":0.0"
export HOME="/home/$X11User"

# Don't bother informing the user if no files have changed
if [[ ("${FROM_LOCAL}" == ".d..t...... ./") && ("${FROM_USB}" == ".d..t...... ./") ]]; then
    exit
fi

# Inform user that synchronization is complete and display the modified files
echo "${COMPLETE_LIST}" | sudo -u $X11User zenity --list --title "Files to transfer" --text "File transfer summary" --column "Files" --height 800 --width 600 --display=:0 && RESPONSE=ok
if [ "${RESPONSE}" == "ok" ];
then
    # Synchronize thumbdrive with local
    FROM_USB=`rsync ${SYNC_OPTIONS} ${DEV_LOC}/ ${SYNC_LOC}/`
    # Synchronize local with thumbdrive
    FROM_LOCAL=`rsync ${SYNC_OPTIONS} ${SYNC_LOC}/ ${DEV_LOC}/`
fi

```

---

### Post by huzzak on 2007-09-25
Neato!  That looks great peitschie.  I guess the trick then for to get zenity to do its thing is that you have to specify a user to display the information to?

Could you explain why your udev file needs to be modified?  I ask because I would like to be able to judge whether that is something that I ought to do as well.  Thanks for making the code way better.

EDIT: I guess I don't understand.  If I use your code, I get seven or eight dialog boxes popping up all over the place with bogus information in them.  Probably because the script doesn't wait for the final mount, like you said.  If I use your udev rules, though, it doesn't ever seem to get off the ground and go.  I think I am in over my head.

---

### Post by huzzak on 2007-09-26
Another problem I'm having is that the files are being updated on my machine to that you have to be root to do anything with them.  I do not like this because I'd rather not have to be root, you see.  Anyway, if anyone has some ideas as to why it would be doing this and how I can get it to stop it, I would be very appreciative.  Thanks.

---

### Post by b20963a2 on 2007-09-28
My workaround

> chown -Rv user: /home/user/truecrypt

For those wondering; I'm actually trying to sync a truecrypt container on my usb stick to a directory in my home drive...

---

### Post by math_penguin on 2007-09-29
Thanks for the thread this was a big help. I wanted to do something like what you all are doing, however, I am using the program unison to synchronize files.  If you haven't heard of it take aa look at it here:

[http://www.cis.upenn.edu/~bcpierce/unison/]("http://www.cis.upenn.edu/~bcpierce/unison/")

I think that it is a great solution for maintaining current versions of your projects in several places at once. I also must be using a different version of ubuntu that you guys, because I had to modify the udev rule slightly. In any case my solution is as follows:

> KERNEL=="sdb1" SUBSYSTEMS=="usb", ATTRS{serial}=="5B79100001AB", SYMLINK+="flashdrive", RUN+="/usr/local/bin/sync.sh stixx"

from what I understand about udev this could probably be shortened to:

> ATTRS{serial}=="5B79100001AB", RUN+="/usr/local/bin/sync.sh stixx"

but the first one is working, so I won't mess with it any more.

Now the script sync.sh I wrote is a simplified version of what you guys had, but I could probably just replace the call to sync.sh with a direct call to unison, but I haven't tried it yet. Anyways sync.sh contains:

> 
#!/bin/bash
#

# Get the username of whoever is at the local X11 display. 
# If we don't find one, then exit. 
X11User=`who | grep :0\ | cut -f 1 -d ' '` 
if [ -z "$X11User" ] ; then 
    exit 
fi

export DISPLAY=":0.0"
export HOME="/home/$X11User"

# Wait for thumbdrive to settle
sleep 10

# Synchronize thumbdrive with local
unison -batch $1

# Inform user that synchronization is complete.
sudo -u $X11User zenity --title "Unison" --info --text "File synchronization complete."

The argument to the sync.sh program just tells unison which profile to use, this way I can use the same sync script to potential sync different paths on different drives. Finally, much of the real work of keeping the drive synchronized with my data is done with the unison profile .unison/stixx.prf

> 
# Roots of the synchronization
root = /home/kree/Projects
root = /media/STIXX/Projects

# Paths to synchronize 
path = current

# Preferences
perms        = 0o1700
times        = true

backup       = Path current
maxbackupage = 30
minbackups   = 5
backupdir    = /home/kree/Projects/.backup

log          = true
logfile      = /home/kree/Projects/.backup/backup.log

# Files to ignore 
ignore = Name *.o
ignore = Name *.a
ignore = Name *.so
ignore = Name *.cmx
ignore = Name *.opt
ignore = Name semantic.cache*
ignore = Path current/pscope-server/src/imaging/test
ignore = Path current/pscope-server/src/server/test
ignore = Path current/pscope-server/src/server/pscope


Note that this solutions not only syncs the thumbdrive with my project source code, but it also backups up the source code locally. Unison has some features for merging with old versions that I haven't explored, but should put your mind at ease about the possibility of losing data.

One thing I would recommend is to test out running unison by hand since it can be quite finicky about syncing across file systems. In fact it wants to preserve as many permissions as possible, but I found that I had to tell it to preserve only the owner permissions in order for it to copy the files to a FAT filesystem. That is what the following line does:

> 
perms = 0o1700


FAT also does not support symbolic links, so I had to manually exclude some symbolic links that were in the path I was syncing. That is what these lines do:

> 
ignore = Path current/pscope-server/src/imaging/test
ignore = Path current/pscope-server/src/server/test
ignore = Path current/pscope-server/src/server/pscope


The rest of the unison preferences are just convenient features. I am really exited about this solution and I want to try it with my external hard drive to sync my music collection across several systems. Each time the hard drive is plugged into a computer it automatically checks if the music library is up to date....

MP

---

### Post by peitschie on 2007-09-29
Hi again huzzak.

Sorry about the delay.

The reason you are seeing multiple windows is because a usb being plugged in actually triggers several different events!  If you want to see these, you can do something like the following in the terminal:
```

sudo killall udevd #kill any currently running udev daemons
sudo udevd --debug-trace #start the new udev daemon and print it out to the terminal

```
And then plug in your USB and see the events that crop up.

My exact udev value won't work because the ATTR{serial} value isn't the same as yours (though you likely did remember to change this), and the other step is that the KERNEL value likely won't match either. 

I have set this up so that it will work if the usb is mounted in the /dev/sdc[0-9].  You need to find out where your usb key mounts (plug it in, and then type 'mount' in a terminal and look for which device it is), and then replace the line KERNEL=sdc[0-9]* with your location, e.g., KERNEL=hda[0-9]* for one that mounts at /dev/hda8.

I had found that business with the multiple dialogs as well, and this change forces it to only react to the actual device being connected.

The changing permissions, I am a little intruiged about.  You can force the script to set these by adjusting the rsync options (these are the two variables up the top of the script).

It might be modified to something similar to the following:
```

# dry sync doesn't need to be changed.  only the actual file copying run needs adjustment
DRY_SYNC_OPTIONS="-rltxuin"

# --chmod 777 sets the file permissions to global read/write.  755 or 744 might be more suitable
# --owner set the file owner to the current user
# --group set the file group to the current group
SYNC_OPTIONS="-rltxu --owner ${USER} --group ${USER} --chmod 777"

```

More options for the rsync business can be found by typing 'man rsync' in a terminal session (or gnome terminal).

Don't worry about feeling over your head :-)... thats a good sign lol... it means you are learning :-)... I don't know much more than you i guarentee ;-)

---

### Post by clathe on 2008-01-30
I also use Unison for synching, but my question is this: with udev rules calling Unison, will Unison detach itself immediately? I have a rather large amount of files that I synch on a regular basis, and I don't want udev pausing for 10 minutes while I synch all my files. Ideas?

---

### Post by waive on 2009-04-04
There is a nicely convenient tool called usbsync which has specially been desgined for the purpose of keeping a usb flash drive in sync with multiple Unix hosts.

Check it out at [http://klingspor-thueringen.de/usbsync]("http://klingspor-thueringen.de/usbsync")

They also seem to have an autosync daemon in work.

---

