---
title: "What's wrong with my script?"
date: 2012-05-08
forum: Programming Talk
---

### Post by xjonquilx on 2012-05-08
```
#!/bin/bash
echo "This will create a list of installed software that can be re-installed at a later time."
echo "The list is stored in the same folder you opened this script in as installed.log"
echo "This script can only be ran as root or super user."
echo "This script will only work on Ubuntu Linux."
echo "Email questions/comments to jonquil at love.com"
[ "$UID" -ne "0" ] && echo "You must be root to run this script." && exit 1
OPTIONS="Backup Restore Quit"
select opt in $OPTIONS; do
   if [ "$opt" = "Backup" ]; then
      echo "Backing up software..."
      dpkg --get-selections > installed.log
   else if [ "$opt" = "Restore" ]; then
      echo "Restoring software..."
      dpkg --set-selections < installed.log
   else if [ "$opt" = "Quit" ]; then
      echo Done
      exit
   else
      echo bad option
   fi
done
```

---

### Post by sisco311 on 2012-05-08
The syntax of if is:
```
if COMMAND; then
    COMMANDS
**elif** COMMAND; then
    COMMANDS
...
else
    COMMANDS
fi
```

---

### Post by xjonquilx on 2012-05-08
Oops, I pasted the wrong code.

I get the syntax error that "done" is unexpected even if it says elif. I tried else just in case that was the problem, but as you pointed out, it wasn't.

---

### Post by ofnuts on 2012-05-08
> **xjonquilx said:**
> Oops, I pasted the wrong code.

I get the syntax error that "done" is unexpected even if it says elif. I tried else just in case that was the problem, but as you pointed out, it wasn't.
Works for me when  both "else if" are replaced with "elif". Otherwise you have a  nice collection of nested "if" and each needs its own closing "fi" of course.

---

### Post by xjonquilx on 2012-05-08
Hmmm that's odd. I get this:


jonquil@jonquil-Satellite-L755D:~$ sudo sh backup_and_restore.sh
[sudo] password for jonquil: 
This will create a list of installed software that can be re-installed at a later time.
The list is stored in the same folder you opened this script in as installed.log
This script can only be ran as root or super user.
This script will only work on Ubuntu Linux.
Email questions/comments to jonquil at love.com
backup_and_restore.sh: 7: [: Illegal number: 
backup_and_restore.sh: 9: backup_and_restore.sh: select: not found
bad option
backup_and_restore.sh: 22: backup_and_restore.sh: Syntax error: "done" unexpected

This is the script I'm using:


#!/bin/bash
echo "This will create a list of installed software that can be re-installed at a later time."
echo "The list is stored in the same folder you opened this script in as installed.log"
echo "This script can only be ran as root or super user."
echo "This script will only work on Ubuntu Linux."
echo "Email questions/comments to jonquil at love.com"
[ "$UID" -ne "0" ] && echo "You must be root to run this script." && exit 1
OPTIONS="Backup Restore Quit"
select opt in $OPTIONS; do
   if [ "$opt" = "Backup" ]; then
      echo "Backing up software..."
      dpkg --get-selections > installed.log
   elif [ "$opt" = "Restore" ]; then
      echo "Restoring software..."
      dpkg --set-selections < installed.log
   elif [ "$opt" = "Quit" ]; then
      echo Done
      exit
   else
      echo bad option
   fi
done

Maybe I should use elif for that last option instead of else?

---

### Post by xjonquilx on 2012-05-08
No, even when I use elif at the end instead of else I get that same error. This is really weird because I've used this script with other distributions (modified of course) and it worked just fine.

---

### Post by SeijiSensei on 2012-05-08
I recommend replacing the "select" block and using "case":

```

case $opt in

Backup)
      echo "Backing up software..."
      dpkg --get-selections > installed.log
      ;;

Restore)
      echo "Restoring software..."
      dpkg --set-selections < installed.log
      ;;

Quit)
      echo "Exiting" 
      exit 0
      ;;

*)
      echo "Bad option; specify 'Backup','Restore', or 'Quit'"
      exit 1

esac

```

If $opt comes from the command line, like "scriptname Backup", then you should the positional parameter "$1" instead of "$opt" in the case statement.

---

### Post by sisco311 on 2012-05-08
> **xjonquilx said:**
> No, even when I use elif at the end instead of else I get that same error. This is really weird because I've used this script with other distributions (modified of course) and it worked just fine.

In Ubuntu sh is a symlink to dash, NOT bash.

---

### Post by Bachstelze on 2012-05-08
> **sisco311 said:**
> In Ubuntu sh is a symlink to dash, NOT bash.

.. and dash does not define the UID variable, which is where the problem comes from. Otherwise the script is fine.

---

### Post by xjonquilx on 2012-05-08
```
jonquil@jonquil-Satellite-L755D:~$ sudo sh backup_and_restore.sh
[sudo] password for jonquil: 
This will create a list of installed software that can be re-installed at a later time.
The list is stored in the same folder you opened this script in as installed.log
This script can only be ran as root or super user.
This script will only work on Ubuntu Linux.
Email questions/comments to jonquil at love.com
backup_and_restore.sh: 7: [: Illegal number: 
Bad option; specify 'Backup','Restore', or 'Quit'

```
I may have done it wrong, if I did, I apologize. These are variables I'm not familiar with. 


```
#!/bin/bash
echo "This will create a list of installed software that can be re-installed at a later time."
echo "The list is stored in the same folder you opened this script in as installed.log"
echo "This script can only be ran as root or super user."
echo "This script will only work on Ubuntu Linux."
echo "Email questions/comments to jonquil at love.com"
[ "$UID" -ne "0" ] && echo "You must be root to run this script." && exit 1
case $opt in

Backup)
      echo "Backing up software..."
      dpkg --get-selections > installed.log
      ;;

Restore)
      echo "Restoring software..."
      dpkg --set-selections < installed.log
      ;;

Quit)
      echo "Exiting" 
      exit 0
      ;;

*)
      echo "Bad option; specify 'Backup','Restore', or 'Quit'"
      exit 1

esac
```

---

### Post by Bachstelze on 2012-05-08
You were told that sh in Ubuntu is dash, not bash. If you want to run your script with bash, run it with bash!

---

### Post by xjonquilx on 2012-05-08
*sigh*

I'm not a programmer. I'm just a user that knows a little bash and uses it to back up my software. 

If I'm doing something wrong, you need to be specific about what I should do. I understand that sh brings up dash in Ubunutu, but I don't know what you mean when you say to run my script with bash. As far as I know, the only way to run a script in bash is to type sh.

---

### Post by Bachstelze on 2012-05-08
```
bash script.sh
```

What else? Or since you have a "shebang" line

```
./script.sh
```

after having made it executable with

```
chmod +x script.sh
```

---

### Post by xjonquilx on 2012-05-08
I tried ./ and it said command not found. 

However, bash works. Thank you very much for your patience! :)

---

### Post by sisco311 on 2012-05-09
To make your script more portable, you should use something like:
```

...
if [ $(id -u) -ne 0 ]
then
    #errors and warnings are printed to stderr:
    printf '%s\n' "You must be root to run this script" >&2 
    exit 1
fi
...

```

---

