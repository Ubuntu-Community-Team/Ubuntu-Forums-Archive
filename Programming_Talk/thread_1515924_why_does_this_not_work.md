---
title: "why does this not work"
date: 2010-06-23
forum: Programming Talk
---

### Post by Drenriza on 2010-06-23
```
#!/bin/bash

if [ "$(id -u)" != "0" ]; then
   cd /home/cristian #test
else
echo "You must be the superuser to run this script" >&2
fi
```

I have been reading this from a guide, but i think their is an error or 2 in it.

Hope some1 can help. Thanks

---

### Post by Drenriza on 2010-06-23
i found this on the web instead.

```
CMDLN_ARGS="$@" # Command line arguments for this script
export CMDLN_ARGS

# Run this script as root if not already.
chk_root () {

  if [ ! $( id -u ) -eq 0 ]; then
    echo "Please enter root's password."
    exec su -c "${0} ${CMDLN_ARGS}" # Call this prog as root
    exit ${?}  # sice we're 'execing' above, we wont reach this exit
               # unless something goes wrong.
  fi

}

# Call this function early on - now or before your script's main loop starts.
chk_root
```

but i would like to know why #1 does not work, if anyone can tell me.

---

### Post by Lampi on 2010-06-23
```
if [ "$(id -u)" != "0" ]; then
```
has to be 
```
if [ "$(id -u)" == "0" ]; then
```
otherwise it is the wrong way around

Example:

```
#!/bin/bash

if [ "$(id -u)" == "0" ]; then
echo "You are superuser" >&2
else
echo "You must be the superuser to run this script" >&2
fi

```
Now run this as sudo and you end in the if condition
Now run it as normal user and you end in the else condition

---

### Post by Drenriza on 2010-06-23
this code

```
CMDLN_ARGS="$@" # Command line arguments for this script
export CMDLN_ARGS

# Run this script as root if not already.
chk_root () {

  if [ ! $( id -u ) -eq 0 ]; then
    echo "Please enter root's password."
    exec su -c "${0} ${CMDLN_ARGS}" # Call this prog as root
    exit ${?}  # sice we're 'execing' above, we wont reach this exit
               # unless something goes wrong.
  fi

}

# Call this function early on - now or before your script's main loop starts.
chk_root
```

can you do so this can work with other users? for example just to try, my normal user. So a root user cant execute it unless he goes ```
su - "my user"
```

i was thinking along the way

```
CMDLN_ARGS="$@" # Command line arguments for this script
export CMDLN_ARGS

# Run this script as root if not already.
chk_cristian () {

  if [ ! $( id -u ) -eq 1000 ]; then
    echo "Please enter cristian's password."
    exec su -c "${0} ${CMDLN_ARGS}" # Call this prog as root
    exit ${?}  # sice we're 'execing' above, we wont reach this exit
               # unless something goes wrong.
  fi

}

# Call this function early on - now or before your script's main loop starts.
chk_cristian
```

then it does,
```
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
Please enter cristian's password.
```

i see this as an error since it just continues until ctrl + c
how do i solve this.

im not good at bash, learning everyday :p

thanks lampi. for #3

---

### Post by Lampi on 2010-06-23
> **Drenriza said:**
> can you do so this can work with other users? for example just to try, my normal user. So a root user cant execute it unless he goes ```
su - "my user"
```
What about an easier approach? kdesude or gksudo can execute a script as the user you specify:

kdesudo -u christian -c <skript or command>

so it doesn't matter what user you are when you run this script, it will ask for root pw and then execute as user christian

---

### Post by Drenriza on 2010-06-23
i want to specify in the script, the user you need to be to run the script. Because the people who need the scripts has in the past run them as the wrong user multiple times. Resulting in a root user making changes to files of a (user that the server is depentent on, having specific owner, groups, permissions for other services) normal system user, thus changing its group/ownership, file/folder permissions = me figuring out what went wrong.

---

### Post by Lampi on 2010-06-23
So you're saying the script will now always run as user cristian?

---

### Post by Drenriza on 2010-06-23
i'm asking if i with this code
```
CMDLN_ARGS="$@" # Command line arguments for this script
export CMDLN_ARGS

# Run this script as cristian if not already.
chk_cristian () {

  if [ ! $( id -u ) -eq 1000 ]; then
    echo "Please enter cristian's password."
    exec su -c "${0} ${CMDLN_ARGS}" # Call this prog as cristian
    exit ${?}  # sice we're 'execing' above, we wont reach this exit
               # unless something goes wrong.
  fi

}

# Call this function early on - now or before your script's main loop starts.
chk_cristian
```

can do, so if you for example try with a root user. To start the script, the script will ask you to change user to example, cristian and enter his password.

So the script will run with the cristian user permissions.
And not root user permissions EVEN if you try to start the script as root.

---

### Post by Lampi on 2010-06-23
I guess sudo [-u username|#uid] [-g groupname|#gid] <command> will do what you ask for:
```
exec sudo -u cristian "${0} ${CMDLN_ARGS}" # Call this prog as root

```
You can use "cristian" or the uid of cristian

cristian has to be member of group admin or sudo, you might need to tweak /etc/sudoers for the script or the command you like to use.

---

### Post by Drenriza on 2010-06-23
.

---

### Post by Lampi on 2010-06-23
try su with -s and -l paramter:

su -l -c <command>
su -s -c <command>

does one of them work as planned?

BTW: You do use a Shebang at the top of file, do you?

```
#!/bin/bash
```

---

### Post by Drenriza on 2010-06-23
.

---

### Post by Drenriza on 2010-06-23
.

---

### Post by pbrane on 2010-06-23
This is easier syntax to remember.
```

if (($UID > 0)); then
   echo 'This script can be run only by the system administrator'
   exit
fi

```

---

### Post by Drenriza on 2010-06-24
> **pbrane said:**
> This is easier syntax to remember.
```

if (($UID > 0)); then
   echo 'This script can be run only by the system administrator'
   exit
fi

```

your quite right. After a chat with a kolleage, that reminded me that when root and changing to another user(su), you dont get prompted for a password... Had in the mess forgot that and was Dohhhhhh.

So i ended up copying out 
```

   if [ $( id -u ) -eq 0 ]; then
	su - cristian
        echo "something"

   fi
```

For changing from root -> user
made it a whole lot easier.

The only issue i have, is that after using the command. ```
su - cristian
```
The ```
echo "something
``` dosent get run, for some reason.

OUTPUT:
```

root@cristian-laptop:/home/cristian/Dokumenter/scripts# ./test 
cristian@cristian-laptop:~$ 
```

No echo "something"

---

### Post by Lampi on 2010-06-24
> ```
su - cristian
```

it's only su <username>

```
su cristian
```

Or you can use

> sudo -u cristian

Glad you found a solution :)

---

