---
title: "Getting user consent to use system and terminal"
date: 2008-07-28
forum: Programming Talk
---

### Post by dwhitney67 on 2008-07-28
I have a simple shell script that prompts the user for his/her consent that they are operating on a "special" system.  Where would I call this script from if I needed to query the user each time they perform any of the following operations?
[LIST]
[*]ssh anyuser@localhost
[*]su - root
[*]su -
[*]su
[*]gnome-terminal
[*]xterm
[/LIST]

I've tried calling the script from /etc/profile, however it does not get invoked when running su, gnome-terminal or xterm.  What are my other choices?

User's can be using bash, csh, (maybe zsh?) environments.  I also do not need the script running when gdm is invoked.  That would hang up gdm!

Also, on a side-topic, how do I prevent the script from being interrupted?  Is a trap "" 2 sufficient, or should I call out each and every signal?

P.S.  The script contains more detail than what is shown below, but the gist is there:
```
#!/bin/sh

trap "" 2

query=true

while [ $query ]
do
        echo -n "Do you consent to using this system (yes/no)? [no] "
        read ans

        case "$ans" in
                "yes")  exit 0;;
                "no")   echo "Sorry, you will be logged out!"; exit 1;;
                "")     echo "Sorry, you will be logged out!"; exit 1;;
                *)      echo "Error: Illegal input, try again...";;
        esac
done
```

P.S.S.  Within /etc/profile, the script is invoked by:
```
/usr/sbin/consent.sh || exit 1
```

---

