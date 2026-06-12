---
title: "Script for mounting ntfs partition"
date: 2013-08-23
forum: Programming Talk
---

### Post by achuthpnr on 2013-08-23
I am trying to write a script to mount an ntfs partition or unmount it if already mounted (for learning purposes). As a default I open the mounted partition in thunar.

```

#! /bin/bash
# mount or unmount a ntfs partition using ntfs-3g

tobemounted=/dev/sda2 #this partition must exist
mountfolder=/mnt/Data/ #this folder must exist

ismounted=$(cat /etc/mtab | grep -c $tobemounted)
echo $ismounted

if [ $ismounted = 1 ] ; then 
    title="Partition already mounted"
    question="unmount"
else
    title="Partition not mounted"
    question="mount"
fi

if zenity --question --timeout 20 --title="$title" --text="Do you want to $question \n $tobemounted ?" --height=100 --width=300; then    
    if [ $ismounted = 1 ] ; then 
        echo 'unmount'
        sudo umount $mountfolder
    else
        echo 'mount'
        sudo ntfs-3g $tobemounted $mountfolder
        thunar $mountfolder #opens dir in thunar
    fi  
else 
thunar $mountfolder #opens dir in thunar
echo 'default no'
fi

ismounted=$(cat /etc/mtab | grep -c $tobemounted)
echo $ismounted

exit   

 
```

i see the dialog box appear, but in all cases I get the default no operation. Where am I going wrong? 
Thanks.

---

### Post by steeldriver on 2013-08-23
You need to test the *exit code* not the standard output of zenity, I think - e.g.

```

zenity --question --timeout 20 --title="$title" --text="Do you want to $question \n $tobemounted ?"
**if [ $? -eq 0 ]**; then ...

```

(a press of 'Yes' being interpreted as 'success' i.e. exit code 0 by the usual convention). HOWEVER **there appears to be a bug with the zenity --timeout option because 'Yes' returns '5' (i.e. timeout)** - see [https://bugs.archlinux.org/task/26582](https://bugs.archlinux.org/task/26582) (I confirmed it affects my version, 3.4.0). So try it without the timeout.

Also all your tests are written as string tests - for integer tests you want

```
if [ $ismounted -eq 1 ]; then ...
```

and so on. You might want to look at using the 'mountpoint' command instead of catting mtab.

---

### Post by ofnuts on 2013-08-23
You may have some error in the zenity call that makes it return an error that you code doesn't distinguish from answer "no". zenity --question returns 0, 1, 5 or -1  (yes, no, time out, other errors). What value do you actually see?

Testing your code I get rc=5 if I answer yes with --timeout, removing --timeout fixes it.

Seems to be a zenity bug: [https://bugs.launchpad.net/ubuntu/+source/zenity/+bug/1034594](https://bugs.launchpad.net/ubuntu/+source/zenity/+bug/1034594)

---

### Post by achuthpnr on 2013-08-23
Thanks for the replies. I also found that the problem was with the --timeout option. Apparently it is a bug with Zenity. 

Thread marked as solved.

---

