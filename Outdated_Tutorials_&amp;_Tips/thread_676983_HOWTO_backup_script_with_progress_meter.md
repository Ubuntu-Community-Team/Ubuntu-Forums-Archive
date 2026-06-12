---
title: "HOWTO: backup script with progress meter"
date: 2008-01-24
forum: Outdated Tutorials &amp; Tips
---

### Post by calraith on 2008-01-24
_**edit history**_
2008-1-25: modified backup script to move variables to the top
2008-1-26: updated tarp wrapper to final version, modified backup script to incorporate requested "exclude" ability and to fix --progress-bar flag
2008-1-28: backup script checks whether b[] and ex[] are contiguous (so no more errors if elements are commented out)
2008-1-28: backup script accepts "/" to back up the entire filesystem recursively, automatically skipping some system directories better left as excluded
2008-4-2: no clue why I forgot to exclude /dev when backing up /.  Fix'd.

**_known problems_**
It seems that symlinks throw off the accuracy of the progress bar.  This is only cosmetic -- the backup still works.

_**Instructions**_
I use a home-grown script to make my backups. The nice thing about this is that rather than blindly backing up "everything" excluding the directories I don't want or having the script guess what I want backed up as other tutorials show, I can instead specify exactly what I would like to include. This generally only includes conf files I've modified; settings kept in my home directory for apps such as Firefox, irssi, GIMP, etc; the contents of /usr/local/bin; and more obvious stuff such as pictures I have stored in my home directory.

My script uses a perl wrapper for tar that provides a progress bar, called tarp.  This wrapper, written by [Michal Kwiatkowski]("http://joker.linuxstuff.pl/projects/completed"), is published under a [BSD license]("http://www.opensource.org/licenses/bsd-license.php"), and is attached at the bottom of this post.

After you save tarp_0.8.3-1_all.deb, double-click it and enter your password to let gdebi install it.

