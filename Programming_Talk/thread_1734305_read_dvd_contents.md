---
title: "read dvd contents"
date: 2011-04-20
forum: Programming Talk
---

### Post by davbren on 2011-04-20
Hey all,
        I'm building a small application and I need access to the program chain for a given dvd. I have no idea how to do it. I've been looking at libdvdread but I think thats more for playing the dvd.

Any Clues?

---

### Post by An Sanct on 2011-04-20
dd is a great command line tool for that, extremely powerful :)

PS. Sorry, for not giving you any actual help, but I thought I'll just point you into the right direction.

---

### Post by davbren on 2011-04-20
lol no worries, I'll check it out. maybe I can explore the source if its foss...

Thanks!

---

### Post by davbren on 2011-04-20
That is some hardcore shiz! 

I'll give it a go, although I'm sure theres a way of using /dev/cdrom I just don't know it yet...

---

### Post by An Sanct on 2011-04-20
Yes I know :) this is low level reading and writing of sectors (no matter what media)

.. try this bash script (with a GUI!), that someone gave me in [this thread]("http://ubuntuforums.org/showthread.php?t=1717025") (I was asking almost the same thing...)

```

#!/bin/bash
list=$(parted -l|grep -B1 /dev/)
list=$(echo $list|tr " " "_"|sed -e "s/_--_/\n/g"|sed -e "s/^/FALSE /")
list="$list $(blkid|tr " " "_"|sed -e "s/^/FALSE /")"
a=""
while [ -z "$a" ]
do
 a=$(zenity --list --text="Select the device or partition you want to save" --radiolist --column="check" --column="device/partition" $list)
 if [ $? = 1 ];then exit 0;fi
done
a=$(echo $a|sed -e "s/.*\/dev\///"|sed -e "s/:.*//")
b=$(zenity --title="select the directory where the file is saved" --file-selection --directory)
if [ -z "$b" ];then zenity --error --text="Nothing was selected. I will do nothing.";exit 0;fi
c=""
while [ -z "$c" ]
do
 c=$(zenity --entry --text="Type the file name of the saved file" --entry-text="${a}backup$(date -I)"|tr -d " "|tr -d "/")
 if [ -e $b/$c ];then
  zenity --question --text="$b/$c already exists. Do you really want to save to $b/$c ? Saving overwrites $b/$c." --ok-label="Save and Overwrites $b/$c"
  if [ $? = 1 ];then c="";fi
 fi
done
zenity --question --text="Can /dev/$a be saved into the file $b/$c?"
if [ $? = 1 ];then zenity --warning --text="Nothing has been saved.";exit 0;fi
dd if=/dev/$a of=$b/$c
zenity --warning --text="/dev/$a has been saved into the file $b/$c."
exit 0

```

PS. Its good to read the whole thread, this post might not be explanatory enough...

---

### Post by davbren on 2011-04-20
This looks waaaaay more than I want to acheive.

I think I can get what I want from /media the only problem is, when I insert a dvd, the name of the mounted drive changes to the name given to the dvd so I'd have to look at the location /media/my_dvd and such like; instead of something like /media/cdrom0

Is there anyway around this?

---

### Post by davbren on 2011-04-20
Maybe I could choose the folder according to its filesystem type. In the case of a dvd UDF?

I think that maybe the only way to differentiate between the folders. Especially if each dvd comes up with a different volume name.

---

