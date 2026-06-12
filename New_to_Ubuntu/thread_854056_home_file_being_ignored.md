---
title: "home file being ignored?"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by kneewax on 2008-07-09
Logged on to Ubuntu this morning and after entering my password the following error popped up:

"User's $home/.drmc file is being ignored. This prevents the default session from being saved. File should be owned by the user and have 644 permission. User's $home directory must be owned by user and not writeable by other users"

Once logged in Ubuntu seems to be working OK, but I am concerned about the implications of the error.

Anyone got any ideas?

---

### Post by drs305 on 2008-07-09
Your permissions have become messed up. Run the commands below. If you cannot use 'sudo' or log into any account, choose 'Recovery mode' > 'root' from the grub menu and boot to a root prompt. 

Change 'username' to your username (log-in name):

```
sudo chmod 644 /home/**username**/.dmrc
sudo chown **username**: /home/**username**/.dmrc
sudo chmod 755 /home/**username**
sudo chown **username**: /home/**username**
sudo shutdown -r now

```

---

### Post by kneewax on 2008-07-09
GREAT!  That solved it. Thanks.  I wonder how the permisssions got mucked up like that?

---

### Post by ahzadjali on 2008-07-10
thanks drc305.... i too recovered from permission 644.....

is there any explanation how it just permission change to 644.

----------------------

---

### Post by larryfroot on 2008-07-10
Just to add the GUI for chmod is in the right click context menu. Just right click on a file or folder, go down to the properties, then into the permissions tab. As long as you own the file or folder, you can change the permissions of folder and if you wish all the contents of that folder as well. 

Regarding .drmc...

I recently backed up for a full re-install - new hardware etc. Just seemed easier to deal with on a reinstall plus it gave me the motivation to back up everything. Anyways...when I replaced all my folders that I backed up back into /home/username, all the ownerships and permissions were in need of resetting back to myself again! I took the lazy way out and chowned everything in /home/username to myself again using chown -R (recursive) plus set all the permissions in /home/username to read write and execute by right clicking on /home/username and going into properties, again applying the same permissions I set for all folders and files in /home/username. 

A few days later the message that  .drmc file not owned by user comes up!

Its not important - I just went ahead and reset it. But it did my head in a bit! Strange.....Oh, I found out after that if you compress folders when you backup they keep their ownership and permissions when you extract them.

---

### Post by drs305 on 2008-07-10
> **ahzadjali said:**
> thanks drc305.... i too recovered from permission 644.....

is there any explanation how it just permission change to 644.

----------------------

Two of you have asked that question. It is probably the incorrect use of the "chown" or "chmod" commands on the command line or selecting RWX permissions for 'Others' in nautilus or another file browser. You cannot grant universal privileges to Others even though you are the owner of the $HOME folder. If you look at the error messages:
```
"User's $home/.drmc file is being ignored. This prevents the default session from being saved. 
```
The .dmrc file must have a permission of 644. 

If you change the permissions  of the home folder and this file's permissions change from 644 ubuntu is going to complain. So if you universally change the contents of the $HOME folder to 7XX it is going to change the .dmrc permissions to something ubuntu won't like.
 
```
User's $home directory must be owned by user and not writeable by other users
```
Again, this message is saying that 'Others' must not be able to write to the $HOME folder. So the last digit of the permissions (XXX) must not be either 2,3,6, or 7 or to put it differently - the 'write' permission must not be enabled.

Just be careful when setting the permissions of RWX to all folders and files in the $HOME folder and subfolders. The "chmod" or "chown" commands, or doing the same in nautilus with the "Apply permissions to all files" button, are very powerful. And one final caution: If you mistakenly apply the wrong permissions recursively (-R) to the root directory you will likely have to reinstall your system.

---

### Post by larryfroot on 2008-07-10
I am chastened....thank you very much for that advice. I feel fortunate that I didn't spanner my system. :oops:

---

### Post by bodhi.zazen on 2008-07-10
> **drs305 said:**
> So the last digit of the permissions (XXX) must not be either 2,3,6, or 7 or to put it differently - the 'write' permission must not be enabled.

... Or 0 for a private $HOME

---

