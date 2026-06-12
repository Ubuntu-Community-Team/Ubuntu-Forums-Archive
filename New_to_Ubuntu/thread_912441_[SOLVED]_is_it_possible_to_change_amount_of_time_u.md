---
title: "[SOLVED] is it possible to change amount of time ubuntu remembers my password in term"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by imgkg on 2008-09-06
is it possible to customize amount of time ubuntu remembers my password in after installing some software , i dont want my box to cache my password i really dont know how to do that, like when i sign into sudo in terminal but i dont want it to remember my password whenever a new terminal is open as when i type sudo su it should ask me again for password please help how to change it

---

### Post by drs305 on 2008-09-06
The file that contains the timeout value is called 'sudoers'. It is a special file that must be edited in a special way.

If you are familiar and comfortable using the vi editor (and how to insert, delete, save and exit):
```

sudo visudo

```

If you are more comfortable with gedit:
```

export EDITOR=gedit && sudo -E visudo

```

Look for the line with "**timestamp_timeout=**" and change the value (in minutes) to what you desire.

Note that any extension will reduce the security of your system.

---

### Post by Elfy on 2008-09-06
Yes it is possible to change the timeout, I haven't done so but the information should help here

[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=5334942&postcount=3](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=5334942&postcount=3)

---

### Post by imgkg on 2008-09-06
that file is opened "sudoers" it doesnt have any line "timestamp_timeout=" please help if something is wrong , is it safe if i post its contents here for you to take a look

---

### Post by Elfy on 2008-09-06
yes it's safe :)

---

### Post by drs305 on 2008-09-06
> **imgkg said:**
> that file is opened "sudoers" it doesnt have any line "timestamp_timeout=" please help if something is wrong , is it safe if i post its contents here for you to take a look

It must have been something I added. Change *XXXX* to your username. Add:
```

Defaults:XXXX timestamp_timeout=5

```
Example:
**Defaults:[COLOR="Red"]yourusername[/COLOR] timestamp_timeout=10**

This is NOT the entire file, but the top should look something like this:
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

# Defaults

Defaults !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
 %admin ALL=(ALL) ALL

**Defaults:myusername timestamp_timeout=15**
# default time out is 5 minutes

**FILE CONTINUES ...**

```

---

### Post by imgkg on 2008-09-06
here is my sudoers file content 
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
``` please check if something is wrong

---

### Post by imgkg on 2008-09-06
should i add that line ? -------->Defaults:yourusername timestamp_timeout=10

---

### Post by drs305 on 2008-09-06
> **imgkg said:**
> should i add that line ? -------->Defaults:yourusername timestamp_timeout=10

Yes, change *yourusername* and change the timeout value in minutes to what you desire.

Making the timeout longer reduces your security.

Please mark this solved if you have no more questions. See my signature line for how to do this.

---

### Post by imgkg on 2008-09-06
thank you very much

---

