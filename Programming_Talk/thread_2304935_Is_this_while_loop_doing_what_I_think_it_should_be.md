---
title: "Is this while loop doing what I think it should be doing."
date: 2015-12-01
forum: Programming Talk
---

### Post by J_Me on 2015-12-01
The program runs and it seems to be working as expected I just want to make sure.
It should be checking(every 30 seconds) to see if a hard disc drive is present. Once the drive has been inserted it fires off a command(just once) to spin down. Then the process repeats(the drive is hot-swappable).
I wanted to make sure that 'hdparm -S 6 /dev/sdb' executes only once each time the disc is inserted, out of interest if it executed hdparm many times would it break the HDD.
Thanks
```
#!/bin/bash

# This should take one minute to spin down as it waits 30 seconds on either side before executing


FILE=/tmp/spinDownNow
CATPROC=/dev/disk/by-id/ata-HITACHI_HDSK35H332K8864_T46FFGKK3266F


while true; do
  if [ -h "$CATPROC" ] && [ -f "$FILE" ]; then
    sleep 30
  elif [ ! -h "$CATPROC" ] && [ -f "$FILE" ]; then
    rm $FILE
  elif [ ! -h "$CATPROC" ] && [ ! -f "$FILE" ]; then
    sleep 30
  else
    hdparm -S 6 /dev/sdb
    touch $FILE
  fi
done
```

---

### Post by J_Me on 2015-12-01
Ok I worked it out by looking at when the temp file was modified. Anyway if you have suggestions for improvement please let me know. Thank you

---

### Post by SeijiSensei on 2015-12-02
I'm not sure why you have a while loop.  Since it's always true, you get the same results as you would get without the loop.

---

### Post by sisco311 on 2015-12-02
Your script looks okay.

Some *rule of thumb* or *good practice* suggestions:

[list]
[*]The variable names should be lowercase (or contain at least one lowercase character) in order to prevent the accidental overriding of environment and internal shell variables which by convention are fully capitalized.

[*]You should double quote **every** expansion ($FILE)! 
[/list]

If you are using Ubuntu (or any other modern distro which uses udev), you should write a udev rule to run the `hdparm' command each time the disk is attached. If you need any help with that, please feel free to ask.

And you shouldn't use the device name (/dev/sd*) in your command. Use the symlink created in /dev/disk/by-id/ for the specific device. See: [uhelp]community/UsingUUID[/uhelp] and   [https://liquidat.wordpress.com/2013/03/13/uuids-and-linux-everything-you-ever-need-to-know/](https://liquidat.wordpress.com/2013/03/13/uuids-and-linux-everything-you-ever-need-to-know/)

---

### Post by J_Me on 2015-12-05
@sisco311 Thanks for taking the time to explain why I shouldn't be doing something the way I did it really helps to get a clear picture. I'll definitely make all the changes and look into udev as well.[br]1[/br] [br]1[/br] @SeijiSensei I just used whatever I understood to achieve a goal, I'm not a programmer but thanks anyway.[br]1[/br] [br]1[/br] Much appreciation[br]1[/br] J[br]1[/br]

---

