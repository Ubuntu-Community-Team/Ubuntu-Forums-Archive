---
title: "[SOLVED] shell script: stripping a combined, multiple (3) output and running command"
date: 2007-12-09
forum: Programming Talk
---

### Post by mdpalow on 2007-12-09
Hi Everyone,

Can you tell me what bash command would do the following:

I want to take some output that would be diplayed as [COLOR="Red"]output 1 output 2 output 3[/COLOR] and be able to put it in a command like:

echo "output 1"
echo "output 2"
echo "output 3"

However, the output above may NOT always contain three outputs. Sometimes it might just be one [COLOR="Red"]output 2[/COLOR] - so I know I will need the IF/THEN statement, but how do you strip out the output individually and put it in a separate command.

Hope that makes sense,

Thanks in advance for any help...

---

### Post by scorp123 on 2007-12-09
Can you explain in detail what you want to do? Because you could just as well do e.g.

echo $OUTPUT1 $OUTPUT2 $OUTPUT3

... if only $OUTPUT2 is set and the other two are empty then only $OUTPUT2 will be displayed, wrestling with "if ... then ... else" statements isn't even necessary.

---

### Post by mdpalow on 2007-12-09
I can't think how I can explain it better, but I can tell you the output will not be able to have a $ in front of it.

the three options to select from in the script are:

/
/home
device files

which is output as follows (if all three were selected):

/ /home device files        # (no , ; -  just a space between the three)

not all three will be output each time, so I could get:

/ device files

or just:

/home

I don't need help with running a command against the output (that's not a problem), but I do need to parse the output in order to run a command against it.

Hope that makes a little more sense. :)

thanks again...

---

### Post by scorp123 on 2007-12-09
> **mdpalow said:**
> but I can tell you the output will not be able to have a $ in front of it. you are familiar with the concept of using variables, yes? :)

...
VARIABLE1=`/path/to/binary/that/we/will/execute/to/have/output -someparameter /path/to/datafile`
echo $VARIABLE1
...

Maybe it would help if you copy & paste your script here.

---

### Post by mdpalow on 2007-12-09
Here's where I'm at...

#!/bin/bash

ans=$(zenity --list --width=630 --height=200 --text "Select one or more options to perform" --checklist --column "  Pick " --column "Action				" --column "Comments" FALSE "Back-Up /" "Step 1 of 3  -  Does not include /home or Device files" FALSE "Back-Up /home" "Step 2 of 3  -  Does not include / or Device files"  FALSE "Back-Up Device Files" "Step 3 of 3  -  Does not include / or /home" --separator=", "); echo $ans

sleep 5

If you click all three options, you'll get the output I'm trying to work with.

If I were to pick 1, 2, or all three options, I would like to be able to parse the output ($ans) and use it in 1, 2, or 3 separate commands.

thanks again..

---

### Post by geirha on 2007-12-09
It's easier if you set the seperator to newline with ```
--seperator="\n"
```

Then iterate through the answers with a while loop:
```

echo -e $ans | while read line
do
  case "$line" in
    "Back-Up /") echo "Backing up root" ;;
    "Back-Up /home") echo "Backing up home" ;;
    "Back-Up Device Files") echo "Backing up dev" ;;
    *) echo "You shouldn't get this line" ;;
  esac
done

```

---

### Post by mdpalow on 2007-12-09
That was clever with the \n for separator; wish I had thought of that.

Thank you very much for your help geirha. Appears to work perfectly.

I'll mark as solved.

---

### Post by geirha on 2007-12-09
BTW, Back-up Device files, is that intended to backup the /dev directory? if so, that's a bit pointless since the device nodes in /dev are created dynamically by udev. i.e. if you insert an usb drive, udev will automatically create /dev/sdb and /dev/sdb1 or similar for that drive and it's partition(s).

---

### Post by mdpalow on 2007-12-09
> **geirha said:**
> BTW, Back-up Device files, is that intended to backup the /dev directory? if so, that's a bit pointless since the device nodes in /dev are created dynamically by udev. i.e. if you insert an usb drive, udev will automatically create /dev/sdb and /dev/sdb1 or similar for that drive and it's partition(s).

No, it backs-up the xorg.conf, fstab files and a couple others.

Thanks for following-up though. :)

---

### Post by scorp123 on 2007-12-09
> **mdpalow said:**
> No, it backs-up the xorg.conf, fstab files and a couple others.  You mean /etc? Wouldn't it be better then to call it "Config Files" instead of 'device files'?

BTW, did you ever test if a restore works? e.g. on purpose destroy your system and then try a "bare metal" recovery? You could test that e.g. with a VMware or VirtualBox virtual machine (so you don't accidentally destroy your real installation).

---

### Post by mdpalow on 2007-12-10
> **scorp123 said:**
> You mean /etc? Wouldn't it be better then to call it "Config Files" instead of 'device files'?

BTW, did you ever test if a restore works? e.g. on purpose destroy your system and then try a "bare metal" recovery? You could test that e.g. with a VMware or VirtualBox virtual machine (so you don't accidentally destroy your real installation).

Originally when the script was written, it only backed up the fstab, so it was called device, but as it grew I never changed the name.

However, it was a good suggestion and I changed it now.

Tested it many times and it works perfectly.

Thanks...

---

