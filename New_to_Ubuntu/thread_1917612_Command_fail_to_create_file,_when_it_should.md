---
title: "Command fail to create file, when it should"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by Frozen Forest on 2012-01-30
I keep getting an error with this command, saying that the file or folder/directory doesn't exist, strange thing is that the point of the command is to create the file authorized_keys
[PHP]
/bin/echo "/home/$ADMIN/keys/$KEY_NAME${USERS[$i]}.pub" > "home/${USERS[$i]}/.ssh/authorized_keys"
[/PHP]

EDIT;
If it does any difference does the script that contains this command run as root.

---

### Post by Vaphell on 2012-01-30
try *mkdir -p home/$USERS[$i]/.ssh* first
you can't redirect to a file in a nonexistent dir

---

### Post by Dumbestcrayon on 2012-01-30
> **Vaphell said:**
> try *mkdir -p home/$USERS[$i]/.ssh* first
you can't redirect to a file in a nonexistent dir

This is correct, but to elaborate on this look in the man page for mkdir.


```
       -p, --parents
              no error if existing, make parent directories as needed
```

The '-p' parameter says to create the parent directories in the tree if necessary.

---

### Post by Frozen Forest on 2012-01-30
That was is so strange, I'm doing that but it doesn't work, maybe I missed something obvious.
[PHP]
    /bin/mkdir -p /home/"${USERS[$i]}"/.ssh
    /bin/chown "${USERS[$i]}":"$GROUP" /home/"${USERS[$i]}"/.ssh

    /usr/bin/ssh-keygen -t rsa -N "${PASSWORDS[$i]}" -f /home/$ADMIN/svn-keys/$KEY_NAME"${USERS[$i]}"
    /bin/chown "${USERS[$i]}":$GROUP "/home/$ADMIN/keys/$KEY_NAME${USERS[$i]}"
    /bin/echo "/home/$ADMIN/keys/$KEY_NAME${USERS[$i]}.pub" > "home/${USERS[$i]}/.ssh/authorized_keys"  
[/PHP]

---

### Post by Vaphell on 2012-01-31
is there any reason why you use full paths of system tools?

try to echo anything that moves so you get to see if you have proper values in your variables. What does your loop look like exactly?

---