Anyway, as follows is my script.  I've updated it so that adding new files and directories to back up is a bit more intuitive.  The script will automatically append a / to the end of directory names, escape spaces in file names, and check for files that don't exist.  As franestepona requested below, I also added the ability to specify patterns to exclude from the backup.  I left my backup list untouched because, I don't know, maybe something in it will remind you to backup a file you would have forgotten about otherwise.
```
#!/bin/bash

# destination directory
BACKUP_TO=/media/storage

# p = preserve permissions; P = store absolute path; c = create; j = bzip2; f = overwrite
TAR_FLAGS=pcjf

# array of files and directories to be included in the backup -- Enclose any paths
# containing spaces in quotation marks.  If / (as the file system root) is specified,
# then /proc, /lost+found, /mnt, /sys, /tmp, /dev, and /media are skipped.  If you
# wish to re-include any of those ignored directories, simply specify each as an
# additional item to be included in the backup.
b[0]=/home/rojo/.centericq/
b[1]=/home/rojo/.conkyrc
b[2]=/home/rojo/.gimp-2.4/
b[3]=/home/rojo/Pictures/
b[4]=/home/rojo/se-code.tar
b[5]=/home/rojo/.irssi/
b[6]=/home/rojo/.kiba-dock/
b[7]=/home/rojo/.ssh/
b[8]=/home/rojo/.vnc/
b[9]=/home/rojo/.wacom
b[10]=/home/rojo/.mozilla/
#b[11]=/home/rojo/REISUB.txt
b[12]=/home/rojo/backupscript.sh
b[13]=/home/w00t/eggdrop/
b[14]=/etc/X11/xorg.conf
b[15]=/etc/default/locale
b[16]=/etc/environment
b[17]=/etc/rc.local
b[18]=/etc/bluetooth/hcid.conf
b[19]=/etc/network/interfaces
b[20]=/etc/wpa_supplicant/
b[21]=/etc/nanorc
b[22]=/etc/fail2ban/
b[23]=/etc/fstab
b[24]=/etc/qemu-ifup
b[25]=/etc/samba/smb.conf
b[26]=/etc/hosts.deny
b[27]=/etc/vpnc/
b[28]=/usr/local/
#b[29]=/boot/grub/splashimages/
b[30]=/var/www/
b[31]=/var/lib/locales/
b[32]=/root/.vnc/
b[33]=/root/.ssh/
b[34]=/usr/share/applications/screensavers/

## array of patterns matching files and folders to exclude from the backup
ex[0]=*Cache*
ex[1]=*.bak
ex[2]=*.old
ex[3]=quota.*

############################## nothing else needs to be edited ################################

function make_backup {
    local timestamp=$(date | sed -r -e 's/^\S+ //' -e 's/([0-9]+:){2}[0-9]+ //g' -e 's/[A-Z]{3} //' -e 's/ +/-/g')
    local bakfile=$BACKUP_TO/backup-$timestamp.tar.bz2
    # Unless the P flag is included in $TAR_FLAGS, tar will brag about removing leading slashes.
    # By the time this bit executes, we will have already silently removed them.  cd / to keep sane.
    cd / >/dev/null
    time sudo tarp -$TAR_FLAGS $bakfile $INCLUDES --progress-bar
    cd $OLDPWD >/dev/null
    ls -sh --color $bakfile
}

EXCLUDES=
exLen=${#ex[@]}
for (( x=0; x<$exLen; x++ )); do {
    if [ "${ex[$x]}" != "" ]; then
        # prepend --exclude= to the element and escape spaces
        ex[$x]=`echo '--exclude='${ex[$x]} | sed -r -e 's/ /\\\\ /g'`
        EXCLUDES=`echo ''$EXCLUDES ${ex[$x]}`
    else
        ((exLen=$exLen+1))
    fi
}; done

INCLUDES=
bLen=${#b[@]}
for (( x=0; x<$bLen; x++ )); do {
    if [ "${b[$x]}" != "" ]; then
        # if array element is the name of a directory
        if [ -d "${b[$x]}" ]; then
            # append a trailing /, but only if not already existing
            b[$x]=`echo ${b[$x]} | sed -r -e 's/([^\/])$/\1\//'`
        else
            # otherwise, try removing trailing slash in case this is a regular file
            b[$x]=`echo ${b[$x]} | sed -r -e 's/\/$//'`
            # if array element *still* can't be found in the filesystem
            if [ ! -f "${b[$x]}" ]; then
                # don't bother adding it to the backup list -- insult user instead
                read -p "Dropping ${b[$x]} -- file does not exist.  Replace user and strike any key to continue." -n 1
                echo;
                b[$x]=" "
            fi
        fi
        # escape spaces in the filename and remove leading slashes (so tar won't make a
        # big deal about doing it for us, otherwise ruining our pretty pretty output)
        if [ "${b[$x]}" = "/" ]; then
            b[$x]=`ls -Amp --ignore=proc --ignore=lost+found --ignore=mnt --ignore=sys --ignore=media --ignore=tmp --ignore=dev / | sed -r -e 's/,//g'`
        else
            b[$x]=`echo ${b[$x]} | sed -r -e 's/ /\\\\ /g' -e 's/^\///'`
        fi
        INCLUDES=`echo $INCLUDES ${b[$x]}`
    else
        ((bLen=$bLen+1))
    fi
}; done

if [ "$EXCLUDES" != "" ]; then
    INCLUDES=`echo ''$EXCLUDES $INCLUDES`
fi

make_backup

```It looks like this when run:
[IMG]http://xs123.xs.to/xs123/08044/backupimg311.gif[/IMG]

---

### Post by franestepona on 2008-01-26
Great job, thanks! I have one point to make though. I back up my entire system, and what I do it's to list directories to exclude, instead of include, as u say in the beginning. I have tried to modify your script so I can make it work for me but I'm not good at bash programming. Could you add a section for excluding directories? Or tell me how can I use the INCLUDES array to make them excluded instead? Although there are instructions out there about how to make a system backup i have never seen a progress bar, which I think it's very useful.

