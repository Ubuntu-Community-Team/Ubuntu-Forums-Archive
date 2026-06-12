---
title: "Bash script not working - File not found???"
date: 2018-10-26
forum: Programming Talk
---

### Post by hartman8227 on 2018-10-26
I'm trying to set up a script to backup and update my website and I'm running into a problem with the IF statement that checks for whether or not the upload file is present and I'm not sure why. It keeps jumping to the end and telling me the file is not there. Granted I've no real clue what I'm doing, So I've probably goofed something. do any of ya'll see where I've gone wrong here?


```
#! /bin/bash

## This script is to automatate the updateing of the main
## website. Upload package should be an uncompressed tarball named upload.tar
## Drop it in the upload folder.

# Backup file
CONDOM=/home/ubuntu/backups/hartman-$(date +%Y%m%d).tar
# Upload loacation and file
UPLOAD=/home/ubuntu/Upload/
# Publishing location
FINAL=/var/www/html/
# Package Name 
TARBALL=upload.tar


# internals. Leave alone.
HI=$UPLOAD$TARBALL
FI=$FINAL$TARBALL


if [[ $EUID -ne 0 ]]; then
echo "This script must be run as root"
exit 1
if [ -e $HI ]
then
    echo "backing up Website"
    tar -cf $CONDOM
    echo "Moving Tarball"
    mv $HI $FI
    echo "Extracting Tarball"
    tar -xf $FI
    # echo "Deleting Tarball"  #Commented out during testing
    # rm $FI                         # Test this before going live.
    echo "Congratulations! Your website has been updated"
fi


else
echo "Your update is not present in the upload folder."
echo "Please check your update and try again."
fi

exit
```

---

### Post by spjackson on 2018-10-26
Welcome to the forums.

Your else is associated with
```

if [[ $EUID -ne 0 ]]; then

```
not with 
```

if [ -e $HI ]

```
You need to add a 'fi' line after 'exit 1' and remove the 'fi' line after Congratulations.

---

### Post by SeijiSensei on 2018-10-26
```

    #! /bin/bash

    ## This script is to automatate the updateing of the main
    ## website. Upload package should be an uncompressed tarball named upload.tar
    ## Drop it in the upload folder.

    # Backup file
    CONDOM=/home/ubuntu/backups/hartman-$(date +%Y%m%d).tar
    # Upload loacation and file
    UPLOAD=/home/ubuntu/Upload/
    # Publishing location
    FINAL=/var/www/html/
    # Package Name 
    TARBALL=upload.tar


    # internals. Leave alone.
    HI=$UPLOAD$TARBALL
    FI=$FINAL$TARBALL


    if [[ $EUID -ne 0 ]]; 
    then
        echo "This script must be run as root"
        exit 1
**    fi  # close this if here; if not root, exit and end**

    # continue on if user is root
    if [ -e $HI ]
    then
        echo "backing up Website"
        tar -cf $CONDOM
        echo "Moving Tarball"
        mv $HI $FI
        echo "Extracting Tarball"
        tar -xf $FI
        # echo "Deleting Tarball"  #Commented out during testing
        # rm $FI                         # Test this before going live.
        echo "Congratulations! Your website has been updated"
    else
        echo "Your update is not present in the upload folder."
        echo "Please check your update and try again."
    fi

    exit

```

---

### Post by hartman8227 on 2018-11-14
Thank you both. That got the script working. However, me being me I kept twiddling with it and playing with it till I finally realized I was going about this the hardest way possible. In the hopes that this post finds it's way into the hands of someone like me; Remember, why use fifty commands when one will do. Here is my new script.

```
#! /bin/bash
# Remote Update
# Paul Hartman
#
# Program used to update the website from the development system. Replacement for update.sh
# I'll just go ahead and say it. I'm occasionally a #censored#. Much more elegant.

rsync -vrze ssh ~/local/directory username@server.com:/remote/directory


# For passwordless access to work, setup cofig in .ssh/config file
# Host hostname
#     User username
#     IdentityFile ~/.ssh/somekey
```

---

