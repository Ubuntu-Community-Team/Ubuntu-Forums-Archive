---
title: "bash scripting"
date: 2009-09-27
forum: Programming Talk
---

### Post by frustphil on 2009-09-27
Out of curiosity, I am studying it. =)
I am having trouble figuring out what's wrong with this script.

> #!/bin/bash
#This a script that identifies a user whether he/she is a normal, system,
#or a root user.

echo -n "Please enter your username: "
read username

if sudo grep -q $username /etc/passwd
then[INDENT]      id=$(sudo id -u $username)
     declare -i user_id
     user_id=$id
            
if [ $user_id -ge 500 ]
            then[INDENT]         echo "$username, you are a noraml user"
[/INDENT]elif [ $user_id -eq 0 ][INDENT]         echo "$username, you are a root user"
[/INDENT]else[INDENT]                     echo "$username, you are a system user"
[/INDENT]fi
[/INDENT]else echo "Sorry, you're not a valid user!"
fi
if I run it, the shell gives me this error:
> Please enter your username: frustphil
./identify_user.sh: line 16: syntax error near unexpected token `else'
./identify_user.sh: line 16: `    else '
Any idea what's wrong?
Thanks...=)

---

### Post by falconindy on 2009-09-27
Your elif needs a then.

You also don't need to be sudo to use `id`.

---

### Post by frustphil on 2009-09-27
> **falconindy said:**
> Your elif needs a then.

You also don't need to be sudo to use `id`.

So it's the tutorial I followed.. Thanks =)

---

### Post by phrostbyte on 2009-09-27
The current shell's UID is in the variable $EUID

Eg:

```

if [[ $EUID -ne 0 ]]; then
   echo "Error: This script must be run as a superuser. Did you prefix with sudo or are you root?"
   echo 
   exit 1
fi

```

---

### Post by lswb on 2009-09-27
Also ubuntu and debian start numbering for regular users at 1000, not 500.

---

### Post by diesch on 2009-09-28
You don't need sudo to access /etc/passwd either (passwords are stored in /etc/shadow this days).

```
grep -q $username /etc/passwd
``` doesn't do what you want here as it finds not only full user names but partial usernames (like "roo") and other text from /etc/passwd (like "bash"), too.
Either use
 ```
grep "^${username}:" /etc/passwd
``` or ```
getent passwd "$username"
```.

---

### Post by clivelr on 2009-09-30
You forgot the "then" after the elif statement.

```

elif [ $user_id -eq 0 ]
    **then**
    echo "$username, you are a root user"

else

```

---

### Post by frustphil on 2009-10-02
thanks to all =)

---

