---
title: "Create/change username/nickname"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by Jeffrey Kang on 2011-11-27
Can someone walk me through using terminal to create a new home directory, transfer existing files to the new, delete the old - the goal is to change my nickname which appears in the top right corner.

I can change my user name in system > administration > users and groups
but I cannot change my nickname.

I have other threads open, but no one knows quite what to do.

Would this work?

> Do in terminal: 

sudo usermod -l oldname newname

But it won't change the user's home directory, for that you need to do:

sudo cp -r /home/oldname /home/newname
sudo nano /etc/passwd

Find a line like:

corporation:x:1000:1000:corporation,,,:/home/corporation:/bin/ksh

Change the bit /home/oldname to /home/newname.

This should work after a restart, but it's not an elegant method, so make sure you're comfortable in terminal before doing it.

Probably worth noting that if any files in your home directory are  referenced by anything directly (using '/home/oldname/file' instead of  '~/file') the link will break if you delete the old folder.

Any help is much appreciated.

---

### Post by lisati on 2011-11-27
Please do not start [multiple threads]("http://ubuntuforums.org/showthread.php?t=1887121") for the same problem.

---

