---
title: "shell script question"
date: 2010-07-31
forum: Programming Talk
---

### Post by skript_teaze on 2010-07-31
I've created a shell script to run xboxdrv (A driver for my xbox 360 controller.) Here is the content of the file:

#! /bin/bash
sudo ~/tmp/xboxdrv-linux-0.4.10/xboxdrv

Is there a command I can use instead of sudo, so that it runs as root without asking me for the password every time I run the script?

---

### Post by Bachstelze on 2010-07-31
You can configure sudo so that it does not ask your password when you run that particular command.  Edit the sudoers file with

```
sudo visudo
```

You should have a line like this:

```
%admin   ALL=(ALL) ALL
```

Modify it like this:

```
%admin   ALL=(ALL) ALL, NOPASSWD: /home/user/tmp/xboxdrv-linux-0.4.10/xboxdrv
```

You *must* put the absolute path here, no ~.

---

### Post by skript_teaze on 2010-08-04
I don't have that line, do I need to create a new line like the one you wrote?

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have

---

### Post by Bachstelze on 2010-08-04
Yes, though since you're probably not running Ubuntu, things are going to be a bit different.  Do you want to allow running the command for just one user, a group of users, or everyone?

---

### Post by interval1066 on 2010-08-04
Hey, I've noticed that driver in the kernel sources, what exactly does it allow you to do? Can you program what the controller buttons do arbitrarily? Like, hitting the red x calls up your default browser, or what?

---

### Post by skript_teaze on 2010-08-04
> **interval1066 said:**
> Hey, I've noticed that driver in the kernel sources, what exactly does it allow you to do? Can you program what the controller buttons do arbitrarily? Like, hitting the red x calls up your default browser, or what?

I have no idea, I'm using it because I had real problems getting the xpad driver to work for me. They might be able to answer that on the xboxdrv forum though.. 
[http://ubuntuforums.org/showthread.php?t=825464](http://ubuntuforums.org/showthread.php?t=825464)

---

### Post by skript_teaze on 2010-08-04
> **Bachstelze said:**
> Yes, though since you're probably not running Ubuntu, things are going to be a bit different.  Do you want to allow running the command for just one user, a group of users, or everyone?

I'm running Lucid Lynx i386. I would want the command to be allowed to run by anyone using the machine.

---

### Post by Bachstelze on 2010-08-04
Then forget about sudo, you can just make the file setuid root:

```
sudo chown root ~/tmp/xboxdrv-linux-0.4.10/xboxdrv
sudo chmod +s ~/tmp/xboxdrv-linux-0.4.10/xboxdrv
```

Anyone running the file will automatically run it as root.

---

### Post by skript_teaze on 2010-08-05
Thanks that's done the trick!

---

### Post by interval1066 on 2010-08-05
> **skript_teaze said:**
> I have no idea, I'm using it because I had real problems getting the xpad driver to work for me. They might be able to answer that on the xboxdrv forum though.. 
[http://ubuntuforums.org/showthread.php?t=825464](http://ubuntuforums.org/showthread.php?t=825464)

Yeah, that's exactly what it allows you to do, button re-mapping, rumble feedback, mouse control- coming, apparently. All the community needs now is some one to develop a game that uses it. Maybe there's one out, I dunno.

---

