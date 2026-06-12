---
title: "Adding a user to the sudoers list"
date: 2014-05-17
forum: New to Ubuntu
---

### Post by moebob24 on 2014-05-17
I run:

```
visudo
```

and I am presented with a blank file. According to what I was reading about this task, there should already be something in here for me to add to. D:

While I am not completely new to Linux, I have never done anything with a VPS before and certainly never set up a sudoer account. The desktop install just does it for you.

Just want to get community advice before I lock myself out and have to blow the thing away.

It's a Digital Ocean VPS. Little cheapy guy I am using for IRC most of the time, but also using this as a learning experience for myself.

---

### Post by Lars Noodén on 2014-05-17
It should edit the file /etc/sudoers, but even visudo needs root privileges to edit it.  

Also, sudo is not an all-or-nothing permissions choice.  If there are specific activities that you need a user to run, then you can add just those.  That's kind of not mentioned enough.

---

### Post by frytek on 2014-05-17
if you can't run "sudo visudo", try add your username to the "admin" group. 

if you still can't run it because the file is empty, try to do "su -" and then edit the /etc/sudoers file with your favorite editor. if the file is really empty, paste the text i'm attaching in the end of this post. it ads the "admin" group to the file. from now on you should be able to do "sudo visudo" if you are in the admin group. (I'm not sure but you may need to re-login after adding yourself to the "admin" group). 

here's the content of my /etc/sudoers file: 

#
# This file MUST be edited with the 'visudo' command as root.
#
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

---

### Post by moebob24 on 2014-05-17
> **frytek said:**
> if you can't run "sudo visudo", try add your username to the "admin" group. 

if you still can't run it because the file is empty, try to do "su -" and then edit the /etc/sudoers file with your favorite editor. if the file is really empty, paste the text i'm attaching in the end of this post. it ads the "admin" group to the file. from now on you should be able to do "sudo visudo" if you are in the admin group. (I'm not sure but you may need to re-login after adding yourself to the "admin" group). 

here's the content of my /etc/sudoers file: 

#
# This file MUST be edited with the 'visudo' command as root.
#
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

Thank you! I took this, added my username in and boom, I can sudo. :D

---

