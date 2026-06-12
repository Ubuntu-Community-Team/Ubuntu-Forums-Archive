---
title: "udev and Interactive Sheels"
date: 2011-04-10
forum: Programming Talk
---

### Post by HuckBerry on 2011-04-10
(scroll to bottom for the tl;dr version)

I work with some people who, however good at what they do they are, can't seem to copy stuff from one hard drive to another. We handle a reasonable number of client hard drives and copy them onto our machine for backup purposes. The people I work with keep mixing up client's drives, despite the fact that they're all stickered with the client's name. I blamed the 'D:','E:',... naming system from windows and so I built the following udev script:

```
#! /bin/bash 

#udev Rule:
#KERNEL=="sd?[0-9]", PROGRAM="/usr/local/bin/DriveDB.sh\ 
# $env{ID_FS_UUID_ENC}", SYMLINK+="%c"

#BUILD MYSQL QUERY
query='SELECT SYMLINK FROM UUID WHERE UUID='
UUID=$1


#EXECUTE QUERY
#result=`/bin/echo $query"'"$UUID"';" | /usr/bin/mysql -u root -pXXXXXXXXXX DriveDB | /usr/bin/tr '\n' ' ' | /bin/sed s/SYMLINK// | /usr/bin/tr -d ' '` 

#CHECK IF RESULTS ARE BLANK
if [[ "$result" == "" ]] 
 then
 #THIS IS NOT A KNOWN DRIVE
 result=`/usr/bin/zenity --entry --title="Unknown" --text="A new drive was deteched. What is the clients name?`
fi

#REPORT THE DRIVES NAME BACK TO UDEV VIA STDOUT
/bin/echo $result


```

In short, the script does a lookup on each Partition's UUID in a Mysql database that has a UUID<->ClientName(symlink) dictionary. The Script works wonderfully when the UUID is in the database. However when the UUID is unknown, it fails to bring up the zenity prompt. Of course the script works in an interactive shell, but udev doesn't give us that luxury. 

The Short Question: What environment variables do I need to launch zenity from a non-interactive shell

Alternate Short Question: How can I start an interactive shell (i.e. xterm, gnome-terminal, or likewise) from a non-interactive one.

---

### Post by HuckBerry on 2011-04-11
*bump*

If this is the wrong forum, just let me know which is correct.

---

