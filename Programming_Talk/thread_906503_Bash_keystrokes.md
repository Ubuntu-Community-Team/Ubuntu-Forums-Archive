---
title: "Bash keystrokes"
date: 2008-08-31
forum: Programming Talk
---

### Post by Doctor Debian on 2008-08-31
Hello all,

Just wondering if it would be possible to execute the one-letter user input on my bash scripts upon key press.

Thanks,
DocDeb

---

### Post by stylishpants on 2008-08-31
Use stty to put your tty into raw mode.  Restore it after you capture the input.

See "man stty" for more info.

Example code: 
(stolen verbatim from this thread: [http://www.linuxquestions.org/questions/programming-9/user-input-using-a-bash-script...-72189/](http://www.linuxquestions.org/questions/programming-9/user-input-using-a-bash-script...-72189/))
(this code is ugly, but it demonstrates what you want to see)

```

#!/bin/sh

# global var to hold menu selection
MENU_CHOISE=""

function get_choise() {
    ##################################
    # set the tty driver to raw mode #
    # read a char #
    # restore settings #
    ##################################
    stty raw
    MENU_CHOISE=`dd if=/dev/tty bs=1 count=1 2>/dev/null`
    stty sane
    echo $MENU_CHOISE
}

# print the menu
echo "Menu:"
echo " 1) booz"
echo " 2) smokes"
echo " 3) tea"
printf " please enter your choise: "

# read the menu selection
get_choise

# print the results.
case $MENU_CHOISE in

"1")
echo "Can I see some ID?";;

"2")
echo "Smoking is bad for you";;

"3")
echo "One lump or two?";;
esac
```

---

### Post by Doctor Debian on 2008-08-31
Thank you SO much! I've been struggling with this for a few days now. :)

---

