---
title: "whereis"
date: 2012-10-09
forum: Programming Talk
---

### Post by DarkAmbient on 2012-10-09
Is the whereis -commando something that comes with all/most linux-dists?

Trying to come up a platform-independent way of checking for some package... This works for me in Ubuntu and Arch.

```
whereis somepackage | awk '{ print $2 }'
```

it would return a string (/usr/bin/somepackage in my case) if installed, nothing if not installed. Will this always be the case no matter distro?

---

### Post by ssam on 2012-10-09
you might want to use ```
which
```

according to [http://www.linuxquestions.org/questions/linux-newbie-8/what-is-the-difference-between-whereis-and-which-commands-655031/](http://www.linuxquestions.org/questions/linux-newbie-8/what-is-the-difference-between-whereis-and-which-commands-655031/) whereis only looks in certain hardcoded places, but which searches the whole PATH. i.e. which will actually tell you what binary would be run if you typed the command into a terminal.

---

### Post by DarkAmbient on 2012-10-09
sweet, thanks a bunch! I will try out which instead. Have a nice day :)

---

### Post by Bachstelze on 2012-10-09
What do you mean by "package"? whereis and which search files, not packages.

---

### Post by DarkAmbient on 2012-10-09
Sorry, perhaps a bad way of puttin it. I am after a (somewhat distro-independent) way to check if the user has a certain program/tool installed, my script depends on a few tools such as gksu, zenity and wget, and I would like the user to know that he/she doesn't have the required program installed, if that's the case. And ```
whereis -b wget
``` seems sufficient as it's checking for matching installed binaries.

which that ssam pointed out seemed even better, but which does not seem to return anything.. so I'm unable to use it in a if-statement or so.

---

### Post by MG&amp;TL on 2012-10-09
From what I've seen of *configure* scripts, autoconf seems to be right up your street. However, bear in mind that it's an exceedingly complete and complex piece of software.

Perhaps something to consider.

---

### Post by Bachstelze on 2012-10-09
If the user doesn't have them, they will see the "command not found" error message when they run the script, that should be good enough.

---

### Post by drmrgd on 2012-10-09
Not sure what language you're using, but I'll assume BASH since you've asked about 'whereis' and 'which'.  If the file is not located in $PATH, which won't return anything to stdout except a non-zero exit code.  You could use that and the BASH special parameter '$?' to determine whether or not the file is in $PATH.  Here's a quickie example that may not be 100% correct but gives you an idea:


```
#!/bin/bash

echo "What is the program you want to test: "
read APP

which $APP
if [ $? -ne 1 ]; then
        printf "The program is in your path.\n"
else
        printf "The program is not found in your path!\n"

fi
 
```

---

### Post by DarkAmbient on 2012-10-09
Thanks for the help guys! Well, the reason why I would like to check for a certain installed binary is that the script (which you find in my signature) is all-graphical. So upon missing dependency the user should be asked if he/she wants to install (how I havn't figured out just yet as zenity which Is normally used may be the missing dependency) it or simply not continue running the script.

---

