---
title: "bash script, if device exists"
date: 2007-09-07
forum: Programming Talk
---

### Post by PetePete on 2007-09-07
ive written a script to backup my /home to my external drive and write a few details to a log.

but I want to have the code check if the external drive is plugged in, so something in pseudo code like..

if (/media/disk exists) {

     do the rsync and write details to log file
}

how could this be done in bash?

Thanks.

---

### Post by gnusci on 2007-09-07
you must need to check when the device exist something like:

```
if [ -f /media/disk ] ; then {
...
}
```

**-f** will check if the file exist...

---

### Post by PetePete on 2007-09-07
thanks for pointing me in right direction.
but to clarify if anyone looks at this thread for help its 
if [ -d /media/disk ]  as its checking for a directory not a file

thanks!

---

### Post by gnusci on 2007-09-07
I am happy you solved your problem...

Just mark this thread [COLOR="Red"]solved[/COLOR] with the "Thread Tools"

---

### Post by robert_pectol on 2007-09-07
Probably better to check in /etc/mtab since that file contains a list of all currently mounted devices.  Something along the lines of:

```

if grep '/media/disk' /etc/mtab > /dev/null 2>&1; then
    echo "mounted"
else
    echo "not mounted"
fi

```

Add code to the appropriate sections to do something useful other than echo messages to the screen.  Good luck!

---

### Post by OldManRiver on 2011-09-12
> if grep '/media/disk' /etc/mtab > /dev/null 2>&1; then
    echo "mounted"
else
    echo "not mounted"
fi


robert_pectol,

I have a flash drive that always shows as 'E441-2317' and it shows in the "etc/mtab" file when inserted.  I want it to mount as "/flash" and so I have the code:
```

if grep 'E441-2317' /etc/mtab > /dev/null 2>&1; then
    mkdir /flash
    # parsing line
    mount $what /flash
fi

```
What parsing is needed, in the "# parsing line" to get the first string set/portion of "/dev/?" for my flash drive from the grep string you are producing here, assigning it to my $what var?

Thanks!

OMR

---

### Post by sisco311 on 2011-09-12
@OldManRiver

Necromancy. I moved your post [thread=1843083]here[/thread]

Thread closed.

---

