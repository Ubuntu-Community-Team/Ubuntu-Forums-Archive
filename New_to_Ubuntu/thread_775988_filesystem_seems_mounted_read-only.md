---
title: "filesystem seems mounted read-only"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Random Bob on 2008-04-30
I just recently upgraded Ubuntu 7.10 to 8.04.

Last night, I was trying to show hidden files in my home folder and changed permissions in the process (oops!).

Upon booting my computer this morning, I got an error "User's $HOME/.dmrc file ignored" and something about 644 permissions.  So I did some searching and executed the following commands in the terminal:

sudo chmod -R 755 /home/woohoo
sudo chown woohoo $HOME/.dmrc

So that problem was fixed, but now I get a couple of different errors.  "Filesystem seems mounted read-only.  Skipping journal reply." and "differences between boot sector and its backup".  Then, once Ubuntu loads (very slowly compared to how it was before), I get messages like "error starting GNOME Settings Daemon".

I did some more searching for random commands that might help me out.  (I don't know enough about Linux to come up with these commands on my own.)  I tried dosfchk -ar /dev/sda1, but that didn't appear to have any effect.

So... any ideas on how I can fix the read-only problem and synchronize the boot sector and its backup?  (I didn't even realize it had a backup, and I don't know where it is.)  Thanks in advance.

---

### Post by forrestcupp on 2008-04-30
It's because you used sudo.  If you do that in your /home directory, it gives the permission to root.  You shouldn't use sudo in your /home directory.

---

### Post by forrestcupp on 2008-04-30
Try navigating to it in Nautilus.  Then right-click on the folder you messed up and choose Properties.  Then go to the Permissions tab and set everything to 'Create and delete files' and 'Read and Write'.  Then click the button that says 'Apply Permissions to Enclosed Files' and close.  Then you should be ok.

---

### Post by sayakb on 2008-04-30
Open the nautilus as root by entering 
```
gksudo nautilus
```
and then do as forrestcupp's last post :)

---

### Post by Random Bob on 2008-04-30
> It's because you used sudo. If you do that in your /home directory, it gives the permission to root. You shouldn't use sudo in your /home directory.Isn't this a root problem, though?  I guess I don't understand how/why permissions should be modified without using root.

I followed the advice of forrestcupp and LinuxIsInnovation, and here's what happened:

gksudo nautilus
right-click home folder > preferences
I changed folder access for owner, group, and others to "Create and delete" and applied to all enclosed files.  So far so good.
I changed file access for all three categories to "Read and write" and applied to all enclosed files.  After a few moments, all three file access lines reverted to "---"
I closed the preferences window.
I rebooted to see if the problem was fixed.  The "filesystem seems mounted read-only" and "differences between boot sector and backup" text still appear.  In addition, the "User's $HOME/.dmrc file ignored" message has returned.

Should I use

```
sudo chmod -R 755 /home/woohoo
sudo chown woohoo $HOME/.dmrc
```

again, perhaps without the sudo this time?
Anything I should try differently?

---

### Post by stchman on 2008-04-30
> **Random Bob said:**
> Isn't this a root problem, though?  I guess I don't understand how/why permissions should be modified without using root.

I followed the advice of forrestcupp and LinuxIsInnovation, and here's what happened:

gksudo nautilus
right-click home folder > preferences
I changed folder access for owner, group, and others to "Create and delete" and applied to all enclosed files.  So far so good.
I changed file access for all three categories to "Read and write" and applied to all enclosed files.  After a few moments, all three file access lines reverted to "---"
I closed the preferences window.
I rebooted to see if the problem was fixed.  The "filesystem seems mounted read-only" and "differences between boot sector and backup" text still appear.  In addition, the "User's $HOME/.dmrc file ignored" message has returned.

Should I use

```
sudo chmod -R 755 /home/woohoo
sudo chown woohoo $HOME/.dmrc
```

again, perhaps without the sudo this time?
Anything I should try differently?

Other way around and use this:

```
sudo chown -R $USER:$USER ~/
chmod -R 644 ~/

```

$USER is the user currently logged in and ~/ is the current logged in users home directory.

---

### Post by Random Bob on 2008-04-30
> **stchman said:**
> Other way around and use this:

```
sudo chown -R $USER:$USER ~/
chmod -R 644 ~/

```

$USER is the user currently logged in and ~/ is the current logged in users home directory.

Okay, I've got some major problems now.  (using another computer to access internet)

First, I noticed that when I executed the two commands you suggested, a list of files appeared followed by :Permission denied (or something like that).  One of the files was the .dmrc file that initially gave me trouble.

I rebooted and logged in.  Following login, a window popped up saying "Your session only lasted less than 10 seconds. ..."  Pressing continue loops me back to the login screen, where the same thing happens again.

Clicking "view details (~.xsession-errors file)" in the error window gives:

```
Can't create dir /home/woohoo/Desktop
Can't create dir /home/woohoo/Templates
Can't create dir /home/woohoo/Public
Can't create dir /home/woohoo/Documents
Can't create dir /home/woohoo/Music
Can't create dir /home/woohoo/Pictures
Can't create dir /home/woohoo/Videos

Setting IM through im-switch for locale=en_US
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default

(seahorse-agent:6931): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory '/home/woohoo/.gnome2/': Permission denied
```

:confused:

---

