---
title: "[Script Shell] How can i check for sudo"
date: 2005-08-04
forum: Programming Talk
---

### Post by geearf on 2005-08-04
Hello,

I am doing a little install script for my work using shell, and I want to test wheter the script was started with or with sudo.
If it was without, and I need it I will put it in front of my command ..

But i cannot find a way to check for sudo ($USER only gives me the user).

Thanks for the tip

---

### Post by Sam on 2005-08-04
```
#! /bin/sh

ROOT_UID="0"

#Check if run as root
if [ "$UID" -ne "$ROOT_UID" ] ; then
	echo "You must be root to do that!"
	exit 1
fi
```

---

### Post by geearf on 2005-08-04
Hello, 
I will try this right now,

Thanks a lot :)

---

### Post by geearf on 2005-08-04
Thanks it works flawlessly for my needs :)

Would you also happen to know how can I store 'file /usr/bin/java' in a variable in my script ?


Thanks

---

### Post by Sam on 2005-08-04
You need ` quotes to evaluate an expression.
```
#! /bin/sh

FILE_JAVA="`file /usr/bin/java`"

echo "$FILE_JAVA"
```

---

### Post by geearf on 2005-08-04
Oh ok,

thank you very much for your help,

Do you happen to know a good website for learning shell script (so that I won't bother you too much :) ) ?

---

### Post by Sam on 2005-08-04
Just Google for "[bash tutorial](http://www.google.com/search?&q=bash%20tutorial)" and you'll find a lot of websites...

Here's some:[list][*][Introduction to bash shell scripting](http://www.start-linux.com/articles/article_66.php), a good start
[*][AWK, GRP, SED tutorial](http://linuxcourse.rutgers.edu/lessons/lesson9/shell_script_tutorial.html), useful for parsing command outputs
[*][Introduction to Bash Programming pt. 1](http://www.geocities.com/tipsforlinux/articles2/043.html), [pt. 2](http://www.geocities.com/tipsforlinux/articles2/044.html)[/list]

Ask if you have a question! Happy scripting :wink:

---

### Post by geearf on 2005-08-04
Thanks,

I have looked at shell script and stuff like that, but I always found about the same stuff, that is why I asked here in fact :)

Thanks for your help,

---

### Post by Sam on 2005-08-04
You're welcome!

---

