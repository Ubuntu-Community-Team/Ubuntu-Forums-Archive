---
title: "upgrade script"
date: 2007-11-24
forum: Programming Talk
---

### Post by Marinodimare on 2007-11-24
Hi,

I am trying to make a script to automatically upgrade my Ubuntu box. It now looks like this:
```

#!/bin/bash
#automatic updater



if [ "$(id -u)" != "0" ]; then
	echo "you must be superuser to execute this script"
	exit 1
fi

apt-get update

if [ "$(apt-get update)" != "0" ]; then
	echo "there is a problem with the update procedure"
#	exit 1
fi

apt-get -y dist-upgrade

exit
```

This way, my repositories are updated before the system is, avoiding trouble in dependencies etc. 

the problem is that there are some repositories that are ignored by apt-get update. This causes the exit signal to be other than 0, so if I uncomment the 

```
...
#	exit 1
...
```

line, the script aborts. This brings me to my question. I want to be able to see the exit status apt-get update renders so I can build into the script a function to ignore the ignoring of repositories, but still exit at other problems. Could anybody tell me how to see the exit status of a process?

Thanks,

Marijn

---

### Post by geirha on 2007-11-24
> **Marinodimare said:**
> 
```

apt-get update

if [ "$(apt-get update)" != "0" ]; then

```


$(apt-get update) actually runs that command (identical to doing `apt-get update`), and the output of that command (not the return value) will be compared to "0". 

What you want is:
```
if [ $? != 0 ] ; then
  echo apt-get update failed;
fi
```

the special variable $? contains the return value of the last run process in that scope.

---

### Post by Marinodimare on 2007-11-24
It works, thanks!

but still, is there a general way to measure return values?

---

### Post by geirha on 2007-11-24
I guess this is the more general way:
```
 if ! apt-get update ; then
  echo it failed
fi
```

you could also simply do:
```
apt-get update && apt-get -y dist-upgrade
```
command1 && command2 means that command2 will run only if command1 succeeds (returns 0)

---

### Post by Marinodimare on 2007-11-24
thanks for the tips.

the other problem I have is that for some reason Gutsy doesn't recognize my bash_profile. I copied the one from my laptop (which runs Dapper), edited it to fit the new system to include /home/user/.bin in PATH, but even after a complete system reboot that folder still isn't in my path.

---

### Post by geirha on 2007-11-24
Looks like that's a bug. According to the man-page, it will read ~/.bash_profile when starting an interactive shell, but it only seems to read it when it's a login shell "bash --login". It should work if you put that PATH addition in ~/.bashrc though.

---

### Post by smartbei on 2007-11-24
Try adding the PATH addition to .bashrc. I know for sure that gets executed for every [non-logon apprently according to the comment in the file] interactive shell.

---

