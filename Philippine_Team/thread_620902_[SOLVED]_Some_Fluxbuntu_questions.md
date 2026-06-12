---
title: "[SOLVED] Some Fluxbuntu questions"
date: 2007-11-23
forum: Philippine Team
---

### Post by xtrm_redbull on 2007-11-23
I just installed fluxbuntu 7.10rc on an IBM R50e,  and everything is working great. Im just trying it out to see if I can get comfortable using it, however I find it different from ubuntu or xubuntu I have a few questions right now:

1.  How do I copy and paste commands, from kazehakase to the console?
2. Can I turn off the password promt everytime I shutdown?

As of this time I cant post on the fluxbuntu forums, cause my account is not yet active. Please post any useful fluxbuntu links that will help a noob like me.

Thanks in advance.:)

---

### Post by kerry_s on 2007-11-23
> 1. How do I copy and paste commands, from kazehakase to the console?
2. Can I turn off the password promt everytime I shutdown?

1: left click drag to highlight, middle click to paste
2: add reboot and halt to the sudoers list then add the commands to the menu.
example:
in terminal>
**sudo visudo**

```
your-name ALL=NOPASSWD: /sbin/reboot, /sbin/halt
```

(i'm going off memory so check the path for commands)

---

### Post by xtrm_redbull on 2007-11-23
Thank you so much kerry_s, I can copy and paste now\\:D/
Now Im going to try the shutdown part.

---

### Post by xtrm_redbull on 2007-11-23
@ kerry_s, I tried inserting the code but its not working, :confused: this is my /etc/sudoers:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


Can you please tell me were should I put it. Thanks again

---

### Post by kerry_s on 2007-11-23
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
your-name ALL=NOPASSWD: /sbin/reboot, /sbin/halt

```


make sure you check the path, in terminal type> updatedb
after that finishes type> locate reboot

i don't have a linux system up and running right now, so i can't check the path, it might be> /usr/sbin/reboot, /usr/sbin/halt

i'm in the process of selling of some of my old computers and parts so i only have varies windows installed. sorry i can't be more precise, got to get that Xmas cash. :)

---

### Post by xtrm_redbull on 2007-11-23
@ kerry_s
After trying this method I to the best of my limited abilities, I gave up and decided to install apps that are more familiar to like thunar and xfce4-terminal so I can copy and paste the usual method. While reading the [howto-configure: your menu ]("http://community.fluxbuntu.org/index.php?topic=36.0") I found the solution to my shutdown problem.

Thanks for your help :)

---

### Post by xtrm_redbull on 2007-11-28
Hi everyone im almost complete configuring my fluxbuntu install:), can you guys help me put icons on thunar? or just use the icons that rox-filer use? and is it posible to change the splash and login theme?

Thanks again

---

### Post by MangasColoradas on 2007-12-27
Middle clicking isnt working to paste into terminal for me.

I copy from the browser and when I middle click the terminal, it seems to copy and paste my 'username@fluxbuntu:~$'

It seems to work OK if I have the terminal open before I copy from the browser. :)

---

