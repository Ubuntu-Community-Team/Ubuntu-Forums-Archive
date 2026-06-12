---
title: "Batch copy to CD/DVD"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by steveray100 on 2012-02-16
I am wondering if there is a Linux CD/DVD copying program that will essentially, let me pick a folder which, let say, has 15 Gigs of folders programs,documents etc. Then figure out how many DVDs It will need to copy them all so that each DVD has the maximum capacity
and then just keep asking me for another DVD until all the folder/files are burned. Will CD/DVD Creator or Brasero do this?

---

### Post by TeoBigusGeekus on 2012-02-16
I've taken the liberty to write a script for you
```
#!/bin/bash
size=0
burn_string="growisofs -Z /dev/sr0 -RJ "
for item in *;do
    temp=$(du "$item" | sed 's/\t.*$//g') 
    size=$((size+temp))
    if [[ -f $item ]]; then
        burn_string+=" "
        burn_string+=$item
    fi
    if [[ -d $item ]]; then
        burn_string+=" "
        burn_string+="-graftpoints /"
        burn_string+=$item
        burn_string+="="
        burn_string+=$item
    fi
    if (( size >= 4500000)); then
        read -p "Insert a blank dvd"
        $burn_string
        burn_string="growisofs -Z /dev/sr0 -RJ "
        size=0
    fi
done
```
Replace /dev/sr0 with whatever applies to your system (/dev/dvd, /dev/cd, /dev/cdrw, etc.)
Put the script in the folder, make it executable
```
chmod +x name_of_the_script
```
and run it
```
/path/name_of_the_script
```

_DISCLAIMER:_ I haven't tested it, as I don't have the patience to burn 5, or 10, or 50 dvds. Any coasters are yours and yours alone. If it doesn't work, I owe you a sixpack. If it works, you owe me a twelvepack.

---

### Post by Scott Baker on 2012-02-16
I've done this with Brasero, and it works very well.

---

