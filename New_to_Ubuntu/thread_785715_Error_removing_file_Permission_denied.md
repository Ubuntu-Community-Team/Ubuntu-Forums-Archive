---
title: "Error removing file: Permission denied"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by dascheer on 2008-05-07
I'm trying to remove a big folder from my hard drive, but I get the following error message:

Error removing file: Permission denied

The "permissions" tab in the directory's properties window says that it has read, write, and execute for owner, user, and group.  But it still refuses to be removed.  I've tried removing them as root in the terminal, but it doesnt work.  I have no idea have chmod works.

I am the biggest n00b ever.  Help!

---

### Post by tamoneya on 2008-05-07
you need to be very careful when using the following command because you could easily wipe out large sections of your install and easily be forced to do a reinstall from scratch.```
sudo rm -rf /path/to/directory/
```Note that if you dont have the permissions to be removing the directory you probably shouldnt be.  Take another second to think about what you are doing because you wont be able to undo this.

---

### Post by darc on 2008-05-07
> **dascheer said:**
> I'm trying to remove a big folder from my hard drive, but I get the following error message:

Error removing file: Permission denied

The "permissions" tab in the directory's properties window says that it has read, write, and execute for owner, user, and group.  But it still refuses to be removed.  I've tried removing them as root in the terminal, but it doesnt work.  I have no idea have chmod works.

I am the biggest n00b ever.  Help!

If you're extra super sure you want to delete the folder, and everything in it, try this command (delete recursively and force it):
```
sudo rm -rf folder_name
```

Work?

If not, try this command to set permissions (recursively, everyone can read/write/execute):
```
sudo chmod -R 777 folder_name
```

Then try to delete it again : 
```
sudo rm -rf folder_name
```

Still not working?

Post the results of this command, if not:
```
ls -l folder_name
```

-darc

EDIT:  O yeah, added SUDO to the command I listed, forgot about that, thanks Tamoneya : (

---

### Post by spiderbatdad on 2008-05-07
run ```
gksu nautilus
``` and work graphically if you like

---

### Post by dascheer on 2008-05-07
Thanks for the replies.  I can't find the Trash directory, though.  In Gutsy, it was a hidden .Trash directory in the home folder, but I cant find it in Hardy

---

### Post by darc on 2008-05-07
> **dascheer said:**
> Thanks for the replies.  I can't find the Trash directory, though.  In Gutsy, it was a hidden .Trash directory in the home folder, but I cant find it in Hardy

Check here : /home/user/.local/share/Trash 

I don't have access to my system at the moment to verify, but culled this from another thread.
-darc

EDIT:  Note that by "user" I mean your username.  Or:
~/.local/share/Trash

---

### Post by dascheer on 2008-05-07
Yes! The chmod -R 777 worked perfectly! Thanks a lot guys!

---

### Post by fenian on 2008-05-07
You could also do it this way (removes all files in the trash)...

> sudo rm -rf ~/.local/share/Trash/files/*

---

### Post by burningkenshin on 2009-12-13
> **fenian said:**
> You could also do it this way (removes all files in the trash)...

Thanks for the info as I ran into the same issue as well.  :P  I have a question though as I'm learning various switches to use in terminal.  For the command that you listed:

sudo rm -rf ~/.local/share/Trash/files/*

I did not see a switch for "-rf".  I'm assuming it does a recursive search for any files that are in the specified location & forcibly removes them?  Just wondering.  Thanks in advance to anyone that can help me with this.

---

### Post by Yneth on 2010-06-26
Thanks!! That worked for me.

---

### Post by al prince nofl on 2011-01-14
Thanks, all It worked with others but i hope that there is way to solve this problem with all the folders and files in the computer :/   Thanks,

---

