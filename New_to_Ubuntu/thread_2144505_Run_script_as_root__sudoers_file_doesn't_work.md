---
title: "Run script as root / sudoers file doesn't work"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by josvanr on 2013-05-12
I want to set the brightness of my hp envy 17 with a script (doesn't work in 12.04). The script is called 'bri'
 
It containts a line that has to be called as root:

echo $bri > /sys/class/backlight/intel_backlight/brightness

The scritpt is owned by root:

jos@hpux:~/bin$ ls -l bri
-rwsr-xr-x 1 root root 233 Dec 11 22:11 bri


The script works when I am root and also when I do 'sudo ./bri ' something
but when I run it as 'jos' it says 'permission denied'. I tried to change the
sudoers file, adding permissions for the script (see file below) but it just doenst
work. What am I doing wrong? ???????



Jos


-------------------



# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
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

jos ALL = (root) NOPASSWD: /home/jos/bin/gpuoff
jos ALL = (root) NOPASSWD: /home/jos/bin/suspend
jos ALL = (root) NOPASSWD: /sda10/bin/bri

---

### Post by taidoka on 2013-05-12
I would do a 'kdesu' / 'gksu' so that you get a grafical ui to enter your pw.
'kdesu -s' / 'gksu -s' means all following commands will be executed as root.
```
#!/bin/bash
kdesu -s
 echo $bri > /sys/class/backlight/intel_backlight/brightness
exit;

```

---

### Post by taidoka on 2013-05-12
Okay I'm too quickly. You want to run it without any pw prompt: 

 jos      ALL = NOPASSWD: ALL
jos may execute all Apps without pw.
or
%users ALL = NOPASSWD: path/to/script
Now the group users may execute that script without pw prompt.
And
Lowest records have highest privileges. So if there's another record for group %user with ALL = (ALL) ALL then all nopasswd privileges will be removed.

---

### Post by dodo3773 on 2013-05-12
If the path to your script is "[COLOR=#8A8A8A]/sda10/bin/bri[/COLOR]" then how is it that you have a tilde "~" in your previous command ([COLOR=#8A8A8A]jos@hpux:~/bin$ ls -l bri[/COLOR])? Are you sure your script is at /sda10/ or is it actually at either /home/sda10/bin/ or /root/sda10/bin/ That would make sense as to why your sudoers file is not working correctly. What does "pwd" give you when at   [COLOR=#8A8A8A]~/bin ?[/COLOR]

---

### Post by josvanr on 2013-05-25
thnx but ~/bin is a link to /sda10/bin .....

---

### Post by josvanr on 2013-05-25
hi I figured it out: to envoke the script i did

/sda10/bin/bri

where I should have done

sudo /sda10/bin/bri


:-s 

(made a not of that)

---

### Post by dodo3773 on 2013-05-25
Oh nice. Glad you worked it out.

---

### Post by Cheesemill on 2013-05-25
I was just about to post that suggestion, it's a common mistake :)

Adding a custom entry like yours to the sudoers file doesn't mean that you don't have to use sudo anymore, it just means that you won't get prompted for a password when you do.

---

