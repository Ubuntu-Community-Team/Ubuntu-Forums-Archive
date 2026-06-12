---
title: "Bash script: quick ssh mount"
date: 2009-10-04
forum: Programming Talk
---

### Post by sdaau on 2009-10-04
Hi all, 

I was reading [How to mount a remote ssh filesystem using sshfs - Ubuntu Blog]("http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/"), and I thought it world be nice to have a script for quick mounting of ssh - so here is my attempt. Unlike that blog, it seems that for Ubuntu 9.04 only thing necesarry is to have sshfs installed (that is, it is not necesarry to modprobe fuse anymore - not even adding your username to fuse group) 

This script spawns a new terminal window, so you can easily use it from your Nautilus scrips folder (~/.gnome2/nautilus-scripts) and call it via right-click; but you can also call it from the command line directly with arguments: 
```

./sshquicmnt /path/to/local/directory user@server.ssh.com:/path/to/remote/dir

```So, here is the sshquicmnt script: 
```
 
#!/bin/bash
# file: sshquicmnt (quick mount ssh file system)

# save arguments as LOCDIR and REMDIR
LDIR=""
RDIR=""
if [ ! -z "$1" ]; then
  LDIR="$1"
fi

if [ ! -z "$2" ]; then
  RDIR="$2"
fi

USER=`whoami`

## spawn a new terminal window with inline script
## must not use single quotes ' , nor parentheses () , in this part of code
## any var assigned in the inline script can only be read by escaping $, i.e. \$LOCDIR
gnome-terminal -e "bash -c '
# set -x # uncomment for debug

LOCDIR=\"$LDIR\"
REMDIR=\"$RDIR\"

## ask for sudo once at start, and write out passed parameters
sudo pwd
echo Passed from $USER: 
echo LOCAL dir [mountpoint] : \$LOCDIR
echo REMOTE dir: \$REMDIR
echo -------

## if LOCDIR is empty, then prompt
if [ \"\$LOCDIR\" == \"\" ]; then
    read -p \"Enter local dir: \"
    LOCDIR=\$REPLY
    echo LOCAL dir: \$LOCDIR
fi

## if LOCDIR exists, prompt for deletion 
if [ -d \"\$LOCDIR\" ]; then
    read -p \"Local dir \$LOCDIR exists. Delete [y/n]? \"
    [ \"\$REPLY\" == \"y\" ] && sudo rm -r \$LOCDIR
fi

## try to make LOCDIR, and change owner to current user
## in spite of the chown, still have to use sudo rmdir, or sudo rm -r to remove it afterwards
sudo mkdir \$LOCDIR
sudo chown $USER\:$USER \$LOCDIR

## if REMDIR is empty, then prompt
if [ \"\$REMDIR\" == \"\" ]; then
    read -p \"Enter remote dir [ssh path] : \"
    REMDIR=\$REPLY
    echo REMOTE dir: \$REMDIR
fi

## http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/
## fuse doesnt seem to be needed in 9.04, but here is commented code anyways

## just in case, modprobe fuse
# FUSEHERE=`lsmod | grep fuse`
# if [ \"$FUSEHERE\" == \"\" ]; then
    # sudo modprobe fuse
# fi

sshfs \$REMDIR \$LOCDIR
echo Done - mounted \$LOCDIR to \$REMDIR. 
echo Press [ENTER] in this terminal when done, to unmount the local directory.
nautilus \$LOCDIR

read 

## [ENTER] key has been pressed - unmount
fusermount -u \$LOCDIR
## delete the local directory
sudo rmdir \$LOCDIR

## remove the fuse
# if [ \"\$FUSEHERE\" == \"\" ]; then
    # sudo modprobe -r fuse
# fi 
'
"


```Hope this can be useful for some users, 

Cheers!

---

### Post by sdaau on 2009-12-27
A slightly better version:

