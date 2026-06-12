---
title: "Add User to Group via Startup Script"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by llemar97 on 2013-10-21
I am trying to create a script that will run as root and add the logged in user to the lpadmin group upon first login.

This is what I have so far:

```

#!/bin/bash


if groups $USER | grep -q -E ' lpadmin(\s|$)'; then
    #echo $USER" is already in the group lpadmin"
else
    #echo $USER" is NOT in the group lpadmin"
    sudo useradd -G lpadmin $USER
fi

```

Are there additional commands that need to be entered to make this happen?  Any tips are welcome.

---

