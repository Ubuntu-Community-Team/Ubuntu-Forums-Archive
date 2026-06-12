---
title: "Simple permissions question?"
date: 2013-08-03
forum: New to Ubuntu
---

### Post by 1888software on 2013-08-03
I am the owner of the folder called: folder1
I created this empty folder while logged in as superuser and its permissions are: read and write

When I try to move the folder I get permission denied:

[COLOR=#008000]ubuntu@ubuntu-VPCEE43FX:~$ mv /home/ubuntu/Documents/folder1 /var/www/
mv: cannot move ‘/home/ubuntu/Documents/folder1’ to ‘/var/www/folder1’: Permission denied[/COLOR]

Huh? What gives? I'm the superuser and I own the file!

So, suggestions please?

---

### Post by mikewhatever on 2013-08-03
Can you post the outputs of **id** and **ls -ld /home/ubuntu/Documents/folder1** to clarify the simple, but somewhat vague question.
The folder is, likely owned by the superuser, so that a regular user can't move it.
Linux/Unix permissions are a bit more complicated then "It's my computer, my files,I am the owner, etc".

---

### Post by 3rdalbum on 2013-08-03
> **1888software said:**
> I am the owner of the folder called: folder1
I created this empty folder while logged in as superuser and its permissions are: read and write

When I try to move the folder I get permission denied:

[COLOR=#008000]ubuntu@ubuntu-VPCEE43FX:~$ mv /home/ubuntu/Documents/folder1 /var/www/
mv: cannot move ‘/home/ubuntu/Documents/folder1’ to ‘/var/www/folder1’: Permission denied[/COLOR]

Huh? What gives? I'm the superuser and I own the file!

So, suggestions please?

Any files/folders you create as root will be owned by root. Your normal user account is not root, so it can't modify those files or folders. Also, the /var/www directory is root-owned (typically anything outside your home directory is root-owned) so you can't copy anything into it - only root can, of course.

A couple of options for you:
Put the word "sudo" in front of that mv command and it will work.
Or, run the command "pkexec nautilus" to open a file browser as root and move the folder that way. Make sure you close that root file browser after doing what you want to do, so you don't accidentally use it incorrectly.

Try not to create files as root in your home directory. Only use root when absolutely necessary. Remember, opening a program when you are root will cause any files it creates to also be root-owned.

---

