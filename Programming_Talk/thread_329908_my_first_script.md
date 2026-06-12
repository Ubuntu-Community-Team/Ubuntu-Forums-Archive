---
title: "my first script"
date: 2007-01-02
forum: Programming Talk
---

### Post by energiya on 2007-01-02
Hi,

After deleting something that I shouldn't have, I decided to use a backup program so I installed simple-backup using aptitude. Ok... it works! Now I decided to make a very simple backup script so that I can save my work to a vfat partition. After quickly reading a tutorial, I made this:
```
#!/bin/sh
BPATH=/media/hda6/backup
DIRN=$BPATH"/"`date +%F`
if [ ! -d $DIRN ]; then
    echo -n "$DIRN: No such directory. Creating... "
    mkdir $DIRN
    echo "done"
  else
    echo $DIRN
    echo -n "Direcory exists. Are you sure you want to overwite? [y/n]:"
    read answ
    case "$answ" in
    ["y","Y"])
       echo -n "Removing data... "
       cd $DIRN
       rm -r *
       echo "done"
       ;;
     ["n","N"])
       echo "Exiting..."
       exit 0
       ;;
    esac
fi
echo "saving:"
echo -n "sources.list... "; cp /etc/apt/sources.list $DIRN"/sources.list"; echo "done"
echo -n "menu.lst... "; cp /boot/grub/menu.lst $DIRN"/menu.lst"; echo "done"
```

It works, but this is my first "more complex" script, and I'm sure I made something wrong, and if not, is there a more "professional" way of doing this?

P.S.
I'm not going to save sources.list and menu.lst, I'm just using these as an example. I will use it to copy my work (crossplatfom programming using fp).

Thanks

---

### Post by rekahsoft on 2007-01-02
Looks fine to me :)

---

### Post by energiya on 2007-01-03
Thanks, that means I can start working... :)

---

