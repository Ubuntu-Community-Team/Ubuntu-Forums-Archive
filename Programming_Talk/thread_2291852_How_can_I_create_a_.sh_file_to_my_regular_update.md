---
title: "How can I create a .sh file to my regular update"
date: 2015-08-23
forum: Programming Talk
---

### Post by mehmet_salih_binda on 2015-08-23
#SOLVED
#LOOK FIRST REPLY

hello I would like to execute  following commands. 

```
 sudo apt-get update        
 sudo apt-get upgrade        
 sudo apt-get dist-upgrade 

```

I try to write this codes on new .sh file which called update.sh on desktop

```

#!/bin/bash


# sudo apt-get update        
# sudo apt-get upgrade        
# sudo apt-get dist-upgrade 

```

 and try to run on terminal

it returns an error 
```
cybersalih@cyber:~/Desktop$ sudo update.sh
sudo: update.sh: command not found

``` 



How can I repair this or any advice for me ?

Note : I am new on this platforms. If I did a big mistake please ignore it.

---

### Post by TheFu on 2015-08-23
a) '#' is a comment. The first line is special and required.
b) no need to run both upgrade/dist-upgrade - if you want new kernel releases, use dist-upgrade. If you only want patched versions of old kernels, use "upgrade"
c) whenever scripting, always specify full paths to all programs. Often, we want to run scripts with cron, which doesn't have the same environment as a user login. It would be bad for the wrong program to be run - often there are similar programs with the same name on a system and only the PATH controls which is run. Not good as we use more automation.

Yours is an excellent example to show best practices.

```
#!/bin/bash

SUDO=/usr/bin/sudo
APTGET=/usr/bin/apt-get

$SUDO $APTGET update
$SUDO $APTGET dist-upgrade
```

Make sense?   And if you want to expand this to run across 20 systems, it isn't hard, though using a tool like ansible would be a better long term choice.

---

### Post by mehmet_salih_binda on 2015-08-24
Thanks :)

---

### Post by TheFu on 2015-08-24
Oh - sorry - I forgot the 1 thing that you need to see nothing happen from your original script.

Linux doesn't use extensions for anything. Naming a file file.sh means nothing. It doesn't tell the OS it is a program/script and should be able to run.  For that, you must set the "execute" permissions.  I generally do it as** chmod +x file.sh**. Now running ./file.sh will work.

If you are going to do more scripting - some additional background on the OS would be extremely helpful to explain "why" things work the way they do or "why" you need to do things in a certain way.  With Unix systems, there are usually 100-500 different ways to solve any problem - but some answers are better than others.

For example, I tend to put sudo inside scripts.  That can cause issues with redirections and I accept that. I'm lazy.  Some people figure that if you are running a script that needs elevated access, then invoking it with sudo is better.

Also instead of changing the permissions, you could just pass the file as an argument into bash yourself.  **bash ./file.sh** would work.  This is sometimes needed if the script to be run is on non-Unix file systems like vfat or NTFS.

Another common way to do this specific task is to check the result from the first command before bother with the second at all. If the "update" failed, why attempt the "upgrade"
**sudo apt-get update && sudo apt-get upgrade** on a single line. If update isn't error free, upgrade won't work.

Lastly, using apt-get still works, but many people use **aptitude** instead.  Most of the time there isn't any difference in the result. Some times, mostly when installing packages with complex dependencies, apt-get cannot find a safe dependency solution, but aptitude can.  Once apt-get removed my DBMS (mariaDB) and installed the one it wanted (mysql).  Completely trashed the webapp on that machine.  Ran aptitude to reinstall mariadb and had to reject a few dependency solutions before the one I needed came up.  

Lots of different ways to solve an issue.  Around the web, we often see examples that are less than ideal and ignore well-known best practices to the professionals. 

Hope this helps.

---

