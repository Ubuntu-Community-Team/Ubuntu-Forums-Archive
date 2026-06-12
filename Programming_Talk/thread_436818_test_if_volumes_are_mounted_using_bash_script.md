---
title: "test if volumes are mounted using bash script"
date: 2007-05-08
forum: Programming Talk
---

### Post by munkyeetr on 2007-05-08
I have found the code to do this before, and now I cannot remember nor find it again.  Basically I want to test if volumes are mounted from inside a bash script, and take action depending on the finding.

Pseudocode:

volume="/media/storage"

if [ $volume is mounted] then
     echo "mounted"
else
     echo "not mounted"
fi

Can someone please help.

---

### Post by heimo on 2007-05-08
This seems related, I'm not sure if it's done correctly:
[http://forums.macosxhints.com/showthread.php?t=14156](http://forums.macosxhints.com/showthread.php?t=14156)

---

### Post by blackened on 2007-05-08
This follows the basic syntax you laid out.
```
volume="/media/storage"

if mount|grep $volume; then
echo "mounted"
else
echo "not mounted"
fi
```

---

### Post by munkyeetr on 2007-05-08
Different than what I used before (I think there was an -e switch somewhere in the if statement), but this does what I need it to do.

Much thanks blackened.

---

### Post by blackened on 2007-05-08
As ever, there's more than one way to skin the proverbial cat.

---

### Post by hartz on 2007-05-08
The above test could result in some false positives.  For example you may want to check whether /mydata is mounted, and someone might just have a usb-disk mounted under /media/mydata.  The test will pass as the "grep" will find the string "/mydata" in "/media/mydata".

Many other possible false positives might be encountered, especially with nested mountpoints.

A safer check would be

```
....
if [ mount | grep "on ${volume} type" > /dev/null ]
then
...
```

The entire string "on ${volume} type" needs to match and this avoids matching sub-strings.

---

### Post by munkyeetr on 2007-05-08
thanks hartz3, i'll try that when I get home tonight.

---

### Post by hartz on 2007-05-10
My appologies, there is a mistake in my code.  It should look like this:

```
....
if mount | grep "on ${volume} type" > /dev/null
then
...
else
...
fi
```

... Note the missing [...] brackets.

or alternatively

```
mount | grep "on ${volume} type" > /dev/null
if [ $? -eq 0 ]
then
...
else
...
fi
```

---

### Post by munkyeetr on 2007-05-10
thanx again.

---

### Post by A.Jay on 2009-03-11
As mentioned before there are more then one solutions for a problem, so here is another one:

libsmount="/some/potential/mount/point/to/check";

mountpoint $libsmount
if [ $? -eq 0 ] ; then
        echo "already mounted"
else
        echo "not mounted do it now"
fi

Cheers

---

### Post by lensman3 on 2009-03-12
grep the file "/etc/mtab".  mtab is kept up to date by the kernel with all mounted file systems.  /etc/mtab is also found on Suns and Macs.

---

### Post by terrrorr on 2009-05-14
Hi,

Could someone tell witch one is most reliable one if you want to make sure if networkshare is allready mounted

1. Use mount command to list all mountpoints
2. Use mountpoin command to search if path is mounted
3. grep or cat from /proc/mount
4. grep /etc/mtab 

- Terrrorr

---

### Post by ibuclaw on 2009-05-14
> **terrrorr said:**
> Hi,

Could someone tell witch one is most reliable one if you want to make sure if networkshare is allready mounted

1. Use mount command to list all mountpoints
2. Use mountpoin command to search if path is mounted
3. grep or cat from /proc/mount
4. grep /etc/mtab 

- Terrrorr

Natural choice would be **/etc/mtab**, it shows the exact same information as mount, but is quicker to access directly.

Also, if you have a question, can you please create a new thread next time.

Regards
Iain

---

### Post by dn* on 2009-06-03
I was wondering if someone could help me out by making a script similar to this. Basically, I want to have a quick launch icon I can click that will

1. Mount a directory if it is not mounted 'mount /media/my_mount' 
2. Unmount the directory if it is mounted 'umount /media/my_mount'

Thanks in advance!

---

### Post by bwakkie on 2009-09-03
mount | grep "/mnt/mymount" /etc/mtab > /dev/null
if [ $? -ne 0 ]; then
sudo mount -t cifs //192.168.1.100/d$ /mnt/mymount -o credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777
else
sudo umount /mnt/mymount
fi

where /root/.smbcredentials looks like: (no spaces)
username=myname@MYDOMAIN
password=myp4ssw0rd

---