```
#!/bin/bash
# file: sshquicmnt (quick mount ssh file system)

# save arguments as LOCDIR and REMDIR
LDIR=""
RDIR=""
if [ ! -z "$1" ]; then
  LDIR="$1"
fi

if [ ! -z "$2" ]; then
  RDIR="$2"
fi

USER=`whoami`

## spawn a new terminal window with inline script
## must not use single quotes ' , nor parentheses () , in this part of code
## any var assigned in the inline script can only be read by escaping $, i.e. \$LOCDIR
gnome-terminal -e "bash -c '
# set -x # uncomment for debug

function incorrectSudoQuit {
    echo
    echo Sorry, seems sudo password is invalid. 
    echo This script will now terminate\; please try again afterwards.
    echo
    echo Press [ENTER] in this terminal to quit this script.
    read
    exit
}

function incorrectSshQuit {
    echo
    echo Sorry, seems ssh password is invalid. 
    echo This script will now terminate\; please try again afterwards.
    echo
    echo Deleting local dir..
    ## delete the local directory
    echo \$lpass | sudo -S rmdir \$LOCDIR
    echo Press [ENTER] in this terminal to quit this script.
    read
    exit
}

LOCDIR=\"$LDIR\"
REMDIR=\"$RDIR\"

## prompt for sudo password
echo -n \"sudo password for local user $USER: \"

stty -echo
read lpass
stty echo

# first run sudo -k to reset previously entered passwords
sudo -k

## ask for sudo once at start...
## terminate if password is incorrect 
echo -e \"\nTrying sudo out...\"
echo \$lpass | sudo -S pwd || incorrectSudoQuit

## ... and write out passed parameters
echo Passed from $USER: 
echo LOCAL dir [mountpoint] : \$LOCDIR
echo REMOTE dir: \$REMDIR
echo -------

## if LOCDIR is empty, then prompt
if [ \"\$LOCDIR\" == \"\" ]; then
    read -p \"Enter local dir: \"
    LOCDIR=\$REPLY
    echo LOCAL dir: \$LOCDIR
fi

## if LOCDIR exists, prompt for deletion 
if [ -d \"\$LOCDIR\" ]; then
    read -p \"Local dir \$LOCDIR exists. Delete [y/n]? \"
    [ \"\$REPLY\" == \"y\" ] && echo \$lpass | sudo -S rm -r \$LOCDIR
fi

## try to make LOCDIR, and change owner to current user
## in spite of the chown, still have to use sudo rmdir, or sudo rm -r to remove it afterwards
echo \$lpass | sudo -S  mkdir \$LOCDIR
echo \$lpass | sudo -S  chown $USER\:$USER \$LOCDIR

## if REMDIR is empty, then prompt
if [ \"\$REMDIR\" == \"\" ]; then
    read -p \"Enter remote ssh dir [user@url:/path] : \"
    REMDIR=\$REPLY
    echo REMOTE dir: \$REMDIR
fi

## http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/
## fuse doesnt seem to be needed in 9.04, but here is commented code anyways

## just in case, modprobe fuse
# FUSEHERE=`lsmod | grep fuse`
# if [ \"$FUSEHERE\" == \"\" ]; then
    # sudo modprobe fuse
# fi

# try to mount - exit on fail
sshfs \$REMDIR \$LOCDIR || incorrectSshQuit
echo Done - mounted \$LOCDIR to \$REMDIR. 
echo Press [ENTER] in this terminal when done, to unmount the local directory.
nautilus \$LOCDIR

read 

## [ENTER] key has been pressed - unmount
fusermount -u \$LOCDIR
## delete the local directory
echo \$lpass | sudo -S rmdir \$LOCDIR

## remove the fuse
# if [ \"\$FUSEHERE\" == \"\" ]; then
    # sudo modprobe -r fuse
# fi 
'
"

```

---

### Post by Redsandro on 2010-07-19
[SIZE="1"]I know this is a tad bit old, but it's relevant. (:[/SIZE]

Wow, I found this while trying to find out why **sshfs** *unmounts* when I *close the terminal*. I built this little script for personal use. It's much simpler but since it's just for me, I don't need to [idiot-proof]("http://en.wikipedia.org/wiki/Idiot_proof") it if you know what I mean.

Here's my script now:

```

#!/usr/bin/env bash
#sshfs mounter by Redsandro
#2010-07-17 #www.Redsandro.com
#Last edit" 2010-07-19
# Now you can have a desktop shortcut:
# Linux # gnome-terminal -x /usr/local/bin/sshfs.sh redsandro 192.168.1.10 / sshfs-redserv
# Win32 # gnome-terminal -x /usr/local/bin/sshfs.sh Sander Redsandro /cygdrive sshfs-redsandro

#SELFNOTE: test works but if it fails it outputs error:
# ./sshfs.sh: line 12: [: too many arguments
#Why?

if [ ${1:+1} = 1 -a ${2:+1} = 1 -a ${3:+1} = 1 -a ${4:+1} = 1 ]; then
	USER=$1
	HOST=$2
	DEST=$3
	DIR=~/$4

	if [ ! -d $DIR ]; then
		mkdir $DIR
	fi

	echo "Mounting" "$USER"@"$HOST":"$DEST"
	echo "Mountpoint:" "$DIR"
	echo

	sshfs "$USER"@"$HOST":"$DEST" "$DIR"
	nautilus "$DIR"
	#sleep 10 # Give fusermount time to mount the share. Yes it can take some time for some computers with encrypted home dirs.

	echo
	echo "sshfs will unmount when terminal closes."
	echo "Press ENTER to close."
	read
else
	echo "Wrong parameters."
	echo "Usage:"
	echo "sshfs.sh user host host_dir mount_dir"
	echo "(sshfs user@host:host_dir ~/mount_dir)"
	echo "(NO TRAILING SLASH on mount_dir!)"
fi

```

Anyway, I didn't want those echo's there and just let the terminal popup for the password. Turns out that the mount will **unmount** right after the terminal closes. Do you have any idea why?

I see you actually have a **fusermount -u** in there. But over here (Ubuntu 10.04) exiting the terminal is sufficient.



**-edit-**

If anyone finds and uses this, let me write 2 sentences of documentation:

The purpose is to have frequently mounted local and remote computers as desktop-shortcuts (gnome) all using the same script in: */usr/local/bin/sshfs.sh*
The chosen mountpoint will be in ~ (your home folder) and automatically opened with *Nautilus*.

Example shortcut:

**~/Mount MCRED.desktop**
```

#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Name=Mount MCRED
Comment=Mount MCRED through sshfs
Icon=/usr/share/icons/gnome/scalable/apps/gnome-terminal.svg
Exec=gnome-terminal -x /usr/local/bin/sshfs.sh sander 192.168.201.7 / sshfs-mcred

```

Single-click love.

---

### Post by vamsii on 2010-07-20
Thanks..very useful for me :D

---

