---
title: "why this error is occuring what's wrong in my script??"
date: 2012-11-03
forum: Programming Talk
---

### Post by Mohan1289 on 2012-11-03
here is the screen shot of both the script and output i don't get it?? can you tell me

and the directories mentioned in the script are exist in my system??

the script is ```


#!/bin/bash
#Only Sudo can run the script
ROOT_UID=0 #Since Only users with $UID 0 have root privileges
E_NOTROOT=87 #Non-root Exit Error
if [ "$UID" -ne "$ROOT_UID" ]; then
echo "You Must be root to run this script"
exit $E_NOTROOT
fi
echo "Enter your Username"
read uname

if grep -q "^$uname:" /etc/passwd; then
cd /home/$uname/projects
echo "the files in this directory are"
ls
else
echo "Incorrect username"
fi
echo "Enter File name"
read fname
unzip $fname /home/krishna/Desktop/test
```

---

### Post by spjackson on 2012-11-03
You have written a bash script; I know this because on line 1 you have put
```

#!/bin/bash

```
By typing "sh test.sh" you are trying to run it as a sh script. sh is not bash. This may work for some bash scripts because some bash scripts are also sh scripts. However it doesn't work in this case because UID is a variable that is set by the bash shell. It is not set by the sh shell.

Your unzip command means this: search the zip archive for the file /home/krishna/Desktop/test and extract it. unzip warns you that it cannot find this file in the zip archive.

If what you intend is to extract the archive into the directory /home/krishna/Desktop/test then you need to use -d [as you have already been shown.]("http://ubuntuforums.org/showpost.php?p=12329641&postcount=5")

---

### Post by dwhitney67 on 2012-11-03
It should also be mentioned that checking the environment variable UID is inappropriate because it could be set to 0 by a non-root user.

The preferred way to determine one's user ID is to use /usr/bin/id

For example:
```

#!/bin/bash

if [ `/usr/bin/id -u` -eq 0 ]; then
    echo "I'm root"
else
    echo "I'm NOT root"
fi

```

To follow up on spjackson's comments, on some Linux systems such as Ubuntu, /bin/sh is linked to 'dash', not 'bash'.  On RHEL/CentOS/Fedora, /bin/sh is linked to 'bash'.  In summary, don't expect /bin/sh to be mapped to bash.

If you want a script to be executable by the user, then change its mode using chmod; for example:
```

chmod u+x myscript.sh

```
Then you can execute it using:
```

./myscript.sh

```

---

### Post by slavik on 2012-11-03
double brackets instead of single brackets.

[[ ]] instead of [ ]

---

### Post by Mohan1289 on 2012-11-04
> **spjackson said:**
> You have written a bash script; I know this because on line 1 you have put
```

#!/bin/bash

```
By typing "sh test.sh" you are trying to run it as a sh script. sh is not bash. This may work for some bash scripts because some bash scripts are also sh scripts. However it doesn't work in this case because UID is a variable that is set by the bash shell. It is not set by the sh shell.

Your unzip command means this: search the zip archive for the file /home/krishna/Desktop/test and extract it. unzip warns you that it cannot find this file in the zip archive.

If what you intend is to extract the archive into the directory /home/krishna/Desktop/test then you need to use -d [as you have already been shown.]("http://ubuntuforums.org/showpost.php?p=12329641&postcount=5")

Thank You Jackson it worked

---

