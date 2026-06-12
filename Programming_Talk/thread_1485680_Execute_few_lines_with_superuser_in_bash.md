---
title: "Execute few lines with superuser in bash"
date: 2010-05-17
forum: Programming Talk
---

### Post by dragos2 on 2010-05-17
I have a bash script and there are few lines inside that needs to be executed as superuser.

Is there a way that the script be executed normally and when it gets to those lines to
ask for the superuser password, execute them and then leave the superuser ?

---

### Post by yaaarrrgg on 2010-05-20
To just get user input:

#!/bin/bash
echo Please, enter your password
read PASSWORD
echo "Your password is $PASSWORD"

Though if you pass this along on the command line to sudo, it might be less secure than just running the whole script as sudo.   

You might just want to add the user to the sudoers config instead.

---