Thanks!

---

### Post by calraith on 2008-01-26
> **franestepona said:**
> Great job, thanks! I have one point to make though. I back up my entire system, and what I do it's to list directories to exclude, instead of include, as u say in the beginning. I have tried to modify your script so I can make it work for me but I'm not good at bash programming. Could you add a section for excluding directories? Or tell me how can I use the INCLUDES array to make them excluded instead? Although there are instructions out there about how to make a system backup i have never seen a progress bar, which I think it's very useful.

Thanks!

**UPDATE:**
As requested, I added a section to specify patterns matching files to exclude.  Before using the updated script, you should also remove /usr/local/bin/tarp.pl and install the final version of tarp as is attached to the original post.  Enjoy!

**original reply:**
In composing a response to you, I found that the author of tarp.pl has added an [updated version]("http://joker.linuxstuff.pl/projects/completed") of his tar progress meter wrapper to his website.  I'll be updating the parent post as soon as I finish this response.  What I was originally going to tell you is as follows:
> There are [several backup howtos]("http://ubuntuforums.org/search.php?searchid=35355587") in this Tutorials & Tips forum.  [This one]("http://ubuntuforums.org/showthread.php?t=80790") seems to be the most robust, and will let you exclude any number of files and directories simply by including the file / directory name in a text file, ~/.exclude.  There's really nothing spectacular in my script that makes the progress bar work -- Michal Kwiatkowski, the author of tarp.pl, did all the hard work.There were a few weird things about the way tarp.pl worked -- sometimes generating a divide-by-zero error if filenames were enclosed in quotation marks, and so forth.  Apparently the script expects a "--progress-bar" switch to display its bar.  I have no clue how it worked with just "--progress," but perhaps it was my failure to read the source code correctly causing the divide-by-0 errors.  Or it could've been a bug in version 0.6-2 which has since been corrected.  Like I said, I'll be updating the parent post of this thread in a sec.  :)

I also had to play around with some of tar's switches to get tarp.pl to work without erroring.  For instance, tarp.pl -cjfpP wouldn't work, whereas tarp.pl -pPcjf would.  If you play with tarp but it doesn't work right, you might have to move some junk around in the tar / tarp statement of whatever script you use.  In any case, you should delete /usr/local/bin/tarp.pl and upgrade to the [final version]("http://joker.linuxstuff.pl/projects/completed"), 0.8-3 (which I'll also attach to my original thread starter).

---

### Post by franestepona on 2008-01-28
Hi calraith,

Thanks for considering excluding directories in your script. I was thinking to use two versions of your script, one to backup the whole system (by including jast a slash in the first element of the include matrix) and another to backup just a couple of directories.

But when I try to use the one that back up the whole system I get this error:

```
[10:39:55]Fran@FransMachine: '/home/fran/Media/Backup/Scripts/Backup_System2' 
Option exclude requires an argument
Option exclude requires an argument
/bin/tar: Cowardly refusing to create an empty archive                    ]
Try `/bin/tar --help' or `/bin/tar --usage' for more information.
 | [                                                                      ] 000%

real    0m0.462s
user    0m0.080s
sys     0m0.016s
ls: /home/fran/Media/Backup/System/backup-Jan-28-2008.tar.bz2: No such file or directory

```

And the script I used is as follows:
```
#!/bin/bash

# destination directory
BACKUP_TO=/home/fran/Media/Backup/System

# p = preserve permissions; P = store absolute path; c = create; j = bzip2; f = overwrite
TAR_FLAGS=pPcjf 

# array of files and directories to be included in the backup
# enclose any paths containing spaces in quotation marks
b[0]=/

