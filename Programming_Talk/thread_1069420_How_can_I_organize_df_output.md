---
title: "How can I organize df output?"
date: 2009-02-13
forum: Programming Talk
---

### Post by jyaan on 2009-02-13
I often use the command ```
df -h
``` to list the free space of my partitions. I would like to know if there is a way to organize this output by various attributes such as percentage used, free space available, total disk size and so on. 

I didn't see any built-in options in the df man page. Maybe it can be done with sed? Maybe a different command entirely? All of the partitions I made are Ext3 (aside from swap), and I use LVM2.

---

### Post by lykwydchykyn on 2009-02-14
You could use a combination of awk and sort, though it would get messy and it'd be hard to get exactly what you wanted.  Numbers, in particular, aren't going to sort right when you use the -h option (i.e., 10G will come before 500M).

Awk may be able to do it on its own, it's pretty powerful but the syntax is a little weird.

---

### Post by jyaan on 2009-02-14
Well, I'm just looking for a simple way to do it. If only I could type something like "df -hfp" for free percent, "df -hs" for size, "df -hu" for used space, etc. I guess if I really want it I might just have to write some kind of wrapper. Perhaps downloading the df source and adding the options I want would be a nicer thing to do. I don't really want to go through all that trouble for such a simple thing, though. :S

---

### Post by cdtech on 2009-02-14
You could create your own "df" script:
```
#!/bin/bash

# -------------------------------------------
# modify this one to fit your needs.
# -------------------------------------------

# --------------------------------
# variables:
# --------------------------------

name="mydf"
purpose="list drive information"
sysnopsis="${name} [-fuhl]"
version="1.1"
dev=$2

# --------------------------------
# program:
# --------------------------------

usage () {

echo -e >&2 "\n${name} ${version} - ${purpose}
Usage: ${sysnopsis}

Options:
     -f, free percentage
     -u, used percentage
     -h, options (help)
     -l, see this script \n"

    exit 1
}

# args check
[ $# -eq 0 ] && { echo >&2 missing argument, type ${name} -h for help; exit 1; }

# option and argument handling

while getopts fuhl options; do

    case $options in
        f) df -h ${dev} | awk '{print $4}' ;;
        u) df -h ${dev} | awk '{print $3}' ;;
        h) usage ;;
        l) more $0; exit 1 ;;
       \?) echo invalid argument, type ${name} -h for help; exit 1 ;;
        *) usage ;;
    esac

done
```
You can add what ever you want to this one: create a second flag for your device (ie.. mydf -u /dev/sda1) or whatever. This would be easier than rewriting the entire program.......

**UPDATE::.**
I just threw in the device variable "dev" so type:
mydf -u /dev/sda1
to get the used space.......

---

### Post by geirha on 2009-02-14
If you can live with having sizes displayed in mebibytes instead of a mix of mebibytes and gibibytes etc., then:
```

df -B M | sort -k4 -g # sort by 4th field (Available) numerically
df -B M | sort -k5 -g # sort by 5th field (Use%) numerically

```

---

### Post by jyaan on 2009-02-15
cdtech: You script sort of works since it shows the data I'm looking for, but unfortunately still has the problem of being out of order.

geirha: Those are exactly the options I needed, thanks. It doesn't matter to me if the size is in GB or MB, I just want to be able to compare the data quickly.

Now I'll just make a script like above to add in the sorting.

---

