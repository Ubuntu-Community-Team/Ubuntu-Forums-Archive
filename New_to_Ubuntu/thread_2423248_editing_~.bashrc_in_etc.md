---
title: "editing ~/.bashrc in /etc"
date: 2019-07-19
forum: New to Ubuntu
---

### Post by engrpeterjohn on 2019-07-19
Hi, 

I would like to edit the ~/.bashrc in /etc but when I close the file it only has save as option or the changes will be discarded within some second ... Do I need to open the file with SUDO, if yes then how ?

---

### Post by TheFu on 2019-07-19
First, you need to understand what ~/.bashrc means.  ~/ == $HOME == /home/engrpeterjohn (probably).  The HOME environment variable it set by the login process based on the entire for the specific userid in the password record.

```
getent passwd engrpeterjohn
``` is the command to see the password entry for 1 userid.
~/.bashrc **==** $HOME/.bashrc **==** /home/engrpeterjohn/.bashrc
That is not /etc/.bashrc. No way, no how.

If you want to modify any files or directories outside YOUR home, then you need to understand that Linux is multi-user from the ground up.  Permissions matter.   There are lots of permissions tutorials which you can look up and follw, but just know that every process running and every file and every directory on every Unix-like OS runs with an effective owner, and effective group.  This is critical to the security of the system and if you forget it, bad things are likely.

BTW, you probably want to edit the /etc/bash.bashrc file.  I would suggest that this is a very bad idea, especially when you don't understand the other things listed above.  If you mess up this file, you may prevent all userids from logging in.  It could cause what is known as a login-loop.

---

### Post by Impavidus on 2019-07-19
~ is short for your home directory, so ~/.bashrc is a file in your home directory, not in /etc. Are you editing some other file in /etc? You need root permissions to edit most files there. Some options:```
# for terminal-based text editors like nano or vim:
sudo nano /etc/file
# for GUI text editors like gedit of mousepad, to prevent root-owned config files in your home directory:
sudo -H gedit /etc/file
# sudoedit has some extra safety belts and will use a default text editor:
sudoedit /etc/file
```

---

### Post by sevendogs1337 on 2019-07-19
OP: are you talking about the .bashrc in /etc/skel?

---