## array of patterns matching files and folders to exclude from the backup
ex[0]=/lost+found
ex[1]=/backup.tgz
ex[2]=/mnt
ex[3]=/sys
ex[4]=/opt/google-earth
ex[5]=/home/fran/Media
#ex[6]/home/fran/.miro/Movies
#ex[7]/media/
ex[8]=*Cache*
ex[9]=*.bak

############################## nothing else needs to be edited ################################

function make_backup {
    local timestamp=$(date | sed -r -e 's/^\S+ //' -e 's/([0-9]+:){2}[0-9]+ //g' -e 's/[A-Z]{3} //' -e 's/ +/-/g')
    local bakfile=$BACKUP_TO/backup-$timestamp.tar.bz2
    # Unless the P flag is included in $TAR_FLAGS, tar will brag about removing leading slashes.
    # By the time this bit executes, we will have already silently removed them.  cd / to keep sane.
    cd / >/dev/null
    time sudo tarp -$TAR_FLAGS $bakfile $INCLUDES --progress-bar
    cd $OLDPWD >/dev/null
    ls -sh --color $bakfile
}

EXCLUDES=
for (( x=0; x<${#ex[@]}; x++ )); do {
    # prepend --exclude= to the element and escape spaces
    ex[$x]=`echo '--exclude='${ex[$x]} | sed -r -e 's/ /\\\\ /g'`
    EXCLUDES=`echo ''$EXCLUDES ${ex[$x]}`
}; done

INCLUDES=
for (( x=0; x<${#b[@]}; x++ )); do {
    # if array element is the name of a directory
    if [ -d "${b[$x]}" ]; then
        # append a trailing /, but only if not already existing
        # append a trailing /, but only if not already existing
        b[$x]=`echo ${b[$x]} | sed -r -e 's/([^\/])$/\1\//'`
    else
        # otherwise, try removing trailing slash in case this is a regular file
        b[$x]=`echo ${b[$x]} | sed -r -e 's/\/$//'`
        # if array element *still* can't be found in the filesystem
        if [ ! -f "${b[$x]}" ]; then
            # don't bother adding it to the backup list -- insult user instead
            read -p "Dropping ${b[$x]} -- file does not exist.  Replace user and strike any key to continue." -n 1
            echo;
            b[$x]=" "
        fi
    fi
    # escape spaces in the filename and remove leading slashes (so tar won't make a
    # big deal about doing it for us, otherwise ruining our pretty pretty output)
    b[$x]=`echo ${b[$x]} | sed -r -e 's/ /\\\\ /g' -e 's/^\///'`
    INCLUDES=`echo $INCLUDES ${b[$x]}`
}; done

if [ "$EXCLUDES" != "" ]; then
    INCLUDES=`echo ''$EXCLUDES $INCLUDES`
fi

make_backup
```

Can you detect the problem? Is it okay to write just "/" if I want to backup everything? By the way I've detected that it also shows an error message when a directory in the exclude list doesn't exist, since the exclude matrix is not that important maybe could be good to tell the program to skip an element that doesnt exist in the exclude matrix?

Thanks again, I cant wait to make it work.

---

### Post by calraith on 2008-01-28
> **franestepona said:**
> Can you detect the problem? Is it okay to write just "/" if I want to backup everything? By the way I've detected that it also shows an error message when a directory in the exclude list doesn't exist, since the exclude matrix is not that important maybe could be good to tell the program to skip an element that doesnt exist in the exclude matrix?

Thanks again, I cant wait to make it work.

I believe the problem was that the loops populating the includes and excludes got confused when array elements were commented out, not contiguous.  Your ex[] array jumped from ex[5] to ex[8], which the script didn't like.

That should no longer be a problem.  I modified the script again, so that now you can safely comment out backup items, both in the files to back up, and the files to exclude.

To answer your question about using "/" to back up everything, the answer is, yes.  Go for it.

---

### Post by franestepona on 2008-01-30
Great! Now it works perfectly! It works very good to backup folders, but the whole system takes forever when  "Preparing progress bar..." Anyway great script, and very good job!

Cheers.

---

