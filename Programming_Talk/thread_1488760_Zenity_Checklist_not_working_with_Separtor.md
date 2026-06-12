---
title: "Zenity Checklist not working with Separtor"
date: 2010-05-20
forum: Programming Talk
---

### Post by t-molli on 2010-05-20
Hi All,

A little confused by why this isn't working anymore.

```
#!/bin/bash

ans=$(zenity --list --checklist --width=630 --height=200 --text "Select one or more options to perform" --column " Pick " --column "Action " --column "Comments" FALSE "1" "Whatever" TRUE "2" "Whatever" TRUE "3" "Whatever" --separator="\n"); echo $ans

echo -e $ans | while read line 
do
  case "$line" in
    "1") echo "You Selected 1" ;;
    "2") echo "You Selected 2" ;;
    "3") echo "You Selected 3" ;;
  esac
done
sleep 25

```

When running this in terminal, I don't see the '--separator="\n" creating new lines for the output. Instead, it's showing on one line. And, it's not reading the lines and providing the output of the associated selection with the 'case' command.

It's been a while for me, so I'm wondering if anything has changed that I'm unaware of or is it just something I'm missing?

Any help is greatly appreciated.

---

### Post by kaibob on 2010-05-20
I think it will work if you double quote $ans (two spots).

---

### Post by dwhitney67 on 2010-05-21
This thread was posted yesterday, which discusses how to interpret return values from zenity:

[http://ubuntuforums.org/showthread.php?t=1345808](http://ubuntuforums.org/showthread.php?t=1345808)

It is unfortunate that you did not perform a search for this thread yourself; it is so easy to do so.

---

### Post by kaibob on 2010-05-21
> **dwhitney67 said:**
> This thread was posted yesterday, which discusses how to interpret return values from zenity:

[http://ubuntuforums.org/showthread.php?t=1345808](http://ubuntuforums.org/showthread.php?t=1345808)

It is unfortunate that you did not perform a search for this thread yourself; it is so easy to do so.
I think the OP posted to that thread, so he was aware of it.

---

