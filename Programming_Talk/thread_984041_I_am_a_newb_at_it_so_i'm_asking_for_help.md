---
title: "I am a newb at it so i'm asking for help"
date: 2008-11-16
forum: Programming Talk
---

### Post by Th3D0n on 2008-11-16
First of all i would like to apologize if i didn't post in the correct section. Well here it goes:
I have to make this program called Hello.sh which can offer information about a user account as well as information related to the time of the day + add additional commands to show the shell in use and last commands visualized and any other information at one's choice. i have been given this code as a starting point 
#!/usr/local/bin/bash

if [ `expr \`date +%H\` \< 12` = "1" ] ; then
    printf "Good Morning!\a\n"
elif [ `expr \`date +%H\` \< 18` = "1" ] ; then
    printf "Good Afternoon!\a\a\n"
else
    printf "Good Night!\a\a\a\n"
fi

fi

Please if anyone can help me with this and knows the command lines in ubuntu terminal feel free to answer.

Thanks a lot,
Deian

---

### Post by kerry_s on 2008-11-16
sorry, we don't do homework. your going to have to find another way to cheat.

---

### Post by Th3D0n on 2008-11-16
whatever u say...this is not a homework...thanks for nothin'

---

### Post by dwhitney67 on 2008-11-16
> **Th3D0n said:**
> First of all i would like to apologize if i didn't post in the correct section. Well here it goes:
I have to make this program called Hello.sh which can offer information about a user account as well as information related to the time of the day + add additional commands to show the shell in use and last commands visualized and any other information at one's choice. i have been given this code as a starting point 
#!/usr/local/bin/bash

if [ `expr \`date +%H\` \< 12` = "1" ] ; then
    printf "Good Morning!\a\n"
elif [ `expr \`date +%H\` \< 18` = "1" ] ; then
    printf "Good Afternoon!\a\a\n"
else
    printf "Good Night!\a\a\a\n"
fi

fi

Please if anyone can help me with this and knows the command lines in ubuntu terminal feel free to answer.

Thanks a lot,
Deian

It's very odd to see
```

#!/usr/local/bin/bash

```
Usually bash is installed in /bin, but I guess on your system it is different.

You can get the user's name by examining the environment variable USER (or perhaps USERNAME).  The shell in use is specified in SHELL.

As for the "last commands visualized", I have no idea what you mean by that.  Do you mean a command history?  If so, the 'history' command may be of use to you.

P.S.  echo $USER $SHELL

---

### Post by Th3D0n on 2008-11-16
thanks for helping a lil'

---

### Post by mali2297 on 2008-11-16
You can get a list of the defined environment variables via the command
```

env

```

---

### Post by Keith Hedger on 2008-11-16
For a great guide to bash programming check out the Advanced Bash Scripting guide in the repos

---

### Post by kerry_s on 2008-11-16
> **Th3D0n said:**
> whatever u say...this is not a homework...thanks for nothin'

just making sure. :lolflag:

user = echo $USER 
time of the day = date
show the shell in use = echo $SHELL
last commands visualized = tail ~/.bash_history 
other information at one's choice = i'm not psychic

---

### Post by jimi_hendrix on 2008-11-16
for the last one pick what options you want to give the user and then use a switch statement

---

### Post by drubin on 2008-11-17
> **kerry_s said:**
> sorry, we don't do homework. your going to have to find another way to cheat.

This really doesn't seem like a home work assignment. If they are teaching Bash scripting in school/uni I am all for helping them out :)

> **Th3D0n said:**
> whatever u say...this is not a homework...thanks for nothin'
Not every thing needs a reply.. 


Please take a look at the stickies for guides to programming in bash. There are tones of tutorials for getting started.

---

